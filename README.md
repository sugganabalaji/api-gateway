# API Gateway

The **API Gateway** serves as the single entry point for all client requests in the microservices architecture.  
It routes, filters, and secures requests to backend services such as the **Question Service**, **Quiz Service**, and **Discovery Service**.

---

## 🚀 Features
- Centralized entry point for all microservices
- Intelligent routing to Question and Quiz services
- Integrated with **Discovery Service (Eureka)** for dynamic service lookup
- Request filtering and logging
- Security features (JWT/OAuth2 authentication)
- Supports load balancing and fault tolerance

---

## 🏗️ Tech Stack
- **Backend**: Java 17, Spring Boot
- **Gateway Framework**: Spring Cloud Gateway
- **Service Discovery**: Eureka
- **Build Tool**: Maven

---

## 📂 Project Structure
```
  api-gateway/
      ├── src/main/java/com/app/ApiGatewayApplication.java   # Main class
      ├── src/main/resources/application.properties         # Configurations
      ├── pom.xml
      └── README.md
```

---

## ⚙️ Setup & Quickstart

### 1. Clone the repository
```bash
  git clone https://github.com/your-username/api-gateway.git
  cd api-gateway
```
### 2. Configure application.properties
```
  spring.application.name=api-gateway
  server.port=8765
  
  # Eureka Discovery Service
  eureka.client.service-url.defaultZone=http://localhost:8761/eureka/

  spring.cloud.gateway.discovery.locator.enabled=true
  spring.cloud.gateway.discovery.locator.lower-case-service-id=true

  # Routing rules
  spring.cloud.gateway.routes[0].id=question-service
  spring.cloud.gateway.routes[0].uri=lb://QUESTION-MICROSERVICE
  spring.cloud.gateway.routes[0].predicates[0]=Path=/questions/**
  
  spring.cloud.gateway.routes[1].id=quiz-service
  spring.cloud.gateway.routes[1].uri=lb://QUIZ-MICROSERVICE
  spring.cloud.gateway.routes[1].predicates[0]=Path=/quiz/**
```
### 3. Run the gateway
```bash
  mvn spring-boot:run
```
### 4. Access APIs
Clients can now call:

`http://localhost:8765/QUESTION-MICROSERVICE/questions/...`

`http://localhost:8765/QUIZ-MICROSERVICE/quiz/...`

## ✅ Advantages
- Simplifies client communication with microservices
- Provides centralized security and monitoring
- Enables dynamic routing via Discovery Service
- Improves scalability and resilience

## 📌 Future Enhancements
- Add rate limiting and throttling
- Implement API versioning
- Enhance monitoring with distributed tracing (Zipkin/ELK)

## 👨‍💻 Author
Developed by **Balaji Suggana**

Senior Software Engineer | Java/Spring | Cloud & AI Integration
