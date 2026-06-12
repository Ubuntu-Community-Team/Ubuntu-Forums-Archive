---
title: "QTParted problem"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by nwr222 on 2007-02-15
I can't get QTParted to run.  It was running at some stage in the past.  If I run it from the menu I get the splash screen for a few minutes, then it disappears.  If I run it from a terminal window I get the following...

linux@linux-desktop:~$ sudo qtparted
Password:
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

linux@linux-desktop:~$

The history of my installation is that I installed Xubuntu and have recently installed Kubuntu-desktop.

---

### Post by tchoklat on 2007-02-15
If you are ruinning GPartEd to amend your partitions you need to boot from it. Download it, burn it to a CD and boot from it. See what happens then!
 
 
Tony

---

### Post by nwr222 on 2007-02-17
I was not trying to run Gparted, but I now have, and fixed my immediate problem - Thanks.

I would still like to know why QTParted has stopped working, and what I can do to make it work again.

---

