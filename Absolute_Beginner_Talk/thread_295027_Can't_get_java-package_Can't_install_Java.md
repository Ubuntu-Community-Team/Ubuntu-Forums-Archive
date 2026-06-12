---
title: "Can't get java-package Can't install Java"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by lilalfyalien on 2006-11-07
Hi,

Please help me! I'm trying to install Sun's java on by Ubuntu Dapper Drake box. I've read millions of webpages on this nothing is working! For example, I try the following and look what happens: (!)

```
sudo apt-get -u install java-package
Reading package lists... Done
Building dependency tree... Done
Package java-package is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package java-package has no installation candidate
```

I have all possible repositories enabled, I have done apt-get update. How can I install the Java sdk on my system?

I've been to the Sun website downloaded the .bin files, installed a .deb file listed on these forums nothing works I only get the following:
```
java -version
java version "1.4.2"
gij (GNU libgcj) version 4.1.0 (Ubuntu 4.1.0-1ubuntu8)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

```

But I'm trying to get the Sun version?!

Please can someone explain a way that I can get Java (in a directory that I know as I'm tryin to install Tomcat)?

Thanks,

Lilalfyalien

---

### Post by taurus on 2006-11-07
Use automatix to install it on your system.  Fast and easy for newbies...

[http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38#Installing_on_.28K.2CX.29Ubuntu_6.06_i386.2Camd64_.28Dapper.29](http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38#Installing_on_.28K.2CX.29Ubuntu_6.06_i386.2Camd64_.28Dapper.29)

---

### Post by jordanmthomas on 2006-11-07
You can install java anywhere you want if you get the bin from the site...you just need to update your PATH variable to include it.  For example, say you install java in /home/yourname/java, you would put this in your ~/.bashrc
```

PATH=/home/yourname/java/bin:$PATH

```
...but that'll only work in terminals where you log in as you.

If you have installed a deb like you say you have, try this:
```
sudo update-alternatives --config java
```
and choose the sun java from the list.

---

### Post by ajgreeny on 2006-11-07
If it is the runtime environment files and package you need simply use apt-get as you did, but install sun-java5-jre and not java-package

---

