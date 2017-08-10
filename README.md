# springfileuploadWithHibernate-3
Day 4 - Spring MVC 3.0 - springfileuploadWithHibernate Example

> In this tutorial you will know how to create Spring 3.0 MVC hello world example in simplest way.


### Project Structure

![](extra/projectstructure.JPG)


#### Step 1 - Let’s Setup Environment

1. Spring 3.2.13.RELEASE and any latest version
2. Maven 3 and any latest version
3. JDK 1.6 / JDK 1.7 / JDK 1.8 / JDK 1.9
4. Eclipse Kepler / Eclipse Juno / Eclipse Neon
5. Tomcat 6 / Tomcat 7 / Tomcat 8 / Tomcat 9

#### Step 2 - Create Project

> Click on File > New > Dynamic Web Project

####![](extra/step2.1.JPG)
####![](extra/step2.2.JPG)
####![](extra/step2.3.JPG)


#### Step 2 - Add Dipendency in ``pom.xml`` file

```XML
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd">
	<modelVersion>4.0.0</modelVersion>
	<groupId>com.journaldev.spring</groupId>
	<artifactId>SpringFileUploadHibernate</artifactId>
	<name>SpringFileUploadHibernate</name>
	<packaging>war</packaging>
	<version>1.0.0-BUILD-SNAPSHOT</version>
	<properties>
		<java-version>1.6</java-version>
		<org.springframework-version>4.0.0.RELEASE</org.springframework-version>
		<org.aspectj-version>1.7.4</org.aspectj-version>
		<org.slf4j-version>1.7.5</org.slf4j-version>
	</properties>
	<dependencies>
	<!-- Apache Commons FileUpload --> 
	<dependency>
		<groupId>commons-fileupload</groupId>
		<artifactId>commons-fileupload</artifactId>
		<version>1.3.1</version>
	</dependency>
 
	<!-- Apache Commons IO --> 
	<dependency>
		<groupId>commons-io</groupId>
		<artifactId>commons-io</artifactId>
		<version>2.4</version>
	</dependency>
 
		<!-- Spring -->
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-context</artifactId>
			<version>${org.springframework-version}</version>
			<exclusions>
				<!-- Exclude Commons Logging in favor of SLF4j -->
				<exclusion>
					<groupId>commons-logging</groupId>
					<artifactId>commons-logging</artifactId>
				 </exclusion>
			</exclusions>
		</dependency>
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-webmvc</artifactId>
			<version>${org.springframework-version}</version>
		</dependency>
				
		<!-- AspectJ -->
		<dependency>
			<groupId>org.aspectj</groupId>
			<artifactId>aspectjrt</artifactId>
			<version>${org.aspectj-version}</version>
		</dependency>
		 <!-- MySQL database driver -->
	<dependency>
		<groupId>mysql</groupId>
		<artifactId>mysql-connector-java</artifactId>
		<version>5.1.9</version>
	</dependency>
	
	<!-- Hibernate framework -->
	<dependency>
            <groupId>org.hibernate</groupId>
            <artifactId>hibernate-core</artifactId>
            <version>4.3.10.Final</version>
        </dependency>
         <!--orm  -->
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-orm</artifactId>
            <version>${org.springframework-version}</version>
        </dependency>	
		
		<!-- Logging -->
		<dependency>
			<groupId>org.slf4j</groupId>
			<artifactId>slf4j-api</artifactId>
			<version>${org.slf4j-version}</version>
		</dependency>
		<dependency>
			<groupId>org.slf4j</groupId>
			<artifactId>jcl-over-slf4j</artifactId>
			<version>${org.slf4j-version}</version>
			<scope>runtime</scope>
		</dependency>
		<dependency>
			<groupId>org.slf4j</groupId>
			<artifactId>slf4j-log4j12</artifactId>
			<version>${org.slf4j-version}</version>
			<scope>runtime</scope>
		</dependency>
		<dependency>
			<groupId>log4j</groupId>
			<artifactId>log4j</artifactId>
			<version>1.2.15</version>
			<exclusions>
				<exclusion>
					<groupId>javax.mail</groupId>
					<artifactId>mail</artifactId>
				</exclusion>
				<exclusion>
					<groupId>javax.jms</groupId>
					<artifactId>jms</artifactId>
				</exclusion>
				<exclusion>
					<groupId>com.sun.jdmk</groupId>
					<artifactId>jmxtools</artifactId>
				</exclusion>
				<exclusion>
					<groupId>com.sun.jmx</groupId>
					<artifactId>jmxri</artifactId>
				</exclusion>
			</exclusions>
			<scope>runtime</scope>
		</dependency>

		<!-- @Inject -->
		<dependency>
			<groupId>javax.inject</groupId>
			<artifactId>javax.inject</artifactId>
			<version>1</version>
		</dependency>
				
		<!-- Servlet -->
		<dependency>
			<groupId>javax.servlet</groupId>
			<artifactId>servlet-api</artifactId>
			<version>2.5</version>
			<scope>provided</scope>
		</dependency>
		<dependency>
			<groupId>javax.servlet.jsp</groupId>
			<artifactId>jsp-api</artifactId>
			<version>2.1</version>
			<scope>provided</scope>
		</dependency>
		<dependency>
			<groupId>javax.servlet</groupId>
			<artifactId>jstl</artifactId>
			<version>1.2</version>
		</dependency>
	
		<!-- Test -->
		<dependency>
			<groupId>junit</groupId>
			<artifactId>junit</artifactId>
			<version>4.7</version>
			<scope>test</scope>
		</dependency>        
	</dependencies>
    <build>
        <plugins>
            <plugin>
                <artifactId>maven-eclipse-plugin</artifactId>
                <version>2.9</version>
                <configuration>
                    <additionalProjectnatures>
                        <projectnature>org.springframework.ide.eclipse.core.springnature</projectnature>
                    </additionalProjectnatures>
                    <additionalBuildcommands>
                        <buildcommand>org.springframework.ide.eclipse.core.springbuilder</buildcommand>
                    </additionalBuildcommands>
                    <downloadSources>true</downloadSources>
                    <downloadJavadocs>true</downloadJavadocs>
                </configuration>
            </plugin>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <version>2.5.1</version>
                <configuration>
                    <source>1.6</source>
                    <target>1.6</target>
                    <compilerArgument>-Xlint:all</compilerArgument>
                    <showWarnings>true</showWarnings>
                    <showDeprecation>true</showDeprecation>
                </configuration>
            </plugin>
            <plugin>
                <groupId>org.codehaus.mojo</groupId>
                <artifactId>exec-maven-plugin</artifactId>
                <version>1.2.1</version>
                <configuration>
                    <mainClass>org.test.int1.Main</mainClass>
                </configuration>
            </plugin>
        </plugins>
    </build>
</project>

```


#### Step 3 - Add Spring Servlet in ``webapp\WEB-INF\web.xml`` file

```XML
<?xml version="1.0" encoding="UTF-8"?>
<web-app version="2.5" xmlns="http://java.sun.com/xml/ns/javaee"
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://java.sun.com/xml/ns/javaee http://java.sun.com/xml/ns/javaee/web-app_2_5.xsd">

	<!-- The definition of the Root Spring Container shared by all Servlets and Filters -->
	<context-param>
		<param-name>contextConfigLocation</param-name>
		<param-value>/WEB-INF/spring/root-context.xml</param-value>
	</context-param>
	
	<!-- Creates the Spring Container shared by all Servlets and Filters -->
	<listener>
		<listener-class>org.springframework.web.context.ContextLoaderListener</listener-class>
	</listener>

	
	<!-- Processes application requests -->
	<servlet>
		<servlet-name>appServlet</servlet-name>
		<servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
		<init-param>
			<param-name>contextConfigLocation</param-name>
			<param-value>/WEB-INF/spring/appServlet/servlet-context.xml</param-value>
		</init-param>
		<load-on-startup>1</load-on-startup>
	</servlet>
		
	<servlet-mapping>
		<servlet-name>appServlet</servlet-name>
		<url-pattern>/</url-pattern>
	</servlet-mapping>

</web-app>

```


#### Step 4 - Add Spring Configration in ``\webapp\WEB-INF\spring\appServlet\servlet-context.xml`` file

```XML
<?xml version="1.0" encoding="UTF-8"?>
<beans:beans xmlns="http://www.springframework.org/schema/mvc"
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:beans="http://www.springframework.org/schema/beans"
	xmlns:context="http://www.springframework.org/schema/context"
	xsi:schemaLocation="http://www.springframework.org/schema/mvc http://www.springframework.org/schema/mvc/spring-mvc.xsd
		http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd
		http://www.springframework.org/schema/context http://www.springframework.org/schema/context/spring-context.xsd">

	<!-- DispatcherServlet Context: defines this servlet's request-processing 
		infrastructure -->

	<!-- Enables the Spring MVC @Controller programming model -->
	<annotation-driven />
	<context:component-scan base-package="com.pratikJoshi.spring" />
	
	
	<beans:bean id="data_image" class="org.springframework.beans.factory.config.PropertyPlaceholderConfigurer">
 
    	<beans:property name="location" value="classpath:data_image.properties" />
 
	</beans:bean>

	<!-- Handles HTTP GET requests for /resources/** by efficiently serving 
		up static resources in the ${webappRoot}/resources directory -->
	<resources mapping="/**" location="/" />

	<!-- Resolves views selected for rendering by @Controllers to .jsp resources 
		in the /WEB-INF/views directory -->
	<beans:bean
		class="org.springframework.web.servlet.view.InternalResourceViewResolver">
		<beans:property name="prefix" value="/WEB-INF/views/" />
		<beans:property name="suffix" value=".jsp" />
	</beans:bean>
	<beans:bean class="org.springframework.jdbc.datasource.DriverManagerDataSource" id="dataSource">
		 <beans:property name="driverClassName" value="com.mysql.jdbc.Driver"></beans:property>
		 <beans:property name="url" value="jdbc:mysql://localhost:3306/uploadfile"></beans:property>
		 <beans:property name="username" value="root"></beans:property>
		 <beans:property name="password" value="root"></beans:property>
	</beans:bean>
	<beans:bean class="org.springframework.orm.hibernate4.LocalSessionFactoryBean" id="sessionFactory">
			<beans:property name="dataSource" ref="dataSource"></beans:property>
			<beans:property name="annotatedClasses">
				   <beans:list>
					    <beans:value>com.pratikJoshi.spring.model.Avatar</beans:value>
				   </beans:list>
			</beans:property>
	<beans:property name="hibernateProperties">
		<beans:props>
			  <beans:prop key="hibernate.dialect">org.hibernate.dialect.MySQL5Dialect</beans:prop>
			  <beans:prop key="hibernate.show_sql">true</beans:prop>
			  <beans:prop key="hibernate.hbm2ddl.auto">update</beans:prop> 
		</beans:props>
	</beans:property>
</beans:bean>
<beans:bean id="transactionManager" class="org.springframework.orm.hibernate4.HibernateTransactionManager" >
		<beans:property name="sessionFactory" ref="sessionFactory"></beans:property>
	</beans:bean>
	<beans:bean class="org.springframework.orm.hibernate4.HibernateTransactionManager" id="hibernateTransactionManager">
		<beans:property name="sessionFactory" ref="sessionFactory"></beans:property>
	</beans:bean>

	<beans:bean id="multipartResolver"
		class="org.springframework.web.multipart.commons.CommonsMultipartResolver">

		 <!-- setting maximum upload size -->
		<beans:property name="maxUploadSize" value="500000" />

	</beans:bean>


	


</beans:beans>

```


#### Step 5 - Add View to project ``webapp\WEB-INF\views\upload.jsp`` file

```JSP
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<%@ page session="false" %>
<html>
<head>
<title>Upload File Request Page</title>
</head>
<body>

	<form method="POST" action="uploadFile" enctype="multipart/form-data">
		File to upload: <input type="file" name="file"><br /> 
		Name: <input type="text" name="name"><br /> <br /> 
		<input type="submit" value="Upload"> Press here to upload the file!
	</form>
	
</body>
</html>
```

##![](extra/output.JPG)


#### Step 6 - Add Controller Class in ``src\main\java\com\pratikJoshi\spring\controller\FileUploadController.java`` folder

> Right Click on ``src`` folder > New > Class

#![](extra/step7.1.JPG)

```JAVA
package com.pratikJoshi.spring.controller;

import java.io.BufferedOutputStream;
import java.io.ByteArrayInputStream;
import java.io.File;
import java.io.FileOutputStream;
import java.io.IOException;
import java.util.Locale;

import com.pratikJoshi.spring.controller.Property;
import com.pratikJoshi.spring.dao.FileUploadDao;
import com.pratikJoshi.spring.model.Avatar;
import com.pratikJoshi.spring.model.FileUpload;

import org.apache.commons.io.IOUtils;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import org.springframework.beans.factory.annotation.Autowired;
//import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Controller;
import org.springframework.ui.Model;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestMethod;
import org.springframework.web.bind.annotation.RequestParam;
import org.springframework.web.bind.annotation.ResponseBody;
import org.springframework.web.multipart.MultipartFile;

/**
 * Handles requests for the application file upload requests
 */
@Controller
public class FileUploadController {

	private static final Logger logger = LoggerFactory.getLogger(FileUploadController.class);
	
	@Autowired
	private FileUploadDao fileUpload;
	
	@RequestMapping(value = "/", method = RequestMethod.GET)
	public String home(Locale locale, Model model) {
		long startTime = System.currentTimeMillis();
		logger.info("Welcome home! The client locale is {}.", locale);
		long endTime   = System.currentTimeMillis();
		long totalTime = endTime - startTime;
		System.out.println("/time"+totalTime);
		return "upload";
	}
	@RequestMapping(value = "/uploadFile", method = RequestMethod.POST)
	public String uploadFileHandler(@RequestParam("name") String name,
			@RequestParam("file") MultipartFile file) {

		if (!file.isEmpty()) {
			try {
				byte[] bytes = file.getBytes();
				Property property =new Property();
				// Creating the directory to store file
				//String rootPath = System.getProperty("");
				//String pathFolder = property.getPropValues();
				//String rootPath = System.getProperty("catalina.home");
				String rootPath = "D:prex";
				System.out.println("in controller pathFolder is"+rootPath);
				String rootPath1 = rootPath + File.separator + "tmpFiles";
				File dir = new File(rootPath + File.separator + "tmpFiles");
				if (!dir.exists()){
					dir.mkdirs();
				}
				
				// Create the file on server
				File serverFile = new File(dir.getAbsolutePath()
						+ File.separator + name);
				String serverFile1 =dir.getAbsolutePath()+ File.separator + name;
				Avatar avatar = new Avatar();
				avatar.setName(name);
				avatar.setPathOfFile(serverFile1);
				FileUpload fu= new FileUpload();
				fu.setFile(file);
				int id = fileUpload.save(avatar);
				BufferedOutputStream stream = new BufferedOutputStream(
						new FileOutputStream(serverFile));
				stream.write(bytes);
				stream.close();

				logger.info("Server File Location="
						+ serverFile.getAbsolutePath());

				//return "You successfully uploaded file=" + name;
				return "redirect:/viewAll";
			} catch (Exception e) {
				return "You failed to upload " + name + " => " + e.getMessage();
			}
		} else {
			return "You failed to upload " + name
					+ " because the file was empty.";
		}
	}
	
	@RequestMapping(value = "/viewAll", method = RequestMethod.GET)
	public String viewAll(Locale locale, Model model) throws IOException {
		logger.info("Welcome viewAll()");
		FileUpload fu = new FileUpload();
		model.addAttribute("showAll", fileUpload.viewAll());
		//model.addAttribute("file", fu.getFile());
		Avatar avatar = new Avatar();
		byte[] bytearr = avatar.getPathOfFile().getBytes();
		ByteArrayInputStream stream = new   ByteArrayInputStream(bytearr);
		String myString = IOUtils.toString(stream, "UTF-8");
		model.addAttribute("file", myString);
		return "showAll";
	}

	/**
	 * Upload multiple file using Spring Controller
	 */
	@RequestMapping(value = "/uploadMultipleFile", method = RequestMethod.POST)
	public @ResponseBody String uploadMultipleFileHandler(@RequestParam("name") String[] names,
			@RequestParam("file") MultipartFile[] files) {

		if (files.length != names.length)
			return "Mandatory information missing";

		String message = "";
		for (int i = 0; i < files.length; i++) {
			MultipartFile file = files[i];
			String name = names[i];
			try {
				byte[] bytes = file.getBytes();

				// Creating the directory to store file
				String rootPath = System.getProperty("catalina.home");
				File dir = new File(rootPath + File.separator + "tmpFiles");
				if (!dir.exists())
					dir.mkdirs();

				// Create the file on server
				File serverFile = new File(dir.getAbsolutePath()
						+ File.separator + name);
				BufferedOutputStream stream = new BufferedOutputStream(
						new FileOutputStream(serverFile));
				stream.write(bytes);
				stream.close();

				logger.info("Server File Location="
						+ serverFile.getAbsolutePath());

				message = message + "You successfully uploaded file=" + name
						+ "<br />";
			} catch (Exception e) {
				return "You failed to upload " + name + " => " + e.getMessage();
			}
		}
		return message;
	}
}

```
#### Step 7 - Add dao Class in ``src\main\java\com\pratikJoshi\spring\dao\FileUploadDao.java`` folder

> Right Click on ``src`` folder > New > Class

#![](extra/step7.1.JPG)

```JAVA
package com.pratikJoshi.spring.dao;



import java.util.ArrayList;

import org.hibernate.Query;
import org.hibernate.Session;
import org.hibernate.SessionFactory;
import org.hibernate.Transaction;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Repository;

import com.pratikJoshi.spring.model.Avatar;

@Repository
public class FileUploadDao {
	@Autowired(required=true)
	private SessionFactory sessionFactory;

	public int save(Avatar avatar) {
		
		Session session = sessionFactory.openSession();
		Transaction tx = session.beginTransaction();
		int id = (Integer) session.save(avatar);
		tx.commit();
		session.close();
		
		return id;
	}

	public ArrayList<Avatar> viewAll() {
		ArrayList<Avatar> empList = new ArrayList<Avatar>();
		 /*for(Employee empBean : empList){
	            logger.info("Person List::"+p);
	        }*/
		Session session= sessionFactory.openSession();
		Transaction tx = session.beginTransaction();
		String hql = "FROM Avatar ";
		Query query = session.createQuery(hql);
		return (ArrayList<Avatar>) query.list();
	}

}


```


# That's it... you are ready to run

> Right Click on Project > Run As > Run on Server > Select Tomcat Server and click ``finish``

### Note

> In ``spring-web-servlet.xml`` file prefix ``XXX-servlet.xml`` should be same as servlet-name described in ``web.xml`` file

```XML
<servlet>
	<servlet-name>spring-web</servlet-name>
	<servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
	<load-on-startup>1</load-on-startup>
</servlet>
<servlet-mapping>
	<servlet-name>spring-web</servlet-name>
	<url-pattern>/</url-pattern>
</servlet-mapping>
```


## Meta

Pratik Joshi - pratik.joshi7859@gmail.com

Distributed under the GPL V3.0 license. See ``LICENSE`` for more information.
