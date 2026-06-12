---
title: "What this code means?"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by pizza on 2007-08-14
On the [Installation- with floppies ]("https://help.ubuntu.com/community/Installation/WithFloppies")

It said to put the 3 images on the floppy and has this code below it? What do I do with this code?

```
dd if=/path/to/floppy/images/boot.img of=/dev/fd0
```


I am using this method because I have no working cd drive

Thanks for your help

Matthew

---

### Post by Blutack on 2007-08-14
Those instructions are a bit mean!
Try these instead
[https://help.ubuntu.com/community/SmartBootManagerHowto](https://help.ubuntu.com/community/SmartBootManagerHowto)

---

### Post by pizza on 2007-08-14
yes they are mean lol, Remember I dont have a working cd rom drive so will this guide still work?

---

### Post by pizza on 2007-08-14
which one of these do I need 

The newest stable version of Smart BootManager is 3.7 release 1:
Source code : btmgr-3.7-1.tar.gz
Source RPM : btmgr-3.7-1.src.rpm
Binary Linux: sbminst
Binary RPM : btmgr-3.7-1.i386.rpm
Binary DOS : sbminst.exe (Support file: cwsdpmi.exe)
Themes pack : themes-3.7.tgz
Docs package: user-guide-3.7.tgz

---

### Post by louieb on 2007-08-14
> **pizza said:**
> ...I dont have a working cd rom drive so will this guide still work?
SBM is a workaround  for older PC's that can't boot to their CD drive. If your drive does not work at all then SBM won't help you.

---

