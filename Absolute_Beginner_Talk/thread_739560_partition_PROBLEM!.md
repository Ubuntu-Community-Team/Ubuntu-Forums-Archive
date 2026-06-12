---
title: "partition PROBLEM!"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by grannyw on 2008-03-29
when i was installing ubuntu,i made additional partition by mistake,and now when i'm using ubuntu after installation the computer dont see it.so i just lost 50G

pls help

---

### Post by nsche on 2008-03-29
You probably need to use something like cfdisk (sudo cfdisk) and set the type of the partition to ext2 or ext3.  You can then make a file system (sudo mke2fs).  After this you should be able to mount it and use it.  Be very careful as you can really screw things up doing this.  An easier approach if you haven't done much with your system is to redo the system installation.

---

### Post by JK21 on 2008-03-29
> **grannyw said:**
> when i was installing ubuntu,i made additional partition by mistake,and now when i'm using ubuntu after installation the computer dont see it.so i just lost 50G

pls help

Just download the GPartEd-live iso and burn it to cd. After rebooting your 'problem-computer' with this cd you can virtually do anything with any partition that you want to be changed...

Info&download: [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

Suc6!

---

### Post by mrsteveman1 on 2008-03-29
fdisk and cfdisk are really for low level stuff, if you use parted or gparted they will set the partition ID for you automatically when you format with a specific filesystem.

Definitely use gparted or a livecd tho

---

### Post by pieisgood4589 on 2008-03-29
You could use GParted and delete that partition leaving a blank empty spot, restart, and resize your Linux partition so that it fills up that spot, then restart. :popcorn:

---

### Post by grannyw on 2008-03-31
<SOLVED>thank u everybody.the problem solved

---

