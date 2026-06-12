---
title: "UBUNTU NEWBIE-- Looking for advise"
date: 2006-03-03
forum: Absolute Beginner Talk
---

### Post by wolverine007 on 2006-03-03
Hello,

I am looking for compliers to run on Ubuntu. I need compliers for C/C++ and Java. 

With regards to Java, i assume i can download the Java envoriment engine from Sun's website and run it?

Also, is there a complier or problem that would run VB on Ubuntu, or is this wishful thinking?

Regards,

Wolverine

---

### Post by jrib on 2006-03-03
installing the 'build-essential' package through system > administation > synaptic will give you gcc and g++ for c and c++.

Basic usage (using applications menu > accessories > terminal):
```
gcc file.c -o some_name
```
This compiles and creates a file called some_name that you can run (if you omit the ``-o some_name'' part, it will default to ``a.out'').
Then to run your file, just specify the path to it.  If you are in the directory where you created it:
```
./some_name
```

for c++ just use g++ instead of gcc

---

### Post by nalmeth on 2006-03-03
What is VB?
If you want to cheat, use automatix to install Java:
[http://www.ubuntuforums.org/showthread.php?t=114251](http://www.ubuntuforums.org/showthread.php?t=114251)

---

### Post by cotcot on 2006-03-03
Java (sun-JRE1.5) is available in this repository :

deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

Add these to /etc/apt/sources.list (use sudo gedit /etc/apt/sources.list ), save and do an apt-get update. You should then be able to install it through synaptic.

---

