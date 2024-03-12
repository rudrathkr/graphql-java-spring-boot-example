# General Stuff for GraphQL
```
GraphQL common tools:​

Playground​

Postman​

GraphQL Explorer​
​=============================================
Query (a read-only fetch) - Get​

Mutation (a write followed by fetch) - New, Update, Delete​

Subscription (a long‐lived request that fetches data in response to source events.)​

Error Handling​

```

# Testing and Automation Strategies and Best Practices
```
        Know the Type of API to test – Rest, Soap, GraphQL​
        
        Read and understand the documentation​
        
            Rest – Swagger (Rest API)​
            
            GraphQL – Libraries in node as npm – graphql docs, spectaql(explorer endpoint)​
        
        Understand the schema and how they are interrelated ​
        
        Functional Testing - understand the types, queries, mutations, subscriptions​
        
        Focus should on testing schemas, query and mutation(Similar to Rest)​
        
            Missing  required fields.​
            
            Incorrect argument types.​
            
            Validation of schema changes​
            
            Violating custom validations.​
            
            Field-level validations.​
            
            Input object validations.​
        
        Try and explore the network tab of chrome and get the details – Headers, endpoints, type of requests​
        
        All of the request is a Post ​
        
        Convert the queries in rest assured as Json payloads before sending ​
        
        Performance Testing – Complex Queries , Server performance monitoring​
        
        All other functionality of Rest Assured/Karate Framework can be used​

      Begin by tool and language identification ​
      
        Java  - Rest Assured, Karate, TestGraphQL​
        
        JS – SuperTest,Jest, Mocha​
        
        Ready API ​
        
      Error handling and resilience testing -  Query Error, Validation Error , Resolver error​
      
        Empty arrays.​
        
        Maximum/minimum values.​
        
        Invalid query handling.​
        
        Authentication failures.​
        
        Authorization denials.​
        
      Strategies around framework – Data driven, keyword driven, TestNG, Junit remains same ​
      
      Data and payload can be passed at run time​
      
      Security Testing – Authorization and Authentication​
      
      Performance testing – Jmeter ​
      
        Concurrent request handling.​
        
        Response time evaluation.​
```

# graphql-java-spring-boot-example
Sample app for my tutorial [Building a GraphQL Server with Spring Boot](https://app.pluralsight.com/guides/building-a-graphql-server-with-spring-boot). 

Updated by [@Ansonator](https://github.com/Ansonator) to recent versions of Spring Boot and GraphQL Java.

The [tutorial branch](https://github.com/eh3rrera/graphql-java-spring-boot-example/tree/tutorial) contains the original demo app.

You'll need [Java 11 or 17](https://www.oracle.com/java/technologies/downloads/).

Clone this repo and execute `mvnw spring-boot:run`. Or inside an IDE, execute the class `com.example.DemoGraphQL.DemoGraphQlApplication`.

To access the database, you can go to [http://localhost:8080/h2-console/login.jsp](http://localhost:8080/h2-console/login.jsp) and enter the following information:
- JDBC URL: jdbc:h2:mem:testdb
- User Name: sa
- Password: <blank>

Or go to [http://localhost:8080/graphiql](http://localhost:8080/graphiql) to start executing queries. For example:
```
{
  findAllBooks {
    id
    isbn
    title
    pageCount
    author {
      firstName
      lastName
    }
  }
}
```

Or:
```
mutation {
  newBook(
    title: "Java: The Complete Reference, Tenth Edition", 
    isbn: "1259589331", 
    author: 1) {
      id title
  }
}
```
Use these for queries:
```
1. Open browser type http://localhost:8080/graphiql 

In query send  

{ 

  findAllBooks { 

    id 

    isbn 

    title 

    pageCount 

    author { 

      firstName 

      lastName 

    } 

  } 

} 

 

3. Add new Author 

mutation{ 

  newAuthor(firstName: "mike",lastName: "herd"){ 

    id 

    firstName 

    lastName 

     

  } 

} 

4. Display all authors 

{ 

  findAllAuthors{ 

    id 

    firstName 

    lastName 

  } 

} 

5. Countallauthors 

{ 

  countAuthors 

} 

6. Add new book  

mutation{ 

  newBook(title:"Macbeth",isbn:"879700AB",pageCount: 1000,author:1){ 

    id 

    title 

    isbn 

  } 

} 


```





# Extras

This build demos some UIs hosted at [graphql-java-kickstart](https://github.com/graphql-java-kickstart/graphql-spring-boot).
  * Launch with `mvn spring-boot:run`
  * Open a browser to view UIs at the following links:
    * [GraphiQL](http://localhost:8080/graphiql)
    * [Altair](http://localhost:8080/altair)
    * [Playground](http://localhost:8080/playground)  
    * [Voyager](http://localhost:8080/voyager)
# Test Subscription using the following steps outlined
```
Listen to an event  -1 

----------------------------------- 

1. Open the Explorer - https://hasura.io/learn/graphql 

subscription { 

  online_users { 

    id 

    last_seen 

    user { 

      name 

    } 

  } 

} 
Run it
 

2. Fire the event from another NEW browser –2 

 Open the Explorer - https://hasura.io/learn/graphql 

mutation updateLastSeen($now:timestamptz!){ 

  update_users(where:{},_set:{last_seen:$now}){ 

    affected_rows 

  } 

   

} 

Query variables 

{ 

  "now":"2024-03-08T16:37:34.051Z" 

} 

 

Do a console and get the time (new Date()).toISOString() ......get this value and change in the now variable and run this

3. Immediately go to first step browser and you should see the online user updated. (Time is key here so better be fast as the notification will vanish in 5-6 seconds)

```

# License
MIT
