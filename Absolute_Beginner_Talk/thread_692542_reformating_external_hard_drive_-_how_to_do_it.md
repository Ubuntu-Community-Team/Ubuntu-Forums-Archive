---
title: "reformating external hard drive - how to do it?"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by Gigidy5 on 2008-02-09
How in the world do i reformat a, maxtor one touch hard drive.




after typing      sudo fdisk -l     i getb this...






Disk /dev/sdb: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7296    58605088+   7  HPFS/NTFS





THANKS

---

### Post by asmoore82 on 2008-02-09
install and/or run GParted:
```
sudo apt-get install gparted
gksu gparted /dev/sdb
```
-OR-
you could do it the old fashioned way:```
cfdisk /dev/sdb
```
but cfdisk can only partition, not format;
so you would have to run the format tool for
the specific filesystem you want, GParted does that automagically.

---

### Post by Gigidy5 on 2008-02-09
heres what happens


[IMG]http://i202.photobucket.com/albums/aa315/gigidy5/Screenshot.png[/IMG]


now what?

thanks for the help!

---

### Post by boballen55 on 2008-02-09
Oh my god your poor eyes

---

### Post by newlinux on 2008-02-09
Format it  using gparted is next. you will need to unmount it first, I believe, which you can do from gparted.

---

### Post by Gigidy5 on 2008-02-09
thanks new

---

