---
title: "Java is configured, but I can't configure Tomcat"
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by MarcioBarroso on 2006-07-16
Hi,

     That's what I did:
Downloaded and uncompressed Java and Tomcat files(tomcat file is apache-tomcat-5.5.17.tar.gz)

in a file called .bashrc I inserted the lines:

JAVA_HOME=/home/marcio/java
CATALINA_HOME=/home/marcio/tomcat
CLASSPATH=$CATALINA_HOME/common/lib/servlet-api.jar:.:$CLASSPATH
CLASSPATH=$CATALINA_HOME/common/lib/jsp-api.jar:$CLASSPATH
PATH=$JAVA_HOME/bin:$PATH

# Sintaxe Bourne shell (sh), Korn shell (ksh), Bash e similares:
export JAVA_HOME CATALINA_HOME CLASSPATH PATH

After rebooting, I was able to compile and run java programs. The next step was to start Tomcat. So, I executed the startup.sh file and typed [http://localhost:8080](http://localhost:8080) on web browser. I get a message saying "localhost" can't be recognized ou cannot be reached. What should I do ?
Thanks in advance.

---

### Post by timetunnel on 2006-07-16
The error message seems a hint to the fact that tomcat hasn't started properly. In a shell, what is the output of "startup.sh"? What does 
```
pstree -a | grep catalina
```
print?

---

### Post by timetunnel on 2006-07-16
Oops, that should rather read:
```
ps -efww | grep tomcat
```
What's the output after you've run "startup.sh"?

---

### Post by MarcioBarroso on 2006-07-16
when I type this: 
 ps -efww | grep tomcat

 I get this:
 marcio    8814  8792  0 14:42 pts/0    00:00:00 grep tomcat

 By the way, the only file in the logs directory is the cataline.out, which contents:

 /home/marcio/tomcat/bin/catalina.sh: line 258: /usr/local/java/bin/java: No such file or directory
/home/marcio/tomcat/bin/catalina.sh: line 258: /usr/local/java/bin/java: No such file or directory

 Thanks

---

### Post by timetunnel on 2006-07-16
> **MarcioBarroso said:**
> when I type this: 
 ps -efww | grep tomcat

 I get this:
 marcio    8814  8792  0 14:42 pts/0    00:00:00 grep tomcat

That means that tomcat isn't running. So, something with the java paths must be wrong. The output, when running "startup.sh" from the command line, should look like this (paths here from my system, of course):
```
Using CATALINA_BASE:   /opt/tomcat
Using CATALINA_HOME:   /opt/tomcat
Using CATALINA_TMPDIR: /opt/tomcat/temp
Using JRE_HOME:       /usr/lib/jvm/java-1.5.0-sun
```

```
/home/marcio/tomcat/bin/catalina.sh: line 258: /usr/local/java/bin/java: No such file or directory

```
Well, obviously the path you set up with JAVA_HOME=/home/marcio/java isn't recognized, because it's looking in /usr/local/java for the java runtime. I have no idea what the scope of variables that where set in .bashrc is. What I did on my system to make it run is adding a line to startup.sh and shutdown.sh as the first line after the initial comments:
```
export JAVA_HOME="/usr/lib/jvm/java-1.5.0-sun"
```

You can try it with your path:
```
export JAVA_HOME="/home/marcio/java"
```

If that doesn't help you should consider installing Sun's java package from the Dapper repositories instead of having it in your home folder. 

BTW: If you're using Eclipse, there's a good Tomcat plugin by Sysdeo, which makes starting/stopping the server very easy:
[http://www.sysdeo.com/eclipse/tomcatplugin](http://www.sysdeo.com/eclipse/tomcatplugin)

---

