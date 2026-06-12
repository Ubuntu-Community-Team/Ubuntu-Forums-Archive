---
title: "How to Install J2EE, Tomcat, &amp; Apache in Ubuntu"
date: 2005-09-13
forum: Absolute Beginner Talk
---

### Post by dollydoll on 2005-09-13
Hi, it's me again!
this time I would like to get the jsp engine Tomcat to work under ubuntu.
I already have Eclipse, and the jdsk from the repositories, what are the next steps?
thx!

---

### Post by brandnewubuntu on 2005-09-14
I am also wondering if anyone else knows how to install j2ee, specifically version 1.4, which is already a .bin file.  I know the previous versions came in a gzip format, but this one is confusing.  On the sun website it says that version 1.4 works on Red Hat linux, but shouldn't it also work on Ubuntu?

As to dollydoll's question about tomcat, I found on another post that you just have use the synaptic package manager and install libapache2_mod_jk2(apache2) or libapache_mod_jk2(apache 1.3.x), but I haven't yet tested it personally..

---

### Post by aysiu on 2005-09-14
Version 1.5.0 is available in the backports.

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
[http://ubuntuguide.org/#jre](http://ubuntuguide.org/#jre)

---

### Post by brandnewubuntu on 2005-09-15
the software I am trying to install says I need to have j2ee 1.4 installed.  Is J2re1.5 the same thing?

---

### Post by phex on 2005-09-24
not exactly. j2re is only the runtimeenvironement. this means you can only start java applications with the java command. but the javac command to compile java files is missing. this you will only get with a j2sdk (standard developement kit). in j2ee you will get the j2sdk and the java enterprise application server bundeled.

at the moment this bundle is j2ee is only available for version 1.4. for the 1.5sdk no such bundle with the application server can be found at the moment. so dont waste your time with searching for j2ee1.5. but i would suggest you, try to download j2sdk1.5 and the jboss as application server. but well, you can also use the original java application server. just simple goole how to install the j2sdk and the jboss and where you can find it. in the ubuntu forum a lot of questions and answers have been given how to install java and where it can be found. jboss can be found here: [http://www.jboss.com/developers/index](http://www.jboss.com/developers/index).

---

### Post by Ziggurat on 2005-09-26
phex is correct. Please do not get confuse.  J2RE or JRE = Java Runtime Environment  (Only for executing java apps, no compiler)   JDK = Java Development Kit  (Compiler and development kit doh ;) )   J2SE = Java Standard Edition  ( The two thing i mentioned before )   J2EE = Java Enterprise Edition  (This is only a specification of an application server, there are a "sample" fully functional implementation of this specs of Sun, but there are better choices as JoNaS or JBoss)

---

