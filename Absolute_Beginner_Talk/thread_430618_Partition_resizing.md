---
title: "Partition resizing"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by Linux_n00b on 2007-05-02
I have 4 partitions on my system:

1)  16 MB FAT
2)  23.44 GB NTFS
3)  3.7 GB Linux Ext3
4)  784.4 MB Linux Swap

I would like to resize the the 23.44 gb partition and add onto the 3.7 GB Linux Ext3 partition.  I tried using Patition Magic, but when I make unallocated space it does not allow me to add it to my Linux Ext3 parition.  I also tried to boot with Edgy Eft and use GPARTED but that also gave me an error when trying to resize the partition.  Anybody know what I can do to make this work?  Any help would be greatly appreciated.  Thanks!

](*,)

---

### Post by taurus on 2007-05-02
You need to use gparted from the LiveCD for that task since you will be adjusting the size of Ubuntu.  Can't resize Ubuntu partition while you are using it.  That's why you got an error from gparted.  And avoid partition magic at all cost because it doesn't go well with Linux.

---

### Post by Billy McCann on 2007-05-02
get the GParted LiveCD. 

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by az on 2007-05-02
> **Linux_n00b said:**
> I have 4 partitions on my system:

1)  16 MB FAT
2)  23.44 GB NTFS
3)  3.7 GB Linux Ext3
4)  784.4 MB Linux Swap

I would like to resize the the 23.44 gb partition and add onto the 3.7 GB Linux Ext3 partition.  I tried using Patition Magic, but when I make unallocated space it does not allow me to add it to my Linux Ext3 parition.  I also tried to boot with Edgy Eft and use GPARTED but that also gave me an error when trying to resize the partition.  Anybody know what I can do to make this work?  Any help would be greatly appreciated.  Thanks!

](*,)

You will need to resize the 23.4 Gig partition to make room to fir the whole 3.7 gig partition which comes after it.  You will need to copy the 3.7 gig partition to the beginning of the free space, then delete the original, then extend the free space.

Partition magic would be able to do it if it worked properly with ext3 filesystems.  Parted can only resize partitions from the end, not the beginning.  That's why you have to copy it first.

---

### Post by Linux_n00b on 2007-05-02
:)  GParted LiveCD did the trick!! Thanks everybody!! :)

---

