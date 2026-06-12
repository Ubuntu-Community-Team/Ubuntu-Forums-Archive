---
title: "Java &amp; Frostwire"
date: 2006-02-17
forum: Absolute Beginner Talk
---

### Post by snake1130 on 2006-02-17
ok I have installed java using [this]("https://wiki.ubuntu.com/FirefoxAMD64FlashJa") tutroial.
After following [this]("http://www.ubuntuforums.org/showthread.php?t=105169&highlight=frostwire") to install frostwire. When start the program in the termianal i get this

```
blake@ubuntu:~$ cd /opt/FrostWire/
blake@ubuntu:/opt/FrostWire$ java -jar FrostWire.jar
Exception during runtime initialization
java.lang.NullPointerException
   <<No stacktrace available>>
blake@ubuntu:/opt/FrostWire$

```

and nuthing happen. I was just wondering how I could fix this to get frostwire working. I am on Latest and Greates AMD 64

---

### Post by austin on 2006-02-17
what happens when you type           java --version         ?

---

### Post by snake1130 on 2006-02-17
```
java version "1.4.2"
gij (GNU libgcj) version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)

Copyright (C) 2005 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
blake@ubuntu:~$

```

---

### Post by austin on 2006-02-17
it seems that gnu-jre is active here. Are you sure you installed a sun jre? Do you remember where? If yes, try to find the java binary from sun and run your command with full path, e. g. 

/usr/bin/sunjre1.1.1/java -jar FrostWire.jar

Also you might have to set the right path to the core java classes, something like 

/usr/bin/sunjre1.1.1/java -classpath /usr/bin/sunjre1.1.1/lib -jar FrostWire.jar

(there's many ways to set the classpath)

---

### Post by snake1130 on 2006-02-17
ok well i got it to run but now it gives me 

```
Unable to use folder
```

during the Wizared. Any folder I pick it gives the same error :(

---

