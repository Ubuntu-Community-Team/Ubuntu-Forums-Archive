---
title: "installing ati driver"
date: 2006-04-18
forum: Absolute Beginner Talk
---

### Post by nick5449 on 2006-04-18
I just installed Linux (Ubuntu dapper) for the first time and could use a little help.  Im trying to install a driver for my video card (which Im actually not even sure if I need to do) and am having some trouble.  When I run the file I get the following error:

Detected configuration:
Architecture: i686 (32-bit)
X Server: Xorg 7.0.0

Detected version of X does not have a matching 'x700' directory
You may override the detected version using the following syntax:
     X_VERSION=<xdir> ./ati-driver-installer-<ver>-<arch>.run [--install]

The following values may be used for <xdir>:
    x410        XFree86 4.1.x
    x420        XFree86 4.2.x
    x430        XFree86 4.3.x
    x680        X.Org 6.8.x
    x690        X.Org 6.9.x
Removing temporary directory: fglrx-install

Can someone tell me what this means?  Thanks for any help.

---

### Post by William the Conquerer on 2006-04-18
well ok, so first of all, if you don't know if you need to upgrade your video driver than you probably don't =).  What you're dealing with is fglrx which is the xorg ati driver that should let you do cool opengl fancy stuff like that (Xgl and things like that).  Personally I would suggest just typing in a terminal:

$ sudo apt-get update
$ sudo apt-get install xorg-driver-fglrx

that'll install the same driver, but it's in the repository so it will get updated as the developers work on it.  BUT if you really want to install the newest version of the fglrx driver just use this link: [https://wiki.ubuntulinux.org/BinaryDriverHowto/ATI](https://wiki.ubuntulinux.org/BinaryDriverHowto/ATI)

that should answer questions and walk you through installing the ati drivers =).

---

