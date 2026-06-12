---
title: "Lvm"
date: 2013-05-04
forum: Any Other OS
---

### Post by nholloway2007 on 2013-05-04
I'm currently dual boooting Ubuntu 13.04 and Windows 8. I say that to say, I tried to overwrite my Ubuntu partition (12.10 at the time) with Fedora 18. Sadly, it refused to install with my previously existing Windows partition, so I erased it and it installed correctly, as automatic partitioning kicked in and overwrote the entire drive. I tried to boot a Gparted LiveUSB in order to resize the parttion so I could restore my Windows image, but...couldn't resize it, because it was an LVM volume. So I overwrote it with Ubuntu 13.04, resized it in Gparted, and reinstalled Windows. So, my question is this: What does LVM do, why would I use it, why does it prevent Gparted from resizing an LVM partition, and what will allow an LVM partition to be resized?


Thanks!

---

### Post by DarkSwordmaster on 2013-05-04
I'll try to answer the questions in a simple way.
-Basically the LVM is the administrator of logical partitions; it allows to make those unlimited logical partitions by creating one extended primary partition.
-You use it every time you create a logical partition because it is the thing that allows you to make them, make the extended partition and avoid any issue with a windows shared boot. If you only use linux distros you can have as many primary as you want, but when you are sharing boot with windows you can only use 4 primary partitions or windows won't run; there comes the magic of the LVM.
-Gparted can't resize it because the extended partition already has a limited amount of space used that is divided in more spaces in it. The only way you can resize it is by erasing it and making a new set of partitions in that empty space.
-You can only resize an LVM managed partition by doing what I said in the third point as far as I know. Erasing the extended and making a new set.

Just to clarify: LVM is not a disc format, it is only the logical partitions administrator.

---

### Post by Cheesemill on 2013-05-05
There is a good guide to LVM on the #! forums...

[http://crunchbang.org/forums/viewtopic.php?id=19411](http://crunchbang.org/forums/viewtopic.php?id=19411)

---

