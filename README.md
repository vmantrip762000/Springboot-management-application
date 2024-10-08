﻿# employee-profile-management

## Code Explanation:

### MainController.java

Defines a Spring REST controller (@RestController) for handling user data.
Provides a /demo/add endpoint (@PostMapping) that takes user name and email as request parameters, creates a new User object, saves it to the database using userRepository.save(), and returns the saved user.
Exposes a /demo/all endpoint (@GetMapping) that retrieves all users from the database using userRepository.findAll() and returns them.
User.java

Represents a user entity with attributes: id (auto-generated primary key), name, and email.
Uses JPA annotations (@Entity, @Id, @GeneratedValue) for persistence.
Provides getter and setter methods for each attribute.
UserRepository.java

Extends Spring Data JPA's CrudRepository<User, Integer>, providing basic CRUD (Create, Read, Update, Delete) operations on User entities with an integer ID.
### application.properties

Configures Spring Boot application properties:
spring.application.name sets the application name (demo)
spring.jpa.hibernate.ddl-auto specifies database schema update behavior (update in this case)
spring.datasource.url defines the database connection URL (including Aiven cloud details)
CRITICALLY: spring.datasource.username contains the username for database access
CRITICALLY: spring.datasource.password SHOULD NOT be stored in plain text. Instead, use GitHub Secrets or environment variables as explained later.
spring.datasource.driver-class-name sets the JDBC driver class for MySQL.

### DemoApplicationTests.java

A basic Spring Boot test class using @SpringBootTest.
The @Test annotation typically holds a method that tests the application's context loading (contextLoads() in this example). More comprehensive unit and integration tests would be added for a fully tested application.
Importance of DemoApplicationsTest.java

This test verifies that the Spring Boot application context loads successfully.
More tests would be necessary to ensure the functionality of the REST endpoints and database interactions.
