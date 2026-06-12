---
title: "Sun Java JDK &amp; DrJava"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by rick_oen on 2006-10-11
Hi,

I'm trying to use DrJava with the Sun JDK, I've installed this using the instructions on this page:
[https://help.ubuntu.com/community/Java?highlight=%28java%29]("https://help.ubuntu.com/community/Java?highlight=%28java%29")

When I run DrJava I get the following message:

"DrJava cannot find a 'tools.jar' file for the version of Java that is being used to run DrJava (Java version 1.5.0_06).
Would you like to specify the location of the requisite 'tools.jar' file?
If you say 'No', DrJava might be unable to compile or debug Java programs."

I cannot find the file 'tools.jar', and I can't compile anything without it...

Does anyone have any ideas?

Thanks in advance :-D

---

### Post by ergosteur on 2006-10-27
hello rick_oen, 
if you have the java jdk installed, you just have to specify the location of the tools.jar

mine is:
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/lib/tools.jar

you could do a
sudo updatedb
locate tools.jar

if you can't find it. hope this helps

---

### Post by wasd on 2006-10-29
It sounds like you don't have the jdk installed.  You can do this:

sudo apt-get install sun-java5-jdk

that should install the jdk.  Then, when it prompts you for the jdk location:

/usr/lib/jvm/java-1.5.0-sun-1.5.0.08/lib/tools.jar(Your java version may be different)

Good Luck!:)

---

