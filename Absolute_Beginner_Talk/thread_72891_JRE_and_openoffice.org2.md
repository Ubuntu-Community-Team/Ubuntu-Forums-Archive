---
title: "JRE and openoffice.org2"
date: 2005-10-07
forum: Absolute Beginner Talk
---

### Post by kawinter on 2005-10-07
I have an AMD-64 machine and Breezy Badger was installed by a friend 2 weeks ago. My Openoffice.org2 wants a JRE. I have been told I can download the sources from Sun but I am a serious noob. I went to the sun site and there seem to be many files available.  How do I find out which is  correct for my machine and distro and I would also be very grateful for instructions on how to install it from source once I have downloaded the file. 
 
 Any directions or help you could give me would be greatly appreciated.

Thank you.

---

### Post by nitricacid on 2005-10-07
Try this post [http://ubuntuforums.org/showthread.php?t=70017&page=2](http://ubuntuforums.org/showthread.php?t=70017&page=2)

---

### Post by kawinter on 2005-10-10
[QUOTE=nitricacid]Try this post [http://ubuntuforums.org/showthread.php?t=70017&page=2](http://ubuntuforums.org/showthread.php?t=70017&page=2)[/QUOTE]


The java package mentioned in that thread was not the correct one for my computer.  Someone else helped me find the right package so I downloaded it, and followed the first set of instructions from that thread and then got to the part where it said to:

fakeroot make-pkg jre-1_5_0_04-linux-amd64.bin

so I did that and got:

make-pkg: command not found

What now?

---

### Post by asimon on 2005-10-10
[QUOTE=kawinter]fakeroot make-pkg jre-1_5_0_04-linux-amd64.bin
[/quote]
There must be a typo here. It's make-**j**pkg and not make-pkg.

[QUOTE=kawinter]
so I did that and got:

make-pkg: command not found

What now?[/QUOTE]
In case you get the same with make-jpkg, install the package "java-package". make-jpkg is part of java-package.

---

### Post by Nadir on 2005-10-10
[quote=kawinter]The java package mentioned in that thread was not the fakeroot make-pkg jre-1_5_0_04-linux-amd64.bin

[/quote]

Careful: openoffice.org 2 for amd64 is really a 32bit version. Therefore you might need a 32bit JVM for that.

Tristan

---

### Post by kawinter on 2005-10-10
[QUOTE=Nadir]Careful: openoffice.org 2 for amd64 is really a 32bit version. Therefore you might need a 32bit JVM for that.

Tristan[/QUOTE]

Thank you Tristan, that's interesting.  Since I found the right file on the Sun website and installed (following the Sun directions) it I am not getting that "must run in a JRE" error from OpenOffice.org2 any more.  It still is temperamental though with occasional lockups  so maybe that is the 32 vs. 64 issue.

However the AMD64 version of the Java install from Sun does NOT include the plugin so browser-wise I am no better off.  Any suggestions or do I just need to wait longer until more 64bit stuff is available?

---

