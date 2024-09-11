# Use an official Maven image to build the application
FROM maven:3.8.6-openjdk-17 AS build

# Set the working directory
WORKDIR /app

# Copy the pom.xml and source code into the container
COPY pom.xml .
COPY src ./src

# Build the application
RUN mvn clean package -DskipTests

# Use an OpenJDK image to run the application
FROM openjdk:17-jdk

# Set the working directory
WORKDIR /app

# Copy the JAR file from the build stage
COPY --from=build /app/target/my-app-1.0-SNAPSHOT.jar my-app.jar

# Expose the port on which the application will run
EXPOSE 8080

# Run the JAR file
ENTRYPOINT ["java", "-jar", "my-app.jar"]
