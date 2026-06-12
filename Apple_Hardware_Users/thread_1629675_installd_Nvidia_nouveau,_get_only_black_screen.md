---
title: "installd Nvidia nouveau, get only black screen"
date: 2010-11-24
forum: Apple Hardware Users
---

### Post by Azyx on 2010-11-24
I have an PPC iMac 4g flat-screen half white spheric foot, with 800MHz speed. I also have Geforce4 Go 440 according to lspci.

sudo apt-get install xserver-xorg-video-nouveau. But now the screen are black and I don't come into terminal with ctrl+alt+f3 or cntr+alt+f1. How do I do? /Cheers

---

### Post by linuxopjemac on 2010-11-24
```
cat /var/log/Xorg.0.log
```
please

---

### Post by Azyx on 2010-11-24
> **linuxopjemac said:**
> ```
cat /var/log/Xorg.0.log
```please

I don't have any terminal.

/Cheers

---

### Post by linuxopjemac on 2010-11-24
see other thread

---

