---
title: "Eclipse JDK Docs and other problem."
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by ViGiLnT on 2007-04-19
Hi everyone.

I've just finished installing Feisty Fawn.

I've got 2 problems:

1st - I'm using java 6 jre and jdk and even though I downloaded the java docs, eclipse IDE is not displaying the javadoc from the classes and methods from sun on my source files.

2nd - This one is minor, I don't want to mount the windows partition, and even though it is not on /etc/fstab , it is showing on nautilus, on the list where by default go the mounted devices on /media. It is not mounted, but I can do it right clicking on it. I don't know how to get rid of that on nautilus.

Great release. Hope to see someone helping me.

**EDIT**: I've solved the eclipse problem by manually entering "file:/usr/share/doc/sun-java6-doc/html/api/" on each on of the system libs that are on the "installed JREs" on preferences dialog.
If someone as a simpler solution post it please.
I remember that on edgy this was already done by default if we had the sun-5-java-jdk installed.

---

### Post by diafanos on 2007-04-24
ViGiLnT,
Eclipse does not use javadoc to display javadoc :roll: 
It uses the source files themselves.

So the only thing you have got to do is to install src.zip (sudo apt-get install sun-java6-src) or if you have 
another java version you can download src.zip from java.sun.com and put it in your jdkX folder.

---

