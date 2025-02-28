# AM Spring Parent POM

This is a parent POM project that provides common dependencies and configurations for AM microservices.

## Features

- Pre-configured Spring Boot dependencies
- Common third-party libraries with managed versions
- Standardized build configuration
- Development tools and testing frameworks
- Automated builds and publishing via GitHub Actions

## Usage

To use this parent POM in your microservice, first add the GitHub Packages repository to your Maven settings (`~/.m2/settings.xml`):

```xml
<settings>
  <servers>
    <server>
      <id>github</id>
      <username>${github.user}</username>
      <password>${github.token}</password>
    </server>
  </servers>
</settings>
```

Then add the following to your project's `pom.xml`:

```xml
<parent>
    <groupId>org.am.microservices</groupId>
    <artifactId>am.spring.parent</artifactId>
    <version>0.0.1-SNAPSHOT</version>
</parent>

<repositories>
    <repository>
        <id>github</id>
        <url>https://maven.pkg.github.com/${parent.groupId}/${parent.artifactId}</url>
    </repository>
</repositories>
```

## Available Dependencies

The parent POM includes the following major dependency groups:

1. Spring Boot Starters
   - spring-boot-starter-actuator
   - spring-boot-starter-webflux
   - spring-boot-starter-web
   - spring-boot-starter-data-jpa

2. Development Tools
   - lombok
   - spring-boot-devtools

3. Database Drivers
   - mssql-jdbc
   - postgresql

4. Testing Dependencies
   - spring-boot-starter-test
   - reactor-test
   - spring-kafka-test

5. Other Dependencies
   - jackson-databind
   - mapstruct
   - tensorflow
   - opencsv
   - azure-spring-cloud
   - springdoc-openapi

## Version Management

All dependency versions are managed through properties in the parent POM. To override a version in your child project, you can define the same property in your project's properties section:

```xml
<properties>
    <jackson.version>2.15.3</jackson.version> <!-- Override jackson version -->
</properties>
```

## CI/CD

This project uses GitHub Actions for continuous integration and deployment:

- Builds are triggered on:
  - Push to main/master branch
  - Pull requests to main/master
  - Release creation
- Snapshot versions are automatically published to GitHub Packages on successful builds
- Release versions are published when a new GitHub release is created

## Support

For any issues or questions, please contact the AM development team.
