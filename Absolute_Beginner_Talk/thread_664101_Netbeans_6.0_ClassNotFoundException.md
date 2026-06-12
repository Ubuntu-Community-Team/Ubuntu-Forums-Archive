---
title: "Netbeans 6.0 ClassNotFoundException"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by Mubat on 2008-01-10
Hi all! I am just beginner with Java So I have problem
> init:
deps-jar:
compile-single:
run-single:
ClassNotFoundException: org.apache.derby.jdbc.ClientDriver
SQLException: No suitable driver found for jdbc:derby://Localhost:1527/sample
BUILD SUCCESSFUL (total time: 0 seconds)


I tried next sample code

> 
import java.sql.*;

public class CreateCoffees {
   
    public static void main(String args[]) {
       
        // Define the url for the sample database
        String url = "jdbc:derby://localhost:1527/sample";
        Connection con;
        String createString;
        createString = "create table COFFEES " +
                "(COF_NAME varchar(32), " +
                "SUP_ID int, " +
                "PRICE float, " +
                "SALES int, " +
                "TOTAL int)";
        Statement stmt;
       
        try {
            // Load database driver. This is old method of loading
            // database driver.
            Class.forName("org.apache.derby.jdbc.ClientDriver");
           
        } catch(java.lang.ClassNotFoundException e) {
            System.err.print("ClassNotFoundException: ");
            System.err.println(e.getMessage());
        }
       
        try {
            // Create database connection
            con = DriverManager.getConnection(url,
                    "app", "app");
           
            // Create a statement and execute it
            stmt = con.createStatement();
            stmt.executeUpdate(createString);
           
            // If there is no exception, the COFFEES table must be successfully created
            System.out.println("COFFEES table is successfully created");

            // Close statement and connection
            stmt.close();
            con.close();
           
        } catch(SQLException ex) {
            System.err.println("SQLException: " + ex.getMessage());
        }
    }
}


What should I do?

---

### Post by Blutack on 2008-01-10
Sorry, I'm afraid what you are asking is probably above the level of this forum!

---

### Post by Mr Fredrick on 2008-01-10
Have you checked that *derby.jar* in your classpath?

You may be better off asking this question on the Derby community mailing list, they are very helpful and responsive.

Check this website:

[http://db.apache.org/derby/](http://db.apache.org/derby/)

---

### Post by Elegorod on 2008-01-11
Did you add a jar file with database driver to Library list?

---

