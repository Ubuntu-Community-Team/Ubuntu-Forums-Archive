---
title: "Frostwire Startup Java Problem"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by Blanch on 2006-11-04
I am having problems starting up Frostwire on Ubuntu "6.10".  Apparently all i need is the latest version of java "1.4". i got version 1.4 rite now. when ever i install version 1.5 it wont intall. i still got 1.4, i know im doing it correctly. What is wrong?

---

### Post by Sef on 2006-11-04
To install Sun Java 1.5.0.08: 

Applications > Add/Remove  

In the search box type in "Sun Java" (without the quotes.)

Then click "Sun Java 5.0 Plugin" and "Sun Java 5.0 Runtime" and unclick "Java Webstart 1.4".  

Next click apply and follow the directions.  You will need to click apply twice more, I believe.

---

### Post by mia1dolfan on 2006-11-04
This is what worked for me running Dapper, there are other work arounds flying around the forums.  This is simple one line.

sudo ln -s /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/ /opt/jre

Make sure your running Sun Java located in the multiverse repository, I installed Sun Java by using  [automatix]("http://www.getautomatix.com/").  If you are running a different version of Sun Java make sure you change the path of ln (link) command above to your version.

---

### Post by mia1dolfan on 2006-11-04
This appears to be the more appropiate way of doing things, both work.

sudo update-alternatives --config java

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.1
 +*   2        /usr/lib/jvm/java-gcj/jre/bin/java
      3        /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

Make sure you select the Sun version of JRE (3) in my case.

---

### Post by Blanch on 2006-11-04
Alright i got the latest version but frostwire still wont start up on ubuntu 6.10

---

### Post by mia1dolfan on 2006-11-04
I had another issue, it didn't work correctly on my system with Sun Java sun-java5-jre.  Once I specified the Sun Java version using the 'update-alternatives --config java' command, it would start up, but would freeze, never displaying the main screen.  I had to install the package j2re1.4, Blackdown Java in the multiverse repositories and then run 'update-alternatives --config java' and then select the j2se Blackdown version.

---

