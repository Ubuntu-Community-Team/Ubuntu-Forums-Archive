---
title: "after installing..."
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by stickperson on 2007-04-20
Hey guys, I plan on installing Ubuntu today I just have a couple of questions about after installing it.  What happens if I want to get rid of Ubuntu and then get rid of the partition I made for it?  Is there a way to do that without losing everything on both partitions?  Also, when I tried running Beryl when I use Ubuntu off the cd, I follow all the steps and just get a blank white screen.  I'm guessing that's because I'm running it from the cd.  Any help is greatly appreciated!

---

### Post by Cypher on 2007-04-20
With both partitions I'm assuming that you mean Windows is on one of your partitions. If you install Ubnutu on your HD and have it install GRUB into the MBR, then it will dual-boot Linux and Windows. If you were to remove Ubuntu and remove the partitions, you'd have to do some work to get Windows to restore it's own boot loader and then you can reclaim the deleted partitions for Windows use.

Regards

---

