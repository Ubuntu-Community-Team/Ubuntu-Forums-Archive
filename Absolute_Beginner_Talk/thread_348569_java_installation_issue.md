---
title: "java installation issue"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by e^(i*pi) on 2007-01-29
I am having some real issues installing java6.  I enabled my universe and multiverse repos, and then I downloaded and installed the java6 jre, jdk, and plugin with synaptic. but when I check my java version it still tells me 1.4.2. Any thoughts?

---

### Post by morfeibg on 2007-01-29
Hello,

Most likely you see the old version because it is set in the PATH and the JAVA_HOME environment. Check the output of the commands:
>echo $PATH
>echo $JAVA_HOME

The result should point to your new jdk directory.

---

### Post by r4ik on 2007-01-29
sudo apt-get install sun-java5-jre sun-java5-plugin

When asked, agree with DLJ license terms. 

To configure J2SE as the default JVM (necessary for programs such as Frostwire, Freenet, RSSOwl and as a plugin for Mozilla Firefox): 

sudo update-alternatives --config java

From,

[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

Good luck !

---

### Post by jvc26 on 2007-01-29
I hadnt realised JDK6 was available via the repos! I compiled it from the fiesty source and then installed via dpkg -r. There is a post up here on how to do it I'm really sorry but have subsequently lost the link.
Il

---

### Post by phossal on 2007-01-29
My sig contains a link to a Java, eclipse, and Tomcat install tutorial. It shows how you can get the JDK right from SUN, rather than waiting for packages or building your own.

---

