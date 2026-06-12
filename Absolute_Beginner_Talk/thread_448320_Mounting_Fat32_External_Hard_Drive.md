---
title: "Mounting Fat32 External Hard Drive?"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by Cre-ve on 2007-05-19
I have installed Feisty on my IDE hard drive (which is a slave to the master SATA Hard Drive). Everyone works great..except for one thing.

I have an external Hard Drive which is in the FAT32 format. For some reason, I am unable to access this hard Drive in feisty. In Edgy it was auto detected and would show up on the desktop. This dosen't happen for Fiesty for some reason.

Anyone know how i can get the drive to show up? 

here is what i get when i do sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
240 heads, 63 sectors/track, 32301 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       31080   234964768+   7  HPFS/NTFS
/dev/sda2           31081       32301     9230760    c  W95 FAT32 (LBA)

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       29265   235071081   83  Linux
/dev/hdb2           29266       30401     9124920    5  Extended
/dev/hdb5           29266       30401     9124888+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30401   244196001    c  W95 FAT32 (LBA)


Its the Last one.

Thanks for anyone that is able to help me out with it.

---

### Post by tchoklat on 2007-05-19
you may need to edit your fstab to mount it
do a search for 'edit fstab' for instructions about mounting  drives

---

### Post by Inxsible on 2007-05-19
since it is an external drive, mount it using pmount and unmount it using pumount.

Also do NOT put entries in the fstab, because it will give you errors if you try to boot without connecting the drive.

Note that, when mounting an external drive using pmount, it needs to create a new location. It won't allow you to mount to an existing location
```

pmount <device> <NAME>

eg. pmount /media/external MyDrive

```

---

### Post by Cre-ve on 2007-05-19
i tired pmount but i couldn't get it to work. after i typed in pmount and the rest it gave me details on how to use pmount...not helpful.

i tried regular mount..and then it gave me something very interesting

mount /dev/sda1
mount: according to mtab, /dev/sda1 is already mounted on /media/HP_PAVILION
mount failed

so apparently its already mounted in the other hard drive? how do i access that?

---

### Post by Inxsible on 2007-05-19
Try this link :

This is what helped me with my external disks

[http://doc.gwos.org/index.php/Understanding_fstab](http://doc.gwos.org/index.php/Understanding_fstab)

---

### Post by Cre-ve on 2007-05-19
thanks guys i got it to work.

pmount actually worked and that link that the last individual gave me clarified it clearly. thanks :) appreciate it.

i did pmount /dev/sdb1 segate 

and it showed up on my desktop.

---

### Post by Inxsible on 2007-05-19
Glad you got it working !!

---

### Post by Cre-ve on 2007-05-19
here is another tool to help people out..very very good website and easy to do...check it out:


[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

---

### Post by mgmiller on 2007-05-19
This is just what I was looking for.  :lolflag:
I have 3 external USB HDD.  2 I built my self and formatted fat32.  These work as expected, plug in, turn on, automounted and appear on desktop.  The 1 drive I purchased is a Seagate model ST3160026ARK, also formatted fat32.  It will not automount.  It is seen by the system as /dev/sdg in fdisk -l.  So the pmount and pumount commands worked a treat!

---

