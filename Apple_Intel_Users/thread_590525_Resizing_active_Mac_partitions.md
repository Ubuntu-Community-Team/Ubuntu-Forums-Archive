---
title: "Resizing active Mac partitions"
date: 2007-10-24
forum: Apple Intel Users
---

### Post by Monsoonx27 on 2007-10-24
I formated my mac partition using boot camp, which you can only do the once.

Is it okay to resize the partition again using gparted or will it cause a loss of data.

---

### Post by cyberdork33 on 2007-10-24
> **Monsoonx27 said:**
> I formated my mac partition using boot camp, which you can only do the once.

Is it okay to resize the partition again using gparted or will it cause a loss of data.

Some people have issues after using gparted, but if you boot your OSX DVD after resizing the partition and run repairs, it should be OK.

---

### Post by Monsoonx27 on 2007-10-27
Gparted will let me resize and my ubuntu partitions but will not allow me to increase the size of my OSX partitions wiithout formating the drive with the live OSX cd. Any ideas?

---

### Post by cyberdork33 on 2007-10-27
> **Monsoonx27 said:**
> Gparted will let me resize and my ubuntu partitions but will not allow me to increase the size of my OSX partitions wiithout formating the drive with the live OSX cd. Any ideas?
gparted cannot grow hfs+ only shrink. there is no open source tool that i know of that can do this.

---

### Post by Monsoonx27 on 2007-10-28
Any non-open source software that will do this? 
Will boot camp in OSX 10.5 have this ability, I'm waiting on my free upgrade CD.

---

### Post by cyberdork33 on 2007-10-28
> **Monsoonx27 said:**
> Any non-open source software that will do this? 
Will boot camp in OSX 10.5 have this ability, I'm waiting on my free upgrade CD.

yes bootcamp can restore your hard drive, but it might be a roundabout process.
1. Use gparted to delete all your extra partitions (not OSX)
2. Bootcamp should allow you to make a windows partition, do that and make it asa small as possible. 
3.After you create the new partition, start bootcamp again, and it should give you the option to restore your OSX partition, and it will also include all the free empty space left over.

The diskutility in Leopard also has a nifty new feature that allows adding and subtracting partitions from the disk without repartitioning.

---

