---
title: "java on 7.10"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by lstrgrrl on 2008-04-01
ok i am trying to run frostwire and in terminal i type frostwire to get this message:

Starting FrostWire...
Java exec not found in PATH, starting auto-search...
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
 


i have run ubuntu 7.10 before so i went into the synaptic package manager and it says everything is installed including:

libjaxp 1.3-java   1.3.03-5
frostwire 
libservlet 2.4-java    5.0.30-6ubuntu1


what do i do from here i am so confused about what is going on

---

### Post by RealPSL on 2008-04-01
Can we see the output of "which java" from the command line? My suspicion is that you are missing the /usr/bin/java file which is in the "Sun Java 5.0 Runtime" package. It is easier to install this from the Add/Remove Programs. Just select Internet on the left to find it.

---

### Post by lstrgrrl on 2008-04-02
thank you for trying but i figured out the problem, in order to put ubuntu over open bsd i had to destroy the directories on bsd and install ubuntu as an oem. That made ubuntu believe that all my extra repositories were to come from the cd not the internet, now i have unlocked everything and all is running well!

---

