---
title: "JDK Installation"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by T.R.E. on 2008-02-01
well...This going to be real though but i need to find out how to install jdk and set my JAVA_HOME. so don't get mad at me cuz i'm absolutely noob in linux. 

Well i've installed sun java 6 SDK from repos. but all i can find in the folder that's been installed is JRE    
and no JDK. i also searched the whole /usr folder with eclipse but it only found JRE. i thought i've installed the wrong JDK so i installed another SDK called iced tea. but same problem. when i type whereis javac it brings this:  /usr/bin/javac but i cant java packages and libraries. so any help would be appreciated.

---

### Post by taurus on 2008-02-01
```
sudo apt-get update
sudo apt-get install sun-java6-jdk
java -version
```
What's the output of the last command?

---

### Post by SOULRiDER on 2008-02-01
```
sudo aptitude install sun-java6-jdk
```

The java and javac commands should work with no problems.

---

### Post by T.R.E. on 2008-02-01
> **taurus said:**
> ```
sudo apt-get update
sudo apt-get install sun-java6-jdk
java -version
```
What's the output of the last command?

i told you i've installed java 6 but i cant find it. by the way the output's here: 
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) 64-Bit Server VM (build 1.6.0_03-b05, mixed mode)

---

### Post by taurus on 2008-02-01
```
sudo update-alternatives --config java
```

---

### Post by T.R.E. on 2008-02-01
> **taurus said:**
> ```
sudo update-alternatives --config java
```

i've also done this. here is the output sun java is my default.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
*         2    /usr/lib/jvm/java-6-sun/jre/bin/java
 +        3    /usr/lib/jvm/java-7-icedtea/jre/bin/java

---

### Post by taurus on 2008-02-01
Are you sure you installed the jdk, not the jre?  Can you post the whole output of this command from a terminal?

```
sudo apt-get install sun-java6-jdk
```

---

### Post by T.R.E. on 2008-02-01
> **taurus said:**
> Are you sure you installed the jdk, not the jre?  Can you post the whole output of this command from a terminal?

```
sudo apt-get install sun-java6-jdk
```

here's the output:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-jdk is already the newest version.
The following packages were automatically installed and are no longer required:
  fftw3 libtunepimp5 python-qt3 libkonq4 libcurl3 python-sip4 kdebase-bin
  libifp4 libdbus-qt-1-1c2 kdesktop kdebase-kio-plugins libpq5 libnjb5 libofa0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 212 not upgraded.

---

### Post by taurus on 2008-02-01
Try

```
sudo apt-get remove sun-java6-jre
sudo apt-get install sun-java6-jdk
sudo update-alternatives --config java
```

---

### Post by T.R.E. on 2008-02-01
is there anything else i should do? please help i have lot of work to do and i realy need java.

---

