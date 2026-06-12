---
title: "BlueJ want to know where JDK is installed?"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by ejldk on 2007-09-26
Hi,
I want to install BlueJ ([www.bluej.org](www.bluej.org)), but when I launch the .jar file, it asks for the directory of Java (JDK) with a subdirectory called lib with a file called tools.jar in it.
I have tried to find it on my pc, but i cant. 
Can anyone help me?
I think i have installed Java on my computer, with some automatic program from Java.com
Can anyone help me get BlueJ to install?
Thanks?

(Sorry for my bad English)

---

### Post by Majorix on 2007-09-26
An idea is to find that program you installed from, and if its extracted, see where it extracts.

---

### Post by tang0delta on 2008-05-13
Your JDK is usually installed somewhere in your /usr/lib/ directory perhaps under a sub directory called java,j2se, jvm or something like that. I think the java installer from the sun website will install all the Java files in whatever directory the installer is run from. If you really can't find it, it might be easier to create a new Java folder in /usr/lib/ and re-install the jdk there. You'd be best to remove the old one first though.

---

### Post by sunstriker on 2008-05-13
It should be installed on your system. Did you look in /usr/share.
I'm booting my ubuntu right now... I tell you if I find it

edit: I didn't have java installed yet. You should use apt-get though instead of the installer from java itself. It's easier to update and integrates better in Ubuntu i think.
I used ```
sudo apt-get install sun-java6-jdk
```

---

### Post by lswest on 2008-05-13
if you installed sun-java6, it should be under /usr/lib/jvm/java-1.6.0.3.6 or w/e the version number is now :P  I'd tell you for sure, but i'm not at my linux box atm.

---

### Post by sunstriker on 2008-05-13
I just checked it. It is indeed in /usr/lib/jvm/java6-sun-1.6...
I had to point intelliJ (another java ide) to it. It was kinda trial n error ^^ Try home and bin folders first...

---

