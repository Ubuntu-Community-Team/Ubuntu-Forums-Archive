---
title: "accessing windows hard drive"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by BaronVonSTFU on 2007-04-13
I have a second hard drive that was partitioned for xp.  It has all my music and movies on it so I dont want to reformat it.  Is there any way to access it through ubuntu?  It doesnt even show up under computer.

---

### Post by taurus on 2007-04-13
You need to mount it before you can access it.  Here's a guide.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by n3tfury on 2007-04-13
> **taurus said:**
> You need to mount it before you can access it.  Here's a guide.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

wow, what a pain in the butt that looks to be.  why doesn't it auto-mount like various live cd's do? (kanotix, knoppix, etc)

---

### Post by Gazneth on 2007-04-13
Try NTFS-3G it has a nice gui interface to enable and disable read write access, If you use feisty it is in the repositories already.

---

### Post by BaronVonSTFU on 2007-04-14
Yea that worked.   Can I not delete or add things to that hard drive even though I have it mounted?

---

### Post by Gazneth on 2007-04-14
I found out today that you also need ntfs-config to work with ntfs-3g here is a how to link.[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

