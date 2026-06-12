---
title: "Giving eclipse access to servlet api's via $CLASSPATH"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by bcs on 2007-01-24
Hello,
I want to give eclipse access to ```
/usr/local/tomcat/common/lib/servlet-api.jar
/usr/local/tomcat/common/lib/jsp-api.jar
```  So, I went into ```
~/.bashrc
``` and added this ```
export CLASSPATH=.:/home/brian/Documents/:/usr/local/tomcat/common/lib/jsp-api.jar:/usr/local/tomcat/common/lib/servlet-api.jar

```
When i go to compile servlets in eclipse, the necessary api's aren;t recogized.  As a side, I can compile with these api's using javac via terminal, so it's an issue with how eclipse is referencing them.  Thanks for the help!!!

---

### Post by phossal on 2007-02-21
A much, much simpler way to accomplish making the "extras" available for eclipse is to put the .jar files in your JRE/lib/ext folder. If your Java is in /usr/lib/Java6 for example (your isn't, but mine is), then you put the servlet-api.jar in /usr/lib/Java6/jre/lib/ext. This makes the extensions available to the JVM and thus eclipse. 

This isn't always a good technique, because some extensions are needed on the *client* computer. But, for the jar files in question, they only need to be on the development machine, and on the actual server.

---

### Post by bcs on 2007-02-21
Thanks phossal,
I ended up just chaning the build path for the project to include the necessary jar's.  I'll check out your method next time around.  Thanks!

---

