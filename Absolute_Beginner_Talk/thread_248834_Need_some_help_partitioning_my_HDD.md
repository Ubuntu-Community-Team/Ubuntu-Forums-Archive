---
title: "Need some help partitioning my HDD"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by fatsheep on 2006-09-01
I have downsized my Windows XP partition using the GPARTED live cd.  Now I have about 10 GBs of unallocated space that I need to allocate to my Ubuntu partition.  How do I do this?

---

### Post by bodhi.zazen on 2006-09-01
Just install Ubuntu, it will format and install.

BE CAREFULL with your windows partition. It is likely hda1.

---

### Post by fatsheep on 2006-09-01
> **bodhi.zazen said:**
> Just install Ubuntu, it will format and install.

BE CAREFULL with your windows partition. It is likely hda1.

I already have Ubuntu so I want to allocate the unallocated space to my current installation.  Is this possible?

---

### Post by PPAAUULL on 2006-09-01
Fatsheep, do you want to add to a current partition or install Ubuntu on the new free space?

---

### Post by PPAAUULL on 2006-09-01
You beat me to it. lol.

---

### Post by bodhi.zazen on 2006-09-01
> **fatsheep said:**
> I already have Ubuntu so I want to allocate the unallocated space to my current installation.  Is this possible?

Should be possible with GPARTED, no guarentees.

I would format it as a fat32 and use it (the free space) as a shared/data partition.

---

### Post by PPAAUULL on 2006-09-01
But there must be a way to add it too the current partition. It can't be a new idea.

---

### Post by fatsheep on 2006-09-01
When I right click on the unallocated space the only options are information (which does nothing) and "New" (which creates a new partition).  :-k

---

### Post by bodhi.zazen on 2006-09-01
You need to:
1.  Boot with the desktop CD (not from HD).

2. Unmount your hard drive.

3. Run GParted & re-size with the hard drive un-mounted:

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

---

### Post by PPAAUULL on 2006-09-01
What about in the menus, if you select the partition?

---

### Post by bodhi.zazen on 2006-09-01
Hi PPAAUULL

---

### Post by PPAAUULL on 2006-09-01
Found this in Gparted Wiki:
> GParted cannot increase the size of partitions "backwards." That is, it cannot move a partition left in the partition map to fill up empty space before it. It can only increase the partition to fill up empty space after it.

I hope that helps a bit.

---

### Post by fatsheep on 2006-09-01
#Trying to allocate 10 Gbs of unallocated space to Ubuntu partition.

- Booted GPARTED LiveCD successfully.
- Now I am going to try to unmount the HDD as per bodhi.zazen's suggestion:

> 
**umount dev/hdc**
umount:dev/hdc: not mounted


The hard drive is already unmounted.

-I open up the "Resize/Move" dialog for the Ubuntu partition.  The option to increase the size of the partition is grayed out.


> **PPAAUULL said:**
> What about in the menus, if you select the partition?

I've looked through the menus, haven't found anything... ](*,)

---

### Post by fatsheep on 2006-09-01
> **PPAAUULL said:**
> Found this in Gparted Wiki:


I hope that helps a bit.


Ah thanks for the info, I will try moving the Ubuntu partition over to the left of the unallocated space and then resizing.  :D

---

### Post by fatsheep on 2006-09-02
Well I got a boot grub error after repartitioning and had to edit the boot/grub/menu.lst file's partition coordinates for Ubuntu with my Live CD but everything works great now.  :D

---

