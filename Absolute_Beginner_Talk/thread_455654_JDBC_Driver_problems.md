---
title: "JDBC Driver problems"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by dantastik on 2007-05-26
Hi guys, I am working on this project for uni, just started it...

So, I got MySQL working, i can launch the manager from the command line window and all that. I created a database, which I am now trying to access with a java application.

When I run it I get this exception message:

> 
](*,)
sqlexceptionjava.sql.SQLException: No suitable driver
](*,)


Here's the code:

> 

import java.sql.*;

public class SimpleJDBC
{
   public static void main(String args[])
   {
      Connection conn;
      Statement stmt;
      try
      {
         Class.forName("com.mysql.jdbc.Driver").newInstance();
      }
      catch (Exception ex){}
      try
      {
/*       conn = DriverManager.getConnection("jdbc:mysql://
         localhost:3306timebay_db?user=dan&password=timebay");*/

/*       conn = DriverManager.getConnection("jdbc:mysql://localhost/
         timebay_db?user=dan&password=timebay") */

         conn = DriverManager.getConnection("jdbc:mysql://127.0.0.1:3306/
         timebay_db?user=dan&password=timebay" );
         stmt = conn.createStatement();
      }
      catch (SQLException sqle)
      {
         System.out.println("sqlexception" + sqle);
      }
   }
}




The post here [http://ubuntuforums.org/showthread.php?t=283080&highlight=JDBC+Driver+problems]("http://ubuntuforums.org/showthread.php?t=283080&highlight=JDBC+Driver+problems") is probably the solution.

But when I try

> -cp ./mysql-connector-java-5.0.4-bin.jar:$CLASSPATH

I get this error message here:

> bash: -cp: command not found

What's the magic pill to make that nasty error message go away?


Cheers, Dan

---

### Post by DSn0wMan on 2007-05-26
It looks to me like "-cp ./mysql-connector-java-5.0.4-bin.jar:$CLASSPATH" is a java command, and not a bash command.

try something like this

```
java -cp ./mysql-connector-java-5.0.4-bin.jar:$CLASSPATH
```

Of course for this command to be successfull you have to give it the proper path to your "mysql-connector-java-5.0.4-bin.jar" file.

---

### Post by dantastik on 2007-05-26
Ok, it didn't work,-thx so much anyway!- but I just thought of this, which could be the origin of the problem...

if I launch that basic application from eclipse, the IDE, at least it tries to do something.
If I launch it from the command line I get this error:

> 
Exception in thread "main" java.lang.NoClassDefFoundError: SimpleJDBC/class


I vaguely remember hearing something like having to add the java and javac something to the path.
I roughly know what that meant, but no idea of how to put that in practice...

---

### Post by dantastik on 2007-05-26
Ok, I just thought of this, which could be the origin of the problem...

if I launch that basic application from eclipse, the IDE, at least it tries to do something.
If I launch it from the command line I get this error:

> 
Exception in thread "main" java.lang.NoClassDefFoundError: SimpleJDBC/class


I vaguely remember hearing something like having to add the java and javac something to the path.
I roughly know what that meant, but no idea of how to put that in practice...

---

### Post by dantastik on 2007-05-26
I managed to make java apps work from the command line, but I still get the sqlerror message...

---

### Post by DSn0wMan on 2007-05-26
At least you got past the no driver error. It still seems like it is not finding all the java classes it needs. Wich version of java do you have installed?

```
java -version
```

---

### Post by DSn0wMan on 2007-05-26
I also found a post that might be helpful.

[http://ubuntuforums.org/showthread.php?t=409640](http://ubuntuforums.org/showthread.php?t=409640)

---

### Post by dantastik on 2007-05-27
Java version is 

> 
java version "1.5.0_08"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_08-b03)
Java HotSpot(TM) Client VM (build 1.5.0_08-b03, mixed mode, sharing)


None of the solutions helped, I think the best thing to do is to get my teacher to do that and then post the solution on here :)

Thx for your patience anyway mr :)

dx

---

### Post by dantastik on 2007-05-28
**HERE'S THE SOLUTION!!!**


I thought I looked well, but I make mistakes too, especially at 3 or so a.m. Apologies!

This post sorted it.

[http://ubuntuforums.org/showthread.php?t=122771&highlight=jdbc+HOWTO](http://ubuntuforums.org/showthread.php?t=122771&highlight=jdbc+HOWTO)

Sorry for having wasted your time...

---

