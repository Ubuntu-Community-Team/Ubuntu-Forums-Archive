---
title: "Moving partitions?"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by thedon_1 on 2008-01-16
I am trying to set up a vista linux dual boot system. I want one partition for each OS, then a big partition where i will store my files.

I have installed Ubuntu and it's all good.

I then shrunk each of the Os partitions but now in G parted it shows the unallocated space in blocks around the OS partitions.

How can i move the OS partitions so that the unallocated space is all together?


Thanks

---

### Post by bodhi.zazen on 2008-01-16
gparted will do it for you 

You need to boot a live CD. If you can not do it from the CD you have, you need a more recent version of gparted.

Either download Ubuntu 7.10 or the gparted live CD.

You should be prepared to edit /boot/grub/menu.lst and /etc/fstab , however, if your partition numbering changes.

---

### Post by thedon_1 on 2008-01-16
I have Gparted on rigt now from the livecd. I just have no idea how to move the partitions.

I used Move/resize to resize them, but don't know how to move them

---

### Post by bodhi.zazen on 2008-01-16
What live CD ? What version of Ubuntu ?

[http://gparted.sourceforge.net/larry/move/move.htm](http://gparted.sourceforge.net/larry/move/move.htm)

---

### Post by thedon_1 on 2008-01-16
Ubuntu 7.1 livecd.

I start it up and then go to system, admin, then partition manager.

I read the link you gave, but it involves moving to another hard drive.

I want to move the partitions so they are ordered properly on my hard drive

---

### Post by bodhi.zazen on 2008-01-16
same  procedure regardless of destination (single vs dual drive)

---

