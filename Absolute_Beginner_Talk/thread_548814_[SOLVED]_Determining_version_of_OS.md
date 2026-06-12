---
title: "[SOLVED] Determining version of OS"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by Michael Young on 2007-09-11
How do I determine the version of ubuntu OS I have installed?
I want to download packages (specifically Xerces 2.8 tarball), but I don't know if ubuntu is 32 or 64-bit on my platform (Intel Pentium M).  I believe I installed ubuntu 7.04, but I'm not sure...

---

### Post by runemaste644 on 2007-09-11
```
uname -a
```should do it. It tells the kernel version, though. For finding out if its feisty open firefox and it tells in the default home page.

---

### Post by sumguy231 on 2007-09-11
lsb_release -a will do exactly what you want.

---

### Post by Michael Young on 2007-09-11
uname gives me basic info - see below.  About dialog in Firefox indicates I'm using ubuntu-feisty.  Unfortunately, I don't see anything here that indicates this version is 32-bit (or 64-bit).  Does "feisty" imply I'm one or the other?  (i.e., re all flavors of feisty all the same "bit-width"?  at least, for the same platform?)

myoung:~$ uname -a
Linux my-computer-001 2.6.20-16-generic #2 SMP Fri Aug 31 00:55:27 UTC 2007 i686 GNU/Linux

---

### Post by Michael Young on 2007-09-11
lsb_release -a gives me the output below.  Sorry for being such a noob, but I still have the same question - 32 or 64-bit...

myoung:~$lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 7.04
Release:        7.04
Codename:       feisty

---

### Post by Snoopyowns on 2007-09-11
The Pentium M is a 32-bit processor. So you should be using the 32-bit version. I'm not even sure if it's possible to install 64-bit Ubuntu on a 32-bit system. I could be wrong though :P

Err nevermind, looks like there are some 64-bit Pentium M's :P

---

### Post by rsambuca on 2007-09-11
You have 32bit OS installed, which is the correct architecture for your cpu.

---

### Post by Michael Young on 2007-09-12
I will be specifying to build and/or install 32-bit binaries where necessary.
Thank you all for your help.

---

