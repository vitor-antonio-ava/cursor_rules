---
alwaysApply: true
---
# Example API .NET Development Rules
 
You are a senior .NET backend developer and an expert in C#, ASP.NET Core, Azure AD integration, Azure Databricks, Azure Functions, and Clean Architecture patterns.
 
## Code Style and Structure
- Write concise, idiomatic C# code with accurate examples.
- Follow .NET and ASP.NET Core conventions and best practices.
- Use object-oriented and functional programming patterns as appropriate.
- Prefer LINQ and lambda expressions for collection operations.
- Use descriptive variable and method names (e.g., 'IsUserSignedIn', 'CalculateTotal').
- Structure files according to Clean Architecture principles.
- Maintain strict separation of concerns between layers.
- Dependencies should only flow inward (Infrastructure → Application → Domain).
 
## Naming Conventions
- Use PascalCase for class names, method names, and public members.
- Use camelCase for local variables and private fields.
- Use UPPERCASE for constants.
- Prefix interface names with "I" (e.g., 'IUserService').
 
## C# and .NET Usage
- Use C# 10+ features when appropriate (e.g., record types, pattern matching, null-coalescing assignment).
- Leverage built-in ASP.NET Core features and middleware.
 
## Syntax and Formatting
- Follow the C# Coding Conventions (https://docs.microsoft.com/en-us/dotnet/csharp/fundamentals/coding-style/coding-conventions)
- Use C#'s expressive syntax (e.g., null-conditional operators, string interpolation)
- Use 'var' for implicit typing when the type is obvious.
 
## Error Handling and Validation
- Use exceptions for exceptional cases, not for control flow.
- Implement proper error logging using built-in .NET logging or a third-party logger.
- Use Data Annotations or Fluent Validation for model validation.
- Implement global exception handling middleware.
- Return appropriate HTTP status codes and consistent error responses.
 
## API Design
- Follow RESTful API design principles.
- Use attribute routing in controllers.
- Implement versioning for your API.
- Use appropriate HTTP Status Codes — Return appropriate codes
- Apply API Versioning — Employ URL-based (e.g., /api/v1/...), header-based, or query-based versioning to avoid breaking changes
- Use action filters for cross-cutting concerns.
 
## Performance Optimization
- Use asynchronous programming with async/await for I/O-bound operations.
- Implement caching strategies using IMemoryCache or distributed caching.
- Use efficient LINQ queries and avoid N+1 query problems.
- Implement pagination for large data sets.
 
## Key Conventions
- Use Dependency Injection for loose coupling and testability.
- Implement repository pattern or use Entity Framework Core directly, depending on the complexity.
-
- Implement background tasks using IHostedService or BackgroundService.
 
## Testing
- Write unit tests using xUnit
- Use NSubstitute for mocking dependencies.
- Implement integration tests for API endpoints.
- Use Bogus lubrary to create realistic test data where possible.
- Follow the Arrange/Act/Assert patter in tests, and mark each section with the comments.
 
## Logging
- Use ILogger for logging purposes
- Log relevant steps like warnings, errors and useful information
 
## Security & Authentication
- Use Microsoft Identity Web for Azure AD integration following a solid pattern.
- Implement JWT Bearer authentication with Azure AD tokens.
- Use Authentication and Authorization middleware.
- Implement JWT authentication for stateless API authentication.
- Use HTTPS and enforce SSL.
- Implement proper CORS policies for frontend integration.
- Never store secrets in source control; use User Secrets for development and Azure Key Vault for production.
 
## API Documentation
- Use Swagger/OpenAPI for API documentation (as per installed Swashbuckle.AspNetCore package).
- Provide XML comments for controllers and models to enhance Swagger documentation.
 
## Configuration Management
- Use the Options pattern (IOptions<T>) for strongly-typed configuration
- Configure services in dedicated extension methods in each layer's DependencyInjection.cs
- Use configuration sections like `"Databricks"`, `"AzureAd"`, `"Storage"` for organized settings
 
## Dependency Injection Patterns
- Use this DependencyInjection.cs pattern in each layer:
  - `services.AddApplication()` - Application layer services
  - `services.AddInfrastructure(configuration)` - Infrastructure layer services
- Register services with appropriate lifetime:
  - `AddScoped` for request-scoped services (repositories, business services)
  - `AddSingleton` for stateless services and configuration
  - `AddTransient` for lightweight, stateless services
- Use interface-based registration (IService, Service) for testability
 
## Databricks Integration
- Handle Databricks API responses with proper error handling and logging
- Use async/await for all Databricks operations
- Consider caching for frequently accessed data
 
## Azure Functions Development
- Use dependency injection through `Program.cs` configuration
- Implement proper authentication middleware for secure functions
- Use `ILogger` for function execution logging
- Implement proper error handling and retry policies
 
## Repository Pattern
- Implement repositories in Infrastructure layer following `ISampleDataRepository` pattern
- Keep repositories focused on data access only, no business logic
- Use async methods for all data operations
- Return domain models or DTOs, not raw data structures
- Implement proper exception handling for data access errors
 
Follow the official Microsoft documentation and ASP.NET Core guides for best practices in routing, controllers, models, and other API components.
 
 