---
title: "frostwire doesnt start"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by ELD on 2007-09-23
i get this error
> 
liam@liam-desktop:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at [http://www.java.com](http://www.java.com) [java = SableVM]
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
liam@liam-desktop:~$ 


yet i have checked i have java 6 installed??

---

### Post by Sourcey on 2007-09-23
What version of Java are you running?

From terminal type: 

java -version

---

### Post by ELD on 2007-09-23
> 
liam@liam-desktop:~$ java -version
SableVM version 1.13
- compile date and time: 2006-11-09 00:24:19 UTC
- gcc version: 4.1.2 20061103 (prerelease) (Ubuntu 4.1.1-18ubuntu2)
- 'real life brokenness' features enabled
- signal based exception detection
- copying garbage collection
- bidirectional object layout
- inline-threaded interpreter


I am guessing by that it means this "sablevm" is old??

---

### Post by Arwen on 2007-09-23
java -version gives:
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)
and with these frostwire works fine

---

### Post by Sourcey on 2007-09-23
> **ELD said:**
> I am guessing by that it means this "sablevm" is old??

Yes install java runtime version 1.6

---

### Post by StJimmy on 2007-09-23
Open up terminal and enter the below code:
```
sudo apt-get install sun-java6-jdk sun-java6-plugin
```
use "Tab" to select "Ok" durin the useragreement 

then enter the below to update the version:
```
sudo update-java-alternatives -s java-6-sun
```

To make sure you have the correct version enter this:
```
java -version
```
you should get 1.6 as the version number

---

### Post by ELD on 2007-09-25
Nice one, fixed it!

---

