---
title: "Formating in Ubuntu"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by chaereth on 2007-06-15
How do I format on ubuntu?

I messed up and windows is gone now, I want split partition into 2 and make clean installs of ubuntu and windows on them.

---

### Post by freebird54 on 2007-06-15
If you are installing from a Live CD, this is pretty easy.  

Boot up off the Live CD.

Select System->Administration->Gnome Partition Editor.

Delete existing partitions.

If you want (to save time later) create the new partitions.  Assuming XP, make an XP partition the size you want - and format NTFS.  Make a Linuxswap partition and format that as swap.  Make a Linux partition and format ext3.

shutdown, remove Live CD

insert Win CD, and install Windows.

If you have any patience left - install Ubuntu :)  It will pick up the fact that Windows is there and automatically enable access to Windows, and to its partition.

Enjoy!

---

