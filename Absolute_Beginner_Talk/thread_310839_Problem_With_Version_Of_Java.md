---
title: "Problem With Version Of Java"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by agonoruci on 2006-12-01
I go to terminal and type in java -version this is what i get:

java version "1.4.2"
gij (GNU libgcj) version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-14ubuntu7)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

I notice that my java versoin in 1.4.2, to get Limewire to get working i need at leats 1.5. So I type sudo apt-get install sun-java5-jre sun-java5-plugin to get the latest version. This is what i get.

Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java5-jre is already the newest version.
sun-java5-plugin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

So then i try and check the version again and I get teh same thing

agonoruci@agonoruci-desktop:~$ java -version
java version "1.4.2"
gij (GNU libgcj) version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-14ubuntu7)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

What should i do?

BTW: I am using Edgy Eft

---

### Post by igknighted on 2006-12-01
What repo did you try to install from?  I would bet this is where the issue is

---

### Post by agonoruci on 2006-12-01
I got this from Synaptic Package Manager I do not understand what u mean by repo i am froob lol.

---

### Post by igknighted on 2006-12-01
ok, I would recommend you install a program called automatix2 (try [www.getautomatix.com](www.getautomatix.com) for instructions).  It lets you install java as well as many other programs (including limewire and other p2p programs) and it automates it for you.  It should get you the proper java version as well as everything else you need.

---

### Post by timocrates on 2006-12-01
It might be because it is using GIJ 1.4 instead of Sun Java 1.5, even though the latter is installed.

sudo update-alternatives --config java

[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/java.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/java.html)

I might be wrong; I'm still trying to figure a lot of things out myself.

---

