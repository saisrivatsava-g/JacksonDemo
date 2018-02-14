# Jackson Documentation

# JSON
JSON is short for JavaScript Object Notation. 
JSON is a popular data exchange format between browsers and web servers because the browsers can parse JSON into JavaScript objects natively.
On the server, however, JSON needs to be parsed and generated using JSON APIs.

# Jackson
Jackson is a Java JSON API which provides several different ways to work with JSON.

# Adding Jackson to Project

Add the following dependencies to the maven project.
```
<dependency>
    <groupId>com.fasterxml.jackson.core</groupId>
    <artifactId>jackson-core</artifactId>
    <version>2.9.4</version>
</dependency>
<dependency>
    <groupId>com.fasterxml.jackson.core</groupId>
    <artifactId>jackson-annotations</artifactId>
    <version>2.9.4</version>
</dependency>
<dependency>
    <groupId>com.fasterxml.jackson.core</groupId>
    <artifactId>jackson-databind</artifactId>
    <version>2.9.4</version>
</dependency>
```
# Jackson ObjectMapper Example

JacksonDemo.java
```
import java.io.IOException;
import com.fasterxml.jackson.databind.ObjectMapper;

public class JacksonDemo {

	public static void main(String[] args) {
		objectMapperMethodDemo();
	}

	private static void objectMapperMethodDemo() {
		String bookJsonData = "{ \"name\" : \"sherlock holmes\", \"author\" : \"Arthur Conan Doyle\" , \"isbnNumber\" : 3436, \"category\" : \"fictional\"}";
		ObjectMapper objectMapper = new ObjectMapper();
		// objectMapper.enable(SerializationConfig.Feature.INDENT_OUTPUT);
		try {
			Book sherlockHomes = objectMapper.readValue(bookJsonData, Book.class);
			System.out.println(sherlockHomes.getName());
			System.out.println(sherlockHomes.getAuthor());
			System.out.println(sherlockHomes.getIsbnNumber());
			System.out.println(sherlockHomes.getCategory());

		} catch (IOException e) {
			System.out.println("exception" + e);
		}
	}
}
```
Book.java
```
import lombok.Data;

public @Data class Book {
	private String name;
	private String author;
	private int isbnNumber;
	private String category;
}
```

For complete info about Jackson visit http://tutorials.jenkov.com/java-json/index.html 
