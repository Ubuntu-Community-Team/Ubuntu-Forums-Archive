---
title: "Installing winmodem getting more complicated..."
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by bombitmd on 2006-08-25
This is getting frustrating...

Before I can install my winmodem driver, I'm supposed to have the following installed:

build essential
linux headers
debhelper
fakeroot

I got both from debian and ubuntu package sites.  I tried installing the ubuntu ones (except fakeroot, there wasn't any in the ubuntu site) and only debhelper installed properly.

build_essential_10.1_1ubuntu1_i386.deb didnt install because it said something about gcc and g++ missing or it was looking for another version.

fakeroot_1.2.10_i386.deb said something about libc6

linux-headers-2.6.10-5-386 (etc.) said something about dependency


:confused: What on earth do I do now? Should I try using the equivalent packages I downloaded from debian site?  Do I download gcc, g++, and libc6? which versions?

Woe is me!!!

---

### Post by Bachstelze on 2006-08-25
build-esential is a metapackage. If you want to install it mmanually, you'll have to take care of all dependencies and it will be hell. Can't you get your hands on an internet connection just to install these (and also upgrade to Dapper) ?

---

### Post by bombitmd on 2006-08-25
No, I can't, at least not while running Linux.  I have to download each package one by one in Windows.  So far the packages are pretty small, except for the linux header.  I'll have to install each package manually.  I'm not stopping until I can connect to the Internet using Ubuntu!!!

It doesn't help either that I only have Hoary.  Dapper runs too slow on my machine...

---

### Post by Bachstelze on 2006-08-25
Bot why don't you download a DEB directly from Linuxant ?

You could also get your hands on a SmartLink modem, the driver for them is available in the repos.

---

### Post by bombitmd on 2006-08-25
I could but it will limit me to 14.4kbps. The install procedure I'm following uses a set of free drivers that are compatible and can run at a the full 56 kbps.  Well, I'm downloading the linuxant driver, too.

I just had a thought:
Can I apt-get what I need from the Ubuntu Dapper install CD?

---

### Post by Bachstelze on 2006-08-26
Actually, I checked my Hoary CD and it seems all the packages you need are in there :p

---

### Post by towsonu2003 on 2006-12-05
would the instructions here help?
[https://help.ubuntu.com/community/DialupModemHowto/FromSource](https://help.ubuntu.com/community/DialupModemHowto/FromSource)

---

