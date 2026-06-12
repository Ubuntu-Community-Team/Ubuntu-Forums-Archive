---
title: "Lost dual boot"
date: 2006-02-24
forum: Absolute Beginner Talk
---

### Post by neelabhro on 2006-02-24
I had an XP/Ubunutu dual boot, set up using GRUB during ubunutu installation. 

I have since formmatted and reinstalled XP on it partition.

However, the dual-boot promptdoesn't show up, although i'm pretty sure that ubunutu is still installed in its partition..

any ideas??

---

### Post by suRoot on 2006-02-24
When you formatted & reinstalled XP you blew away the master boot record where Grub lives - and replaced it with ntldr (the XP boot loader).  This thread should tell you how to fix it:

[http://www.ubuntuforums.org/showthread.php?t=24113](http://www.ubuntuforums.org/showthread.php?t=24113)

---

