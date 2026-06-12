---
title: "Installing Java JDK and API"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by Tyke91 on 2007-05-27
Hey guys, sorry for the confusion before.

alright. I'm probably doing this the hard way... but i'm trying to successfully download and install Java 6 JDK and API from this website
[https://sdlc3d.sun.com/ECom/EComActionServlet;jsessionid=FCFB1AC92377D78E154D12823F000201](https://sdlc3d.sun.com/ECom/EComActionServlet;jsessionid=FCFB1AC92377D78E154D12823F000201)

I'm running feisty and ive got an intel core 2 duo processor with 2.13 GHz on each cpu

when i type uname -a into my console i get this

2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux

the file has finished downloading, but when i try to run it, it fails telling me that gedit has failed to detect the character coding.


how do i get Java 6 development kit and API docs on my comp?

---

### Post by taurus on 2007-05-27
If you want to install java 1.6 on your machine, Feisty, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install sun-java6-bin sun-java6-plugin sun-java6-font sun-java6-doc
java -version
```
Otherwise, post the output of this command from a terminal.

```
ls -la ~/Desktop
```

---

### Post by Tyke91 on 2007-05-27
i got this.

total 61376
drwxr-xr-x  2 mykola mykola     4096 2007-05-27 22:48 .
drwxr-xr-x 54 mykola mykola     4096 2007-05-27 23:01 ..
-rw-r--r--  1 mykola mykola 62772481 2007-05-27 22:48 jdk-6u1-linux-i586.bin


btw - i've been copy/pasting these commands... yet i still dont know what they do.

what was the function of the command you just told me to run?

btw- my name is Mykola... which is why it just popped up 6 times :P

---

### Post by taurus on 2007-05-27
The first command is to update your repos.

The second command is to install Sun java 1.6, plugins for your web browser, font, and doc.

The third command is to check to make sure you have the latest version of java, 1.6.

So, did you run three commands and did you get any error message?

What's the output of this command from a terminal then?

```
java -version
```

---

### Post by Tyke91 on 2007-05-27
ah, i should have told you that i already had java 6.  (got it earlier today, no problem)

I want to write my own java code, which is why i need the JDK

output from that command is...

odd...

java version "1.4.2"
gij (GNU libgcj) version 4.1.2 (Ubuntu 4.1.2-0ubuntu5)


i swear it was updated to 1.6 earlier today...

k... im getting error codes from installing java 1.6


```
mykola@TheWinLixBeast-Mykolas:~$ ls -la ~/desktop
ls: /home/mykola/desktop: No such file or directory
mykola@TheWinLixBeast-Mykolas:~$ ls -la ~/Desktop
total 61376
drwxr-xr-x  2 mykola mykola     4096 2007-05-27 22:48 .
drwxr-xr-x 54 mykola mykola     4096 2007-05-27 23:01 ..
-rw-r--r--  1 mykola mykola 62772481 2007-05-27 22:48 jdk-6u1-linux-i586.bin
mykola@TheWinLixBeast-Mykolas:~$ 
mykola@TheWinLixBeast-Mykolas:~$ java -version
java version "1.4.2"
gij (GNU libgcj) version 4.1.2 (Ubuntu 4.1.2-0ubuntu5)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
mykola@TheWinLixBeast-Mykolas:~$ sudo aptitude update
Password:
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release [44.7kB]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages [24.7kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages [6269B]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources [4575B]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources [946B]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages [9473B]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources [1366B]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages [3321B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources [14B]
Fetched 95.6kB in 1s (57.0kB/s) 
Reading package lists... Done
mykola@TheWinLixBeast-Mykolas:~$ sudo aptitude install sun-java6 sun-java6-plugin-font sun-java6-doc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find package "sun-java6".  However, the following
packages contain "sun-java6" in their name:
  sun-java6-plugin sun-java6-demo sun-java6-fonts sun-java6-bin 
  sun-java6-doc sun-java6-jdk sun-java6-jre sun-java6-source 
  sun-java6-javadb 
Couldn't find any package whose name or description matched "sun-java6-plugin-font"
The following packages have been automatically kept back:
  linux-image-generic linux-restricted-modules-generic 
The following packages have been kept back:
  linux-generic linux-headers-generic 
The following NEW packages will be installed:
  sun-java6-doc 
0 packages upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
Need to get 39.7kB of archives. After unpacking 197kB will be used.
Writing extended state information... Done
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse sun-java6-doc 6-00-2ubuntu2 [39.7kB]
Fetched 39.7kB in 0s (43.0kB/s)       
Selecting previously deselected package sun-java6-doc.
(Reading database ... 100305 files and directories currently installed.)
Unpacking sun-java6-doc (from .../sun-java6-doc_6-00-2ubuntu2_all.deb) ...
Setting up sun-java6-doc (6-00-2ubuntu2) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] 
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] dpkg: error processing sun-java6-doc (--configure):
 subprocess post-installation script killed by signal (Interrupt)
Errors were encountered while processing:
 sun-java6-doc
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up sun-java6-doc (6-00-2ubuntu2) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] no 
Abort installation of JDK documentation
dpkg: error processing sun-java6-doc (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 sun-java6-doc
mykola@TheWinLixBeast-Mykolas:~$ 
mykola@TheWinLixBeast-Mykolas:~$ java -version
java version "1.4.2"
gij (GNU libgcj) version 4.1.2 (Ubuntu 4.1.2-0ubuntu5)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
mykola@TheWinLixBeast-Mykolas:~$ 


```

---

### Post by taurus on 2007-05-27
> **Tyke91 said:**
> ah, i should have told you that i already had java 6.  (got it earlier today, no problem)

I want to write my own java code, which is why i need the JDK

output from that command is...

odd...

[COLOR="Blue"]java version "1.4.2"
gij (GNU libgcj) version 4.1.2 (Ubuntu 4.1.2-0ubuntu5)[/COLOR]


i swear it was updated to 1.6 earlier today...

k... im getting error codes from installing java 1.6

I guess not because it is still that gij version.  

How did you install it?

And if you want the JDK, you can install it from a terminal as well.

```
sudo aptitude install sun-java6-jdk
```

---

### Post by Tyke91 on 2007-05-27
i installed it with help from this forum earlier today

[http://ubuntuforums.org/showthread.php?t=455535](http://ubuntuforums.org/showthread.php?t=455535)

i assumed it worked because java applications that needed updates suddenly all worked

---

### Post by Tyke91 on 2007-05-27
k... so it's telling me that

```
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    http://java.sun.com/javase/downloads/

now and download.  The file should be owned by root.root and be copied
to /tmp.

```

i've gone to the site, but i can't find either of those 2 files to download.

---

### Post by Tyke91 on 2007-05-27
i'm getting the same issue installing the jdk

---

