# springboot-web-demo (basicspringbootdemo)

## Overview

A minimal Spring Boot web application demonstrating a Spring MVC controller returning a server-rendered Thymeleaf view. It shows the basic request flow: an incoming HTTP request is mapped to a controller method, the controller places data into the model, and a Thymeleaf template renders that data into HTML.

## Technology Stack

- Java 17
- Spring Boot 3.5.7
- Spring Web (`spring-boot-starter-web`)
- Thymeleaf (`spring-boot-starter-thymeleaf`)
- Spring Boot DevTools (development-time auto-restart)
- Maven (with the Maven Wrapper, `mvnw` / `mvnw.cmd`)

## Project Structure

```
basicspringbootdemo
├── pom.xml
├── mvnw / mvnw.cmd
└── src
    ├── main
    │   ├── java/com/example/demo
    │   │   ├── SpringbootWebDemoApplication.java   Application entry point
    │   │   └── controller/HomeController.java      Handles GET /
    │   └── resources
    │       ├── application.properties              Port and app name
    │       └── templates/index.html                 Thymeleaf view
    └── test/java/com/example/demo
        └── SpringbootWebDemoApplicationTests.java   Default context-load test
```

## Prerequisites

- JDK 17 or later
- No external database or service is required
- Maven is not required to be pre-installed; the included Maven Wrapper downloads the correct Maven version automatically

## Cloning and Running

```
git clone https://github.com/senthilmuruganb/basicspringbootdemo.git
cd basicspringbootdemo
./mvnw spring-boot:run
```

On Windows, use `mvnw.cmd spring-boot:run` instead.

Once the application has started, open:

```
http://localhost:8081/
```

The page will display: "Welcome to Spring Boot Web App using STS!"

### Building a runnable jar (alternative)

```
./mvnw clean package
java -jar target/springboot-web-demo-0.0.1-SNAPSHOT.jar
```

## Application Walkthrough

- `SpringbootWebDemoApplication` is the standard Spring Boot entry point (`@SpringBootApplication`), started via `SpringApplication.run(...)`.
- `HomeController` maps `GET /` to the `home` method, which adds a `message` attribute to the model and returns the logical view name `index`.
- Spring resolves `index` to `templates/index.html`. The template reads the `message` attribute with `th:text="${message}"` and displays it inside an `<h2>` element.

## Configuration

`application.properties` sets:

```
server.port=8081
spring.application.name=springboot-web-demo
```

The application listens on port 8081 rather than the Spring Boot default of 8080.
