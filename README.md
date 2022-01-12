# automation-bdd-google

Hi:wave: Perkenalkan Namaku [Wisnu Munawar](https://www.instagram.com/wisnumnw):slightly_smiling_face:, biasa dipanggil Wisnu, Kamu dapat menemukanku di [Linkedin.](https://www.linkedin.com/in/wisnuwm)
<p>Kali ini saya akan membagikan tutorial Test Automation menggunakan Selenium menggunakan bahasa pemrograman Java + Cucumber.</p>
<p>Semoga bermanfaat.</p>
<p>Kamu dapat menonton videonya <a href=https://youtu.be/x59ddRRaHpE>disini</a></p>


**Tools yang dibutuhkan** :
- [Java 15](https://www.oracle.com/java/technologies/javase/jdk15-archive-downloads.html)
- [IntelliJ IDEA](https://www.jetbrains.com/idea/download/)
- IntelliJ IDEA Plugin :  [Cucumber for Java](https://plugins.jetbrains.com/plugin/7212-cucumber-for-java)
- IntelliJ IDEA Plugin : [Gherkin](https://plugins.jetbrains.com/plugin/9164-gherkin)
- [Chromedriver](https://chromedriver.chromium.org/downloads)
  or [Geckodriver](https://github.com/mozilla/geckodriver/releases)
- [Maven](https://maven.apache.org/download.cgi)

**Berikut adalah langkah2 nya :**

1. Buat Project pada IDE, disini saya menggunakan IntelliJ (https://www.jetbrains.com/idea/download/)
<img width="821" alt="Screen Shot 2021-10-23 at 14 42 25" src="https://user-images.githubusercontent.com/54229493/138548508-a77fcfa7-5726-4068-b4bb-45eb283d4ecf.png">
<img width="821" alt="Screen Shot 2021-10-23 at 14 42 46" src="https://user-images.githubusercontent.com/54229493/138548517-89d5debc-13db-4530-b993-c47b052deaed.png">

2. Install Plugin ini "Cucumber for Java" dan "Gherkin"

<img width="989" alt="Screen Shot 2021-10-23 at 14 45 34" src="https://user-images.githubusercontent.com/54229493/138548657-8d0320a9-af22-4bc0-b2af-192da322c7f9.png">

3. Buka pom.xml dan add dependency ini
```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>org.example</groupId>
    <artifactId>automation-bdd-google</artifactId>
    <version>1.0-SNAPSHOT</version>

    <properties>
        <maven.compiler.source>15</maven.compiler.source>
        <maven.compiler.target>15</maven.compiler.target>
    </properties>
    <dependencies>

        <!-- https://mvnrepository.com/artifact/io.cucumber/cucumber-java -->
        <dependency>
            <groupId>io.cucumber</groupId>
            <artifactId>cucumber-java</artifactId>
            <version>6.9.0</version>
        </dependency>

        <!-- https://mvnrepository.com/artifact/junit/junit -->
        <dependency>
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
            <version>4.13.1</version>
            <scope>test</scope>
        </dependency>

        <!-- https://mvnrepository.com/artifact/io.cucumber/cucumber-junit -->
        <dependency>
            <groupId>io.cucumber</groupId>
            <artifactId>cucumber-junit</artifactId>
            <version>6.9.0</version>
            <scope>test</scope>
        </dependency>

        <!-- https://mvnrepository.com/artifact/org.seleniumhq.selenium/selenium-java -->
        <dependency>
            <groupId>org.seleniumhq.selenium</groupId>
            <artifactId>selenium-java</artifactId>
            <version>3.141.59</version>
        </dependency>

        <!-- https://mvnrepository.com/artifact/net.masterthought/cucumber-reporting -->
        <dependency>
            <groupId>net.masterthought</groupId>
            <artifactId>cucumber-reporting</artifactId>
            <version>5.4.0</version>
        </dependency>


    </dependencies>

    <build>
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-surefire-plugin</artifactId>
                <version>2.22.0</version>
                <configuration>
                    <testFailureIgnore>true</testFailureIgnore>
                </configuration>
            </plugin>
            <plugin>
                <groupId>net.masterthought</groupId>
                <artifactId>maven-cucumber-reporting</artifactId>
                <version>2.8.0</version>
                <executions>
                    <execution>
                        <id>execution</id>
                        <phase>verify</phase>
                        <goals>
                            <goal>generate</goal>
                        </goals>
                        <configuration>
                            <projectName>automation-bdd-google</projectName>
                            <outputDirectory>${project.build.directory}/cucumber-report-html</outputDirectory>
                            <cucumberOutput>${project.build.directory}/cucumber.json</cucumberOutput>
                        </configuration>
                    </execution>
                </executions>
            </plugin>
        </plugins>
    </build>
</project>
```
4. Tambahkan Webdriver (disini saya menggunakan ChromeDriver dan bisa di download di "https://chromedriver.chromium.org/downloads") lalu buat Directory driver dan simpan ChromeDriver
<img width="737" alt="Screen Shot 2021-10-23 at 14 50 28" src="https://user-images.githubusercontent.com/54229493/138548747-aa594413-2b0e-42a6-964c-306dfbcfa92e.png">

5. Buat Directory "StepDef" dan "TestRunner" pada src/test/java dan juga buat Directory "Features" pada src/test/resources
<img width="465" alt="Screen Shot 2021-10-23 at 14 46 51" src="https://user-images.githubusercontent.com/54229493/138548839-de7dba43-6ac9-4d63-b69f-e8d53337da3c.png">

6. Buat Feature file "SearchGoogle.feature" pada directory Features
```gherkin
Feature: Search Google
  Scenario: I want to using feature search on google
    Given I Open browser
    And Open website Google
    And Located on google website
    When I search "Wisnu Munawar"
    Then Showing result related with "Wisnu Munawar"
```

7. Hover ke Gherkin scenarionya dan akan muncul action dan klik "More Action" lalu klik lagi "Create all step definitions" lalu buat nama class nya sesuai dengan nama Feature file dan klik "OK"
<img width="608" alt="Screen Shot 2021-10-23 at 14 52 34" src="https://user-images.githubusercontent.com/54229493/138549038-b2809d6e-aaec-4557-bede-11da51e7cb42.png">
<img width="781" alt="Screen Shot 2021-10-23 at 14 52 57" src="https://user-images.githubusercontent.com/54229493/138549042-31420728-1b7a-4ddc-9d5f-f49ce38c3518.png">
<img width="790" alt="Screen Shot 2021-10-23 at 14 53 28" src="https://user-images.githubusercontent.com/54229493/138549044-5d1b1526-2f61-49ab-b465-acd9395fe021.png">

8. Lalu akan otomatis ke generate scenarionya seperti dibawah ini
<img width="706" alt="Screen Shot 2021-10-23 at 14 54 47" src="https://user-images.githubusercontent.com/54229493/138549076-93d6eba3-825a-43eb-a260-bc96c691398a.png">

9. Isi scenario di java code nya seperti dibawah ini ya
```java
import io.cucumber.java.en.And;
import io.cucumber.java.en.Given;
import io.cucumber.java.en.Then;
import io.cucumber.java.en.When;
import org.openqa.selenium.By;
import org.openqa.selenium.Keys;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.chrome.ChromeOptions;

public class SearchGoogle {
    WebDriver driver;
    @Given("I Open browser")
    public void iOpenBrowser() {
        final String dir = System.getProperty("user.dir");
        System.out.println("current dir = " + dir);
        System.setProperty("webdriver.chrome.driver", dir+"/driver/chromedriver");
        driver = new ChromeDriver();
    }

    @And("Open website Google")
    public void openWebsiteGoogle() throws InterruptedException {
        driver.get("https://www.google.co.id/");
        Thread.sleep(1000);
    }

    @And("Located on google website")
    public void locatedOnGoogleWebsite() {
        driver.findElement(By.name("btnK")).isDisplayed();
    }

    @When("I search {string}")
    public void iSearch(String searchValue) {
        driver.findElement(By.name("q")).sendKeys(searchValue);
        driver.findElement(By.name("q")).sendKeys(Keys.ENTER);
    }

    @Then("Showing result related with {string}")
    public void showingResultRelatedWith(String result) {
        driver.findElement(By.xpath("//a[@href='https://id.linkedin.com/in/wisnuwm']")).isDisplayed();
        String urlLinkedinWisnu = driver.findElement(By.xpath("//a[@href='https://id.linkedin.com/in/wisnuwm']")).getText();
        System.out.println(urlLinkedinWisnu);
        driver.close();
        driver.quit();
    }
}
```
Dan untuk cara mencari Elementnya bagaimana?
Klik kanan aja lalu klik inspect element dan arahkan pada elementnya, contoh seperti dibawah ini :
<img width="1041" alt="Screen Shot 2021-10-23 at 15 00 10" src="https://user-images.githubusercontent.com/54229493/138549166-a63602d4-48c9-4172-bff3-a23e4d8ce2fb.png">
<img width="1119" alt="Screen Shot 2021-10-23 at 15 01 17" src="https://user-images.githubusercontent.com/54229493/138549174-d26d3e70-bd36-4ac6-8730-41d097305999.png">


10. Hover pada feature file dan klik Run
<img width="642" alt="Screen Shot 2021-10-23 at 15 28 17" src="https://user-images.githubusercontent.com/54229493/138549132-9cd1b307-8f6f-4646-a017-deec5fb6bd3d.png">

11. Maka akan otomatis running test nya, seperti video dibawah ini :


https://user-images.githubusercontent.com/54229493/138549271-4ad67366-9748-4df9-be78-0362eb72787d.mov

12. Buat java class "TestRunner" pada Directory TestRunner
<img width="1154" alt="Screen Shot 2021-10-23 at 15 34 24" src="https://user-images.githubusercontent.com/54229493/138549343-f278f808-c7ce-4ac1-bac0-df1325e5d9d6.png">

13. Lalu copy code ini 
```java
@RunWith(Cucumber.class)
@CucumberOptions(features="src/test/resources/Features",
        glue= {"StepDef"},
        plugin ={"pretty","json:target/cucumber.json"})
```
<img width="1121" alt="Screen Shot 2021-10-23 at 15 35 10" src="https://user-images.githubusercontent.com/54229493/138549369-166b962a-9ab0-4069-bc9e-b901ff99c19e.png">

14. Lalu open terminal pada IntelliJ dan ketikkan ```mvn test``` maka akan running test automation dan akan memunculkan result seperti ini
<img width="797" alt="Screen Shot 2021-10-23 at 15 38 32" src="https://user-images.githubusercontent.com/54229493/138549452-0c01cb11-199f-4bef-b59e-2aacda9728b0.png">

15. Lalu ketikkan ```mvn verify -DskipTests``` untuk generate report test yang sudah kita jalankan sebelumnya
<img width="989" alt="Screen Shot 2021-10-23 at 15 40 34" src="https://user-images.githubusercontent.com/54229493/138549537-6e6056a4-d4c6-4d06-b660-9487cf30ef9e.png">

16. Buka Directory target dan open file ini pada chrome
<img width="371" alt="Screen Shot 2021-10-23 at 15 41 02" src="https://user-images.githubusercontent.com/54229493/138549577-b9e7e03a-f24d-4b84-b97d-20e29bcd644f.png">
<img width="823" alt="Screen Shot 2021-10-23 at 15 41 34" src="https://user-images.githubusercontent.com/54229493/138549583-8b640d44-c4e3-45a1-940c-a9839bf103bf.png">

17. Maka hasil dari generate test tersebut adalah seperti ini:
<img width="1440" alt="Screen Shot 2021-10-23 at 15 41 42" src="https://user-images.githubusercontent.com/54229493/138549605-8ecefdd4-79be-41f9-99f3-efe991af5c8b.png">

Selamat Mencoba :)
