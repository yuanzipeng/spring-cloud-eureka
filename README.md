# spring-cloud-eureka
spring-cloud-eureka服务注册中心示例

1、pom文件加以下maven依赖包：
<dependencies>

        <dependency>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-starter-web</artifactId>
            </dependency>
            <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-test</artifactId>
            <scope>test</scope>
            <exclusions>
                <exclusion>
                    <groupId>org.junit.vintage</groupId>
                    <artifactId>junit-vintage-engine</artifactId>
                </exclusion>
            </exclusions>
        </dependency>
        <dependency>
            <groupId>org.springframework.cloud</groupId>
            <artifactId>spring-cloud-starter</artifactId>
            <version>2.2.2.RELEASE</version>
        </dependency>
        <dependency>
            <groupId>org.springframework.cloud</groupId>
            <artifactId>spring-cloud-netflix-eureka-server</artifactId>
            <version>2.2.2.RELEASE</version>
        </dependency>
 </dependencies>
 
2、配置文件application.yml加以下配置：

     server:
       port: 8761
         tomcat:
            uri-encoding: utf-8

     eureka:
       instance:
         hostname: localhost
           # 优先使用IP地址方式进行注册服务
           prefer-ip-address: true
        client:
           register-with-eureka: false
           fetch-registry: false
           service-url:
              defaultZone: http://localhost:${server.port}/eureka/

        spring:
          application:
            name: spring-cloud-eureka
	
3、EurekaApplication.java文件加注解@EnableEurekaServer

启动项目访问http://localhost:8761/

