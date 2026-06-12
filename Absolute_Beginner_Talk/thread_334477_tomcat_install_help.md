---
title: "tomcat install help"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by bcs on 2007-01-09
Hello,

I've been using [this HOWTO]("http://www.ubuntuforums.com/showthread.php?t=44006&highlight=%2Fusr%2Flocal%2Ftomcat%2Fbin%2Fcatalina.sh%3A+line+258%3A+%2Fusr%2Flib%2Fj2sdk1.5-sun%2F%2Fbin%2Fjava%3A+No+such+file+OR+directory") to install tomcat...I believe it has installed fine because when I run ```
sh /usr/local/tomcat/bin/startup.sh

```

I get 
```
Using CATALINA_BASE:   /usr/local/tomcat
Using CATALINA_HOME:   /usr/local/tomcat
Using CATALINA_TMPDIR: /usr/local/tomcat/temp
Using JRE_HOME:       /usr/lib/j2sdk1.5-sun/

```

...but pointing browser to localhost get me "connection was refused" (I changed the port to 80...but checked ports 8080 and 8180 too just to be safe).

/usr/local/tomcat/logs/catalina.out has the same line repeated over and over:

/usr/local/tomcat/bin/catalina.sh: line 258: /usr/lib/j2sdk1.5-sun//bin/java: No such file or directory

So I'm guessing that my issue is that tomcat can't locate java5...I installed java some time ago, so not sure where it is located...can anyone help me (a) finding where I have java installed and (b) how to point tomcat to it?? Thanks a lot

---

### Post by bcs on 2007-01-09
I also just checked ```
echo $JAVA_HOME
``` and got ```
/usr/lib/j2sdk1.5-sun/

```...but there doesn;t seem to be anything in that path...

One other thing: from my previous post, I just noticed that "/usr/local/tomcat/bin/catalina.sh: line 258: /usr/lib/j2sdk1.5-sun//bin/java: No such file or directory" seems to have a syntax error:  /usr/lib/j2sdk1.5-sun//bin/java....there is a double forward slash before "bin"...

---

### Post by bcs on 2007-01-10
OK, I think I've figured out the problem, but still don;t know how to fix it...tomcat is using 
/usr/lib/j2sdk1.5-sun/ as JRE_HOME and nothing exists in that path...so  I just need to point tomcat to a new JRE_HOME.  Can anyone tell me how to do that?  Also, can someone tell me how to find the JRE in my system?? (I believe I installed JRE using apt-get, so it should be in default location).  Thanks!

---

### Post by bcs on 2007-01-10
OK...I figured out that I change JRE_HOME in ~/.bashrc...and I am assuming that it needs to point to the executable called "java".  In my system, that is located at /usr/lib/jvm/java-1.5.0-sun/jre/bin/java...but when I change ~/.bashrc to:

```

#Stuff we added to make tomcat go 
export JAVA_HOME=/usr/lib/jvm/java-1.5.0-sun/bin 
export CLASSPATH=/usr/local/tomcat/common/lib/jsp-api.jar:/usr/local/tomcat/common/lib/servlet-api.jar

```

I get this in catalina.out:
```

/usr/local/tomcat/bin/catalina.sh: line 258: /usr/lib/jvm/java-1.5.0-sun/bin/bin/java: No such file or directory

```

when that didnt work, I tried to change JAVA_HOME to /usr/lib/jvm/java-1.5.0-sun/ and got this in catalina.out:

```
Jan 10, 2007 3:35:33 PM org.apache.catalina.core.AprLifecycleListener lifecycleEvent
INFO: The Apache Tomcat Native library which allows optimal performance in production environments was not found on the java.library.path: /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/client:/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386:/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/../lib/i386
Jan 10, 2007 3:35:33 PM org.apache.coyote.http11.Http11BaseProtocol init
SEVERE: Error initializing endpoint
java.net.BindException: Permission denied:80
	at org.apache.tomcat.util.net.PoolTcpEndpoint.initEndpoint(PoolTcpEndpoint.java:297)
	at org.apache.coyote.http11.Http11BaseProtocol.init(Http11BaseProtocol.java:138)
	at org.apache.catalina.connector.Connector.initialize(Connector.java:1016)
	at org.apache.catalina.core.StandardService.initialize(StandardService.java:580)
	at org.apache.catalina.core.StandardServer.initialize(StandardServer.java:791)
	at org.apache.catalina.startup.Catalina.load(Catalina.java:503)
	at org.apache.catalina.startup.Catalina.load(Catalina.java:523)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:585)
	at org.apache.catalina.startup.Bootstrap.load(Bootstrap.java:266)
	at org.apache.catalina.startup.Bootstrap.main(Bootstrap.java:431)
Jan 10, 2007 3:35:33 PM org.apache.catalina.startup.Catalina load
SEVERE: Catalina.start
LifecycleException:  Protocol handler initialization failed: java.net.BindException: Permission denied:80
	at org.apache.catalina.connector.Connector.initialize(Connector.java:1018)
	at org.apache.catalina.core.StandardService.initialize(StandardService.java:580)
	at org.apache.catalina.core.StandardServer.initialize(StandardServer.java:791)
	at org.apache.catalina.startup.Catalina.load(Catalina.java:503)
	at org.apache.catalina.startup.Catalina.load(Catalina.java:523)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:585)
	at org.apache.catalina.startup.Bootstrap.load(Bootstrap.java:266)
	at org.apache.catalina.startup.Bootstrap.main(Bootstrap.java:431)
Jan 10, 2007 3:35:33 PM org.apache.catalina.startup.Catalina load
INFO: Initialization processed in 1163 ms
Jan 10, 2007 3:35:33 PM org.apache.catalina.core.StandardService start
INFO: Starting service Catalina
Jan 10, 2007 3:35:33 PM org.apache.catalina.core.StandardEngine start
INFO: Starting Servlet Engine: Apache Tomcat/5.5.20
Jan 10, 2007 3:35:34 PM org.apache.catalina.core.StandardHost start
INFO: XML validation disabled
Jan 10, 2007 3:35:35 PM org.apache.coyote.http11.Http11BaseProtocol start
SEVERE: Error starting endpoint
java.net.BindException: Permission denied:80
	at org.apache.tomcat.util.net.PoolTcpEndpoint.initEndpoint(PoolTcpEndpoint.java:297)
	at org.apache.tomcat.util.net.PoolTcpEndpoint.startEndpoint(PoolTcpEndpoint.java:312)
	at org.apache.coyote.http11.Http11BaseProtocol.start(Http11BaseProtocol.java:150)
	at org.apache.coyote.http11.Http11Protocol.start(Http11Protocol.java:75)
	at org.apache.catalina.connector.Connector.start(Connector.java:1089)
	at org.apache.catalina.core.StandardService.start(StandardService.java:459)
	at org.apache.catalina.core.StandardServer.start(StandardServer.java:709)
	at org.apache.catalina.startup.Catalina.start(Catalina.java:551)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:585)
	at org.apache.catalina.startup.Bootstrap.start(Bootstrap.java:294)
	at org.apache.catalina.startup.Bootstrap.main(Bootstrap.java:432)
Jan 10, 2007 3:35:35 PM org.apache.catalina.startup.Catalina start
SEVERE: Catalina.start: 
LifecycleException:  service.getName(): "Catalina";  Protocol handler start failed: java.net.BindException: Permission denied:80
	at org.apache.catalina.connector.Connector.start(Connector.java:1096)
	at org.apache.catalina.core.StandardService.start(StandardService.java:459)
	at org.apache.catalina.core.StandardServer.start(StandardServer.java:709)
	at org.apache.catalina.startup.Catalina.start(Catalina.java:551)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:585)
	at org.apache.catalina.startup.Bootstrap.start(Bootstrap.java:294)
	at org.apache.catalina.startup.Bootstrap.main(Bootstrap.java:432)
Jan 10, 2007 3:35:35 PM org.apache.catalina.startup.Catalina start
INFO: Server startup in 1789 ms

```


So at this point, I have no idea what to do...if anyone has any idea at all, I'd love to hear it!  Thanks!

---

### Post by phossal on 2007-01-10
I have installed the JDK and Eclipse [this way]("http://ubuntuforums.org/showthread.php?t=332674").

This method makes it possible to simply download Tomcat to your desktop and extract it. 
You probably want this: [apache-tomcat-6.0.7.tar.gz]("http://download.nextag.com/apache/tomcat/tomcat-6/v6.0.7/bin/apache-tomcat-6.0.7.tar.gz")
Make quick edits to server.xml, and, voila, you're up and running.

---

### Post by bcs on 2007-01-10
Thanks for the response, phossal.  The only problem is that I need java5 and tomcat 5.5...

---

### Post by phossal on 2007-01-10
Get them. They're installed the same way. There was no change in the installation procedure (using my method) between JDK5/Tomcat5 and JDK6/Tomcat6. You just need to download the previous version of each. They're still available at their respective sites as shown below:

[JDK 5]("http://java.sun.com/javase/downloads/index_jdk5.jsp")
[Tomcat 5.5]("http://apache.ziply.com/tomcat/tomcat-5/v5.5.20/bin/apache-tomcat-5.5.20.tar.gz")

---

### Post by bcs on 2007-01-10
Thanks phossal, but I just figured it out with my existing configuration.  For anyone experiencing a similar problem, here;s what I did:

As I stated earlier, I used [this thread]("http://www.ubuntuforums.org/showthread.php?p=226828") to setup tomcat (and [this one]("http://ubuntuforums.org/showthread.php?t=201378") previously to setup java5 and eclipse).  The only thing I needed to change from the tomcat HOWTO was this:

I needed to add the following lines to ~/.bashrc (instead of the lines provided in the HOWTO):

```

#Stuff we added to make tomcat go 
export JAVA_HOME=/usr/lib/jvm/java-1.5.0-sun-1.5.0.06 
export CLASSPATH=/usr/local/tomcat/common/lib/jsp-api.jar:/usr/local/tomcat/common/lib/servlet-api.jar

```

then, I needed to comment out the following lines in /usr/local/tomcat/conf/server.xml

```

<Listener className="org.apache.catalina.core.AprLifecycleListener" />

```

(by the way, I figured that out by Googling the error message I found in /usr/local/tomcat/logs/catalina.out...which lead me [here]("http://mail-archives.apache.org/mod_mbox/tomcat-users/200512.mbox/%3C6.2.3.4.1.20051221120332.03c03fd0@pop.knowledgeplatform.com%3E"))

I shutdown and restarted tomcat and tomcat worked.

Hope that saves someone from going through the same pain as me!

---

