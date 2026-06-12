---
title: "frostwire/java"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by irishgoth8822 on 2008-02-11
```
Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at http://www.java.com
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com

```

i installed what i thought was the sun java package as well as several other basic java packages, but apparently i dont have the correct ones installed, since trying to start frostwire gets me that output.

what packages am i missing?

---

### Post by taurus on 2008-02-11
```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin 
sudo update-alternatives --config java
```
And make sure the latest one is the default version.

---

