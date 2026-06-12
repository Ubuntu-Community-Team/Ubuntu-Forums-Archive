---
title: "make help needed for aMSN webcam"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by r3bol on 2007-08-18
I have been trying to get my web cam working on amsn. I have been following this from the amsn website. I managed to find the webcamsn folder in /usr/share/amsn/utils/webcamsn and noticed it didn't have a second webcamsn folder within the first. Following the guide, I'm having trouble understanding what the instructions are to MAKE the source into a webcamsn.so file.

From the aMSN site...
**Webcamsn extension is not loaded. You have to compile it. (On Linux)**


You need to make sure there is a webcamsn.so in /msn/utils/webcamsn/
and also in /msn/utils/webcamsn/webcamsn/

If these do not exist, you need to enter each of those directories and type make to compile the source into a webcamsn.so file.
> 
beast@1[webcamsn]$ ls
aclocal.m4 config.sub INSTALL Makefile.in webcamsn
AUTHORS configure install-sh missing webcamsn.dll
ChangeLog configure.ac libmimic.pc mkinstalldirs webcamsn.so
config.guess COPYING libmimic.pc.in NEWS webcamsn.tcl
config.h CVS libtool pkgIndex.tcl
config.h.in datastream.bin ltmain.sh README
config.log depcomp Makefile src
config.status doc Makefile.am stamp-h1

> beast@1[webcamsn]$ make

beast@1[webcamsn]$ ls
CVS Makefile webcamsn.c webcamsn.o webcamsn.vcproj
libmimic.a Makefile.in webcamsn.h webcamsn.so

*Note: My webcam isn't working in camorama either. It is however recognised in ubuntu because it asks me to import my pictures. I have used it as a webcam before in windowz.*

Thanks for your help.

---

