---
title: "disk information"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by nishanthaMe on 2007-11-02
I have a SATA hard disk and I would like to know that in which file my hard disk information (size,used space) contains

---

### Post by oskar2000 on 2007-11-02
df -h
will show you the size and used space of all your partitions.
sudo fdisk -l
will show you the exact size of your drives.

Applications - Accessories - Disk Usage Analyzer
Will give you very detailed information on your disk usage.

---

### Post by laidback on 2007-11-02
Gparted gives a graphical view for all partitions. System>Gnome Partition Editor in 7.04, It's in that area of menus but called something else in 7.10.

---

### Post by SOULRiDER on 2007-11-02
You will most likely have to install gParted yourself,
```
sudo aptitude install gparted
```
or you can boot the live CD and use the one thats there, just remember, dont write to your disks :P

---

