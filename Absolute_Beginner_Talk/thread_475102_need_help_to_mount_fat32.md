---
title: "need help to mount fat32"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by cgerb on 2007-06-15
I am total newb trying to get my head around ubuntu.  I have a dual boot system with xp and ubuntu.  1st hard drive has 3 partitions all fat32.  1st partition is xp.  The 2nd drive has 3 partitions also.  1st partition is ubunto and the other 2 is fat32.  The prob is i cant see any files on the fat32 partitions.  after reading around  i did the fdisk -l:

craig@craig-desktop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
16 heads, 63 sectors/track, 155061 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       51360    25885408+  82  Linux swap / Solaris
Partition 1 does not end on cylinder boundary.
/dev/hda2           51361      155055    52262280    f  W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.
/dev/hda3               1           1           0+  83  Linux
Partition 3 does not end on cylinder boundary.
/dev/hda4          155056      155056           0+  83  Linux
Partition 4 does not end on cylinder boundary.
/dev/hda5           51361      104040    26550688+   b  W95 FAT32
/dev/hda6          104041      155055    25711528+   b  W95 FAT32

Partition table entries are not in disk order

Disk /dev/hdb: 81.9 GB, 81964302336 bytes
16 heads, 63 sectors/track, 158816 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       47940    24161728+  83  Linux
Partition 1 does not end on cylinder boundary.
/dev/hdb2           49024      158802    55327860    f  W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.
/dev/hdb3           47941       49024      546210   82  Linux swap / Solaris
Partition 3 does not end on cylinder boundary.
/dev/hdb4               1           1           0+  83  Linux
Partition 4 does not end on cylinder boundary.
/dev/hdb5           49024      104088    27752256    b  W95 FAT32
/dev/hdb6          104088      158802    27575541    b  W95 FAT32

Partition table entries are not in disk order

i would like these to available automatically when i ever i boot ubuntu. 

If i need anything else let me knopw and i'll get it on here.  also i tried the disk manager but not sure if i was doing that right either.

Thanks in advance.

---

### Post by Happy_Man on 2007-06-15
Two things: could you also post the output of ```
cat /etc/fstab
``` and have you tried mounting them manually?

---

### Post by cgerb on 2007-06-15
Here is the fstab.

craig@craig-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by cgerb on 2007-06-15
I'll look around about the manual mounting.  Like i said i am a newb and trying not to get overwhelmed.
 Thanks for your reply

---

### Post by Bachstelze on 2007-06-15
You need to mount your partitions if you want to be able to access their contents. Do this

```
sudo mkdir /media/hdb5
sudo chown $(whoami) /media/hdb5
sudo mount -t vfat /dev/hdb5 /media/hdb5
```

and see how it works.

---

### Post by cgerb on 2007-06-15
YYYYEssss,  that worked.   I'll try the other partitions.  Now, after i mount these are they permanant.  meanig will they be mounted the next time i start ubuntu?

Great forum support.  Liking ubuntu more and more.

---

### Post by Bachstelze on 2007-06-15
No, these are not permanent, to make it so, you need to add a line about it in your fstab, like :

```
/dev/sdb5 /media/sdb5 vfat rw 0 0
```

---

### Post by cgerb on 2007-06-15
Hymn,  thanks alot.  i am all set i got 4 partitions mounted and in my fstab.  also found the psychocat tutorial on editing fstab.  
Great forum.  Thanks again

---

