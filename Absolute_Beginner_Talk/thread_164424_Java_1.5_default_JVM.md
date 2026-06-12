---
title: "Java 1.5 default JVM"
date: 2006-04-22
forum: Absolute Beginner Talk
---

### Post by Reggaeton King on 2006-04-22
Currently, Java 1.4 Blackdown is my default VM for Java. I downloaded JRE 1.5 and used the "mv" command to place  JRE 1.5 into the same directory as that Java Blackdown. How do you make JRE1.5 my default Java VM?? Can someone help me?

---

### Post by drummer on 2006-04-22
Follow the instructions here to install Sun Java, this way you create a .deb, and so is cleaner.
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by adamkane on 2006-04-22
That would be the way to do it.

Automatix is great, if you never need to uninstall anything.

---

### Post by reubadoob on 2006-04-26
I ran automatix to install Java 1.5 but when I run the command java -version it tells me: 

java version "1.4.2-02"
Java(TM) 2 Runtime Environment, Standard Edition (build Blackdown-1.4.2-02)
Java HotSpot(TM) Client VM (build Blackdown-1.4.2-02, mixed mode)

What's the deal? Why isn't Automatix installing 1.5? I also installed and ran easy Ubuntu in attempt to install the newest java but it failed also. Can anyone help me?!

---

### Post by arnieboy on 2006-04-26
Automatix does install Java 1.5 when u ask it to. However it does not set Java 1.5 as your default JRE environment because more and more softwares are becoming compatible with the open source blackdown version (1.4)
To set version 1.5 as your default do the following:
```
sudo update-alternatives --config java
```
and set whatever number java 1.5 is at.
That will make it default.

---

### Post by reubadoob on 2006-04-26
Okay looks like that worked this is what I got when I used the instructions you gave:
[B]
 sudo update-alternatives --config java
Password:

There are 5 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.0
      2        /usr/lib/jvm/java-gcj/bin/java
*+    3        /usr/lib/j2se/1.4/bin/java
      4        /usr/lib/j2re1.5-sun/bin/java
      5        /usr/lib/j2sdk1.5-sun/bin/java

Press enter to keep the default[*], or type selection number: 4
Using `/usr/lib/j2re1.5-sun/bin/java' to provide `java'.[/B]

I chose #4. Was that the right one? I also noticed that I hae some addiotional ones installed. What do I do about those? Last question: will I have to follow the steps in this forum([http://ubuntuforums.org/showthread.php?t=105818&page=2](http://ubuntuforums.org/showthread.php?t=105818&page=2)) in order to make the Java 2 plugin work?

---

### Post by arnieboy on 2006-04-26
yes 4 is the correct one. dont bother about the others.

---

### Post by reubadoob on 2006-04-27
Thanks arnie! Everything is working fine. Now I just need to work out some mPlayer issuses but that's another thread.

---

### Post by cantormath on 2006-05-01
when I do sudo update-alternatives --config java
I get this:
There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /etc/alternatives/kaffe-system/bin/java
      2        /usr/bin/java-sablevm
      3        /usr/bin/gij-wrapper-4.1
*+    4        /usr/lib/jvm/java-gcj/bin/java

Press enter to keep the default[*], or type selection number:

any help?

---

