---
title: "HOWTO: JDBC and MySQL on 5.10"
date: 2006-01-28
forum: Absolute Beginner Talk
---

### Post by paulr on 2006-01-28
(1) Install mysql client, server and the jdbc connector. This seemed to be a bit erratic, bits not being installed. Probably me and I couldn't go back to check it !

> sudo apt-get install mysql-server 
> sudo apt-get install mysql-client
> sudo apt-get install libmysql-java 

You can select "No configuration" for postfix if it is installed unless you want to use it.

(2) Set up the password for the root user as 'root' or whatever you want.

> mysqladmin -u root password root 

(3) Check you can connect to mysql

> mysql -u root -p

then enter the password you just set and press return again. In this case it would be "root".

(4) Create databases and tables or whatever, so you have some data to work with. You can disconnect and use mysql-query-browser for this if you wish.

(5) Create a user with access to that table. Replace the bits in square brackets by the table name, and the chosen user and password. Don't type in the square brackets !

> grant all privileges on [table].* to [user]@localhost identified by "[password]";
> flush privileges;

(This is the only change from the original ; 5.10 requires [user]@localhost rather than [user]@localhost.localdomain)

This is required because when you connect using "mysql -u root -p" it connects directly to the Sql Server. The "grant" line creates access via 127.0.0.1 (localhost.localdomain).

You can test this by

> mysql -u [user] -h 127.0.0.1 -p

This will work only for the user you have just "granted", not for root. Counter-intuitively, the 'default' server and localhost/127.0.0.1 aren't the same thing :)

(6) Add these two lines to /home/[user]/.bashrc. I am running Java 5 which doesn't require the current directory to be on the Classpath ; I *think* Java 2 does, but I'm not going back to check it :) In that case you may need to have $CLASSPATH:.:/user/share/java/mysql.jar

	CLASSPATH=$CLASSPATH:/usr/share/java/mysql.jar
	export CLASSPATH

Log out and Log in again. Start up a terminal and type

> echo $CLASSPATH

It should print out something like ":/usr/share/java/mysql.jar"

It should now work. Except for Prepared statements, which don't work in this version of MySQL, apparently ! Here is some typical code (clearing up removed for simplicity)import java.sql.*;
import java.util.Properties;

public class DBDemo
{
        // The JDBC Connector Class.
	private static final String dbClassName = "com.mysql.jdbc.Driver";

        // Connection string. emotherearth is the database the program
        // is connecting to. You can include user and password after this 
        // by adding (say) ?user=paulr&password=paulr. Not recommended!

	private static final String CONNECTION = 
                                              "jdbc:mysql://127.0.0.1/emotherearth";
		
	public static void main(String[] args) throws 
                                                            ClassNotFoundException,SQLException
	{
		System.out.println(dbClassName);
                // Class.forName(xxx) loads the jdbc classes and
                // creates a drivermanager class factory
		Class.forName(dbClassName);   

                // Properties for user and password				
		Properties p = new Properties();
		p.put("user","paulr");
		p.put("password","paulr");		

		// Now try to connect
		Connection c = DriverManager.getConnection(CONNECTION,p);

                System.out.println("It works !");
                c.close();		
	}
}

---

### Post by brady on 2006-04-24
This gave me the information I needed to use OpenOffice's Base tool as a frontend for MySQL to do some rails development.

---

### Post by kanna1620 on 2007-05-29
> **paulr said:**
> (1) Install mysql client, server and the jdbc connector. This seemed to 
It should now work. Except for Prepared statements, which don't work in this version of MySQL, apparently ! Here is some typical code (clearing up removed for simplicity)import java.sql.*;
import java.util.Properties;

public class DBDemo
{

	}
}

I did what you said but the connection is not established. What to do? 
Edit: I am using Ubuntu 7.04

---

### Post by kanna1620 on 2007-05-29
> **paulr said:**
> (1) Install mysql client, server and the jdbc connector. This seemed to 
It should now work. Except for Prepared statements, which don't work in this version of MySQL, apparently ! Here is some typical code (clearing up removed for simplicity)import java.sql.*;
import java.util.Properties;

public class DBDemo
{

	}
}

I did what you said but the connection is not established. What to do? I am using Ubuntu 7.04 now.
Sorry I posted again.

I got these errors:
com.mysql.jdbc.Driver
Exception in thread "main" java.lang.ClassNotFoundException: com.mysql.jdbc.Driver not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:./,file:/usr/share/java/], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.70)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at java.lang.Class.forName(libgcj.so.70)
   at java.lang.Class.forName(libgcj.so.70)
   at DBconnect.main(DBconnect.java:20)

---

### Post by apetresc on 2007-08-15
If you would also like to have the API documentation for libmysql-java (this is useful if you're using an IDE like NetBeans or Eclipse), you should follow the instructions here to build them yourself (they don't exist "pre-compiled" anywhere online that I've been able to find): [http://www.blog.komrades.org/?p=24](http://www.blog.komrades.org/?p=24)

---

### Post by stevoo on 2007-09-19
well your problem is exactly what i had .... you need to find mysql.jar and place in into /usr/share/java
It will not let you drag and drop so simply use your terminal with this command
sudo cp *where you havethe file*/mysql.jar /usr/share/java/


then youll have to link that using Netbeans, meaning on the right side where your Files are , right click on it and select properties, then add the jar file that you have in there in order for netbeans to use it

if you still have problems post again !

---

### Post by PaulHuffman on 2007-10-15
I don't understand what you mean by that typical code.  Does it start with the line import java.sql;?  Or the next line?  Does this code, once I make the substitutions for my connect, go into /usr/share/java?  What do I name it?  How do I refer to it in OO connect dialog?

No, I was making this too complicated.  I had already installed the libmysql-java.  All I had to do was in [http://ubuntuforums.org/showthread.php?t=502412&highlight=JDBC+mySQL+Openoffice]("http://ubuntuforums.org/showthread.php?t=502412&highlight=JDBC+mySQL+Openoffice")

---

### Post by tungv0 on 2008-03-27
I am currently doing a project for my final year and it involve with JDBC. Thanks to this topic, I have get JDBC work with MYSQL on my server. However, I have one question, hope you guys can help me. I realise that in this topic, you use localhost for the connection. I know twe can also connect to the mysql database remotely and I have tried to replace the localhost with my server name but it does not work. Anyone know how can I do this

---

