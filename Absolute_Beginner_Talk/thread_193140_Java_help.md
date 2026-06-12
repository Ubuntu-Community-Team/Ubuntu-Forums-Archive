---
title: "Java help?"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by cac007 on 2006-06-09
This is what happens when i try to install java.  Anyone know what is wrong? Also how do i install all of this to /usr/java/


Do you agree to the above license terms? [yes or no]
y
Unpacking...
Checksumming...
0
0
Extracting...
UnZipSFX 5.42 of 14 January 2001, by Info-ZIP (Zip-Bugs@lists.wku.edu).
  inflating: jre-1_5_0_07-linux-i586.rpm
rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Packages index using db3 - No such file or directory (2)
error: cannot open Packages database in /var/lib/rpm

---

### Post by andersonmanly on 2006-06-09
Looks like you downloaded the Linux RPM version of Java. You can either install alien so that you can read/install RPM files (Ubuntu uses .deb packages) OR you can go back and download the generic Linux binaries. 

Looks like you downloaded the Linux RPM version of Java. You can either install alien so that you can read/install RPM files (Ubuntu uses .deb packages) OR you can go back and download the generic Linux binaries. 

[http://jdl.sun.com/webapps/download/AutoDL?BundleId=10542]("http://jdl.sun.com/webapps/download/AutoDL?BundleId=10542")

This will dump out a folder you can move it to /usr/java or whereever you want to put it. Perhaps there's a better way of doing all this via Synaptic, but I am at work right now, and have to use a windoze box :shock:  I know that you can get alien with Synaptic.

Good Luck

---

### Post by learning on 2006-06-09
you can get sunjava using synaptic.

---

### Post by brentoboy on 2006-06-09
if you look up the "ubuntu plf" (penguin liberation front) you can find instructions on including a repository that has the sun java binary installer.

it isnt included in ubuntu, becuase ubuntu includes free, open source software by default, and java is free, but not open source.

but the penguin liberation front "specializes" in getting things to penguin pc's that need to be liberated. :)

---

### Post by rbgCODE on 2006-06-09
[QUOTE=learning]you can get sunjava using synaptic.[/QUOTE]

When was the last time you did that because it is no longer the case.

---

### Post by Jagot on 2006-06-09
[QUOTE=rbgCODE]When was the last time you did that because it is no longer the case.[/QUOTE]

Yes it is - it is in the multiverse repo:

[http://www.ubuntu.com/testing/dapperrc#head-11bcb3682004f84b75da4ef2976726d4ff8ff44d](http://www.ubuntu.com/testing/dapperrc#head-11bcb3682004f84b75da4ef2976726d4ff8ff44d)

---

### Post by J0E0NE on 2006-06-09
This was extremly helpful to me :)
give it a try it fixed all my problems I was having:
[http://www.ubuntuforums.org/showthread.php?t=148075]("http://www.ubuntuforums.org/showthread.php?t=148075")

---

