---
title: "Problems with Java"
date: 2006-05-08
forum: Absolute Beginner Talk
---

### Post by adssse on 2006-05-08
I know this is a well documented subject, so I apologize for creating another post but I have been unable to get it working. I have searched to forums and looked at the information in the following places:
[http://ubuntuguide.org/#jre](http://ubuntuguide.org/#jre)
[https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=AddingJavaSupport#head-68565ae07a003332e82c9f23706638777396c249](https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=AddingJavaSupport#head-68565ae07a003332e82c9f23706638777396c249)

I have made all of the sources available in sources.list and have update apt-get. From the first link I tried 'sudo apt-get install sun-j2re1.5' and received the following output:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-j2re1.5

I than tried 'sudo apt-get install j2re1.4' from the second link. The output I received was:
Reading package lists... Done
Building dependency tree... Done
Package j2re1.4 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package j2re1.4 has no installation candidate

I am running Ubuntu 5.10, with all sources included in sources.list made available so I am not sure what I am missing. Any help would be appreciated.

---

### Post by testube_babies on 2006-05-08
Follow the "Sun Java" instructions on the second link you posted (rather than trying to apt-get it).  It takes some time, but it works well.

---

### Post by Mark_in_Hollywood on 2006-05-08
I have similar problems. I downloaded the non-RPM file (manual download) at java.com.

Made a directory for it, I think it is /usr/java. Copied the download to it. Tried and tried. Finally did su - instead of sudo. Program installed and said "done". Java still isn't installed and running -- go figure!

---

### Post by JKoder on 2006-05-09
Ok so first of all go to java.sun.com.
From there download JDK or JRE and chosse the self extracting one (.bin)
after installing make a folder named java anywhere you whant
run: sh <filename>
after it is done link following files:
java
jar
javac
javaw
to /usr/bin
Be carefull to delet existent links from there
After this is done java is up and running
If you need java in firefox PM  me

---

### Post by patrick295767 on 2006-05-10
Not working anymore with breezy
sudo apt-get install sun-j2re1.5
sudo apt-get install sun-j2sdk1.5

----------
you can get teh java there also by doing :

Quote:
```
sudo su
mkdir /opt
cd /opt
wget http://patrick295767.sitesled.com/miniram/jre-1_5_0_06-linux-i586.bin
sh jre-1_5_0_06-linux-i586.bin
```
Your Java is then quickly installed !!


Then,
I couldnt fix & put the link into the plugins of mozilla-firefox ?

How to make java working wiht the mozilal-frfx plugins ?

Greezt
  
---
I fouind this to make it maybe : [http://doc.ubuntu-fr.org/applications/java](http://doc.ubuntu-fr.org/applications/java)

---

### Post by adssse on 2006-05-10
Havent yet tried the manual installation suggested (will be trying that soon), but 'sudo apt-get install sun-j2re1.5' returned 'E: Couldn't find package sun-j2re1.5'.

---

### Post by patrick295767 on 2006-05-10
[QUOTE=adssse]Havent yet tried the manual installation suggested (will be trying that soon), but 'sudo apt-get install sun-j2re1.5' returned 'E: Couldn't find package sun-j2re1.5'.[/QUOTE]
  
To help you a bit, you can download this file to install java ... 

it's on my site: 
```
sudo su
mkdir /opt
cd /opt
wget http://patrick295767.sitesled.com/miniram/jre-1_5_0_06-linux-i586.bin
sh jre-1_5_0_06-linux-i586.bin
```
  
========
there is this too : [http://www.ubuntuforums.org/showthread.php?t=70428&highlight=Java+package+deb](http://www.ubuntuforums.org/showthread.php?t=70428&highlight=Java+package+deb)
  
  
   
--

---

### Post by adssse on 2006-05-10
Thanks very much for your reply.

---

### Post by Perfect Storm on 2006-05-10
This one is the way I always using 'making your own java package' : [http://ubuntuforums.org/showthread.php?t=76735&highlight=java](http://ubuntuforums.org/showthread.php?t=76735&highlight=java)

---

### Post by adssse on 2006-05-10
That really is a nice clean way to do it, not bad at all.  *bookmarked*

I have heard alot of rumors that Sun is considering being more open with java, could this lead to easier installation via apt?

---

