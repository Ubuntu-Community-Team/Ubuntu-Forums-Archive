---
title: "Where to extract Java Runtime 1.5?"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by WalmartSniperLX on 2006-09-05
Hey I just downloaded Java Runtime 1.5 and extracted the contents into a folder. But, I dont know where Im supposed to place it lol. Where is java supposed to be? Is it usr/lib? Or what?

---

### Post by WalmartSniperLX on 2006-09-05
See im trying to install limewire and im getting this:

[I]Starting LimeWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. LimeWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
patrick@patrick-desktop:~/Desktop/LimeWire$
[/I]

---

### Post by monktbd on 2006-09-05
download the jre from the repositories with apt-get:

[https://help.ubuntu.com/ubuntu/desktopguide/C/programming.html](https://help.ubuntu.com/ubuntu/desktopguide/C/programming.html)

---

### Post by WalmartSniperLX on 2006-09-05
ok thanks :D

---

### Post by WalmartSniperLX on 2006-09-05
darn it it says it cannot be found. I must bot be connected to the right channel. I have all the repos checked tho (including multiverse)

---

### Post by WalmartSniperLX on 2006-09-05
WAIt nvm i didnt have it before but now i do lolol

---

### Post by WalmartSniperLX on 2006-09-05
patrick@patrick-desktop:~$ sudo apt-get sun-java5-jre
E: Invalid operation sun-java5-jre


ok whats this.. :confused: ](*,)

---

### Post by monktbd on 2006-09-05
> **WalmartSniperLX said:**
> patrick@patrick-desktop:~$ sudo apt-get sun-java5-jre
E: Invalid operation sun-java5-jre


ok whats this.. :confused: ](*,)

the command is wrong :)


sudo apt-get **install** sun-java5-jre

apt-get is for installing and removing and checking .. so it needs to know what to do.

---

### Post by WalmartSniperLX on 2006-09-05
> **monktbd said:**
> the command is wrong :)


sudo apt-get **install** sun-java5-jre

apt-get is for installing and removing and checking .. so it needs to know what to do.

LOL darn me. Ok it worked now thanks a lot :D

---

