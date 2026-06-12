---
title: "Ubuntu, java mysql not connecting"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by brunoskrebs on 2007-12-04
Hi,

I don't really know if the problem is a linux configuration, a java configuration a mysql configuration, or all together lol...

But anyway I hope someone can help me. I am trying to connect java to mysql server but it is hard. It keeps throwing this exception: ```
java.lang.ClassNotFoundException: com.mysql.jdbc.Driver
```

This is my code (actually I'm not trying to connect yet, just to load this class):
```
public class Main {
	public static void main(String[] args) {
		try {
			// The newInstance() call is a work around for some
			// broken Java implementations

			Class.forName("com.mysql.jdbc.Driver").newInstance();
		} catch (Exception ex) {
			System.out.println(ex.toString());
		}
	}
}
```

I installed libmysql, I tried to set CLASSPATH, I tried to expo CLASSPATH, I tried a lot of stuff actually, but always the same excpetion.

Can someone help me???

Thanks
Bruno

---

### Post by PeterJS on 2007-12-04
You need the Mysql JDBC (Java DataBase Connection) library which can be downloaded from here:
[http://www.mysql.com/products/connector/j/](http://www.mysql.com/products/connector/j/)
And might be in the sun-java6-javadb package, but don't hold me to that, I haven't used JDBC in Ubuntu, only Red Hat.

---

### Post by brunoskrebs on 2007-12-05
Yeah I downloaded this library already, but after that I don't know what to do, it keeps saying that it does not find the class. This is what I was talking about when I said that I tried to add CLASSPATH but without a success...

---

### Post by PeterJS on 2007-12-05
When I used JDBC, I never got it installed "properly" as I didn't have administrative access on the machine. What I ended up doing was just sticking the J Connect source in my project. This solution won't work for precompiled programs but it looks like you're building your own, so it might work. It's terribly inefficient if you're going to have multiple apps using JDBC, but for just one there's no extra overhead.

---

### Post by The Cog on 2007-12-05
I use the jdbc driver regularly. I have always "installed" it by putting the jar file (mysql-connector-java-5.0.7-bin.jar I'm using right now) in the jre/lib/ext directory of the java installation. The command
**locate jre/lib/ext**
will find where this directory is for you

---

### Post by JacksonDane on 2007-12-15
> **The Cog said:**
> I use the jdbc driver regularly. I have always "installed" it by putting the jar file (mysql-connector-java-5.0.7-bin.jar I'm using right now) in the jre/lib/ext directory of the java installation. The command
**locate jre/lib/ext**
will find where this directory is for you

Thank you! Worked perfectly!

---

