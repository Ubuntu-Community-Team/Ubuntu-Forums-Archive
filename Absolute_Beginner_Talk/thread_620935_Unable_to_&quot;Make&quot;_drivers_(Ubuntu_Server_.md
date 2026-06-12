---
title: "Unable to &quot;Make&quot; drivers (Ubuntu Server 7.10)"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by Juice777 on 2007-11-23
I have a HP Workstation xw6000, with Broadcom BCM5700 Ethernet. I have attempted to build both the TG3 drivers which I have obtained from the Broadcom Website and also the BCM5700 source which I obtained from the Ubuntu Website. Both receive the same error.

make -c SUBDIRS=... modules
make: *** SUBDIRS=... : No Such file or Directory. Stop.
make: *** [default] Error 2

I have followed the Readme Instructions for the broadcom drivers. What am I doing wrong?

---

### Post by Pumalite on 2007-11-23
sudo apt-get install build-essential
And try again.

---

### Post by Juice777 on 2007-11-23
Installed the build-essential app

Tried again and still same..

Any ideas?

---

### Post by roninb on 2007-12-22
I am having smae problem with bcm 5700on a 64 bit intel. I don't know how to even unpackage tar or rpm at this time. So if some one repleys please spell everything out and i will print it up and take to my ubuntu and try to get it to work.

---

