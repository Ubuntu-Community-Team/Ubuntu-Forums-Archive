---
title: "help with gparted"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by frito on 2008-03-22
hi there i was wondering how i can format one of my logical partitions?

i am using gparted and when i format a partition linux automatically goes

"drive found" or something like that

and starts to use it!

how do I make this not happen?

---

### Post by Oldsoldier2003 on 2008-03-22
> **frito said:**
> hi there i was wondering how i can format one of my logical partitions?

i am using gparted and when i format a partition linux automatically goes

"drive found" or something like that

and starts to use it!

how do I make this not happen?

use a [GParted Live CD]("http://gparted-livecd.tuxfamily.org/") - you can't format a mounted partition

---

### Post by fmartinez on 2008-03-22
You can go command line as well..... try this: 
#sudo fdisk -l 
     This will give you list of mounted partions
#sudo umount /device/location
    This will unmount the device of your choice
#sudo cfdisk /device/location
    This is more interactive command util to edit or reformat partions
or #sudo fdisk /device/location
    This is a more command oriented 

REMEMBER TO BACK UP YOUR FILES FIRST AND BE VERY CAREFUL WHEN EDITING YOUR PARTIONS.... !!!! GOOD LUCK!

---

### Post by metalf8801 on 2008-03-22
heres a good live CD that has a few different programs on it for partitioning 
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

---

### Post by sandysandy on 2008-03-22
link to gparted tutorial

[http://howtoforge.com/partitioning_with_gparted](http://howtoforge.com/partitioning_with_gparted)

regards

---

### Post by frito on 2008-03-26
thanks everyone!

---

### Post by housam on 2008-03-26
here is all about partitions :[[COLOR="Red"]_http://www.linux.com/base/ldp/howto/Partition/index.htmlt_[/COLOR]]("http://www.linux.com/base/ldp/howto/Partition/index.htmlt")

---

