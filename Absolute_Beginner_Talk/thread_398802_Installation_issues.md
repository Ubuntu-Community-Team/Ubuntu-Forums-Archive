---
title: "Installation issues"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by LightShadow on 2007-04-01
I recently decided to try out Ubuntu Linux and when I downloaded version 6.10 and burned the CD.  Now it ran and installed on my Laptop fine however when I try to boot it up on my Desktop it gets passed the Ubuntu booting screen then I see the brown background and see a partial/distorted window sometimes I'll hear a sound sometimes I won't.  Then it sits there and does nothing at all.  Any help is greatly appreciated.

Thanks!

---

### Post by zvacet on 2007-04-01
Maybe it is your video card.
```
 sudo dpkg-reconfigure xserver-xorg
```
If you have nvidia card replace** nvidia** with **nv** If it is another card choose **vesa**
After that you can go to find proper driver for your card.

---

