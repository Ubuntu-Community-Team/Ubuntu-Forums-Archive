---
title: "Compiing i965_dri.so"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by rene100 on 2006-11-11
Hi guys, I'm wondering if somebody can help me with a problem.  I'm trying to fix my DRI and i found the thread with the explanation on how to do this, but I'm too much of a newb to follow it.  

The last post includes a Makefile, but when I run the make -f Makefile command, it doesn't work properly.

The thread is [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/62135](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/62135)

Assistance with this would be greatly appreciated.  It is to get dri / 3d working with g965 intel onboard video (gma x3000)

Thanks in advance

-R

---

### Post by faddat on 2006-11-15
The first thing you want to do is install the package build-essential.  That will let you compile things on your system.  My friend has the same graphics chipset and I will continue to try to troubleshoot this and let you know the results.

---

### Post by lyur123 on 2006-12-18
I'm with this problem, i don't know how to compile that to  enable openGL with Q965 or G965 chipsets.

I take the message that i need to build dri module of mesa with -fno-strict-aliasing  ...

... but i don't know how to do that.

I have build-essentials and others that i think that i could need, i take the mesa sources doing  apt-get source libgl1-mesa-dri  , but i don't know how to continue.

Anyone could tell us how to build dri module from edgy or feisty?



Thx in advance!

---

