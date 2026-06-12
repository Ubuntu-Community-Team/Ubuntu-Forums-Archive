---
title: "Updating Java"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by divisortheory on 2007-06-03
I'm trying to install a new version of the Java JRE from sun's website.  Iran the test applet on their website and it said I was using version 1.4.something.  So Idownloaded 1.6.something and followed the directions.  Basically just get a root terminal, change the permissions on a file to make it executable, then run the file.  But after I do that the test applet still tells me I'm using the old version.  Plus, when I followed the directions, it never appeared to "configure" anything.  All it did was unpack some files, according to the output anyway.

Is there a way to check what version I have installed?  When I type "java" from a console it seemed to execute the java from the gcc package, which is specifically what I'm trying to get rid of.

---

### Post by taurus on 2007-06-03
Which release are you running right now?  If you are using Feisty, just open a terminal and run

```
sudo aptitude update
sudo aptitude install sun-java6-jre sun-java6-plugin sun-java6-fonts
java -version
```

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by machoo02 on 2007-06-03
Open up a terminal, and enter in```
sudo update-alternatives --config java
```You should be given a choice about which version of java you would like from the versions that you have installed on your baby.

---

### Post by divisortheory on 2007-06-03
> **taurus said:**
> Which release are you running right now?  If you are using Feisty, just open a terminal and run

```
sudo aptitude update
sudo aptitude install sun-java6-jre sun-java6-plugin sun-java6-fonts
java -version
```

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

I'm running x64 Feisty right now.

I did what you suggested and it appeared to install java6.  Even the package manager tells me I have Java Runtime 6 installed.  However, when typing java -version, I get:

java version "1.4.2"
gij (GNU libgcj) version 4.1.2 (Ubuntu 4.1.2-0ubuntu5)

which definitely isn't 6.  Also, Iwant to completely eliminate gij, which is the gnu version of java.  I want to go entirely with the one from sun.



Edit: I tried the other suggestion involving sudo update-alternatives, and that allowed me to change my default java install, and now java -version reports the newest one.  However, eclipse still wants to use gij (my ultimate goal is to get eclipse using 1.6).  I guess this is no longer a Linux issue though, so I can keep playing with it on my own now and go to the eclipse forums if I have other questions.

Thanks!

---

