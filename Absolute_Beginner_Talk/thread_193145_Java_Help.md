---
title: "Java Help"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by cac007 on 2006-06-09
I have Java 1.5.0 so why is it saying this??





cory@ubuntu:~$ limewire
Starting LimeWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. LimeWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
Java exec found in  /usr/java/jre1.5.0_07/bin/
OOPS, you don't seem to have a valid JRE. LimeWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)  [/usr/java/jre1.5.0_07/bin/java = Error]
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)

---

### Post by user1397 on 2006-06-12
first of all, are you using breezy or dapper?

---

### Post by r3st on 2006-06-12
what are you trying to use limewire for?  file sharing can get you arrested and sued

---

### Post by dcstar on 2006-06-12
There is a major problem when installing JRE from the Dapper repos, the package requires a manual confirmation of accepting the Java licence agreement and the default debconf setting in Dapper does not allow you to do this, so it doesn't install!!

[http://ubuntuforums.org/showthread.php?t=148075](http://ubuntuforums.org/showthread.php?t=148075)

You may **think **you have installed it, but if this problem occured you may not have actually done a successful install.

I had to change the default behaviour of debconf to get **sun-java5-jre** to install on my system via Synaptic:
```
sudo dpkg-reconfigure debconf
```

---

### Post by user1397 on 2006-06-12
[quote=r3st]what are you trying to use limewire for?  file sharing can get you arrested and sued[/quote]some people just don't care, and some view this issue as a difference between what's legal/illegal and what's right/wrong ...

---

