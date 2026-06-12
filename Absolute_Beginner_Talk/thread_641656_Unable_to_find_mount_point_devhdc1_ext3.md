---
title: "Unable to find mount point /dev/hdc1 ext3"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by warrior24 on 2007-12-15
I am new to ubuntu about 4 months and I noticed that my  /dev/hdc1  ext3 has this error. Should it look like this? 

I have read similar problems but I get lost on how to fix it.

[http://i66.photobucket.com/albums/h244/enterprisenxo1/Screenshot.png](http://i66.photobucket.com/albums/h244/enterprisenxo1/Screenshot.png)



adrian@adrian-desktop:~$ sudo fdisk -l
[sudo] password for adrian:

Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x24f024ef

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1        1006     8080663+  83  Linux
/dev/hdc2            1007        9728    70059465    f  W95 Ext'd (LBA)
/dev/hdc5            4973        6247    10241406    7  HPFS/NTFS
/dev/hdc6            6248        8159    15358108+   7  HPFS/NTFS
/dev/hdc7            8160        9728    12602961    7  HPFS/NTFS
/dev/hdc8            1008        1195     1510078+  82  Linux swap / Solaris
/dev/hdc9            1196        4972    30338721   83  Linux

Partition table entries are not in disk order

Disk /dev/sda: 519 MB, 519569408 bytes
255 heads, 63 sectors/track, 63 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00021a25

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          64      507360+   6  FAT16
Partition 1 has different physical/logical endings:
     phys=(62, 254, 63) logical=(63, 42, 43)
adrian@adrian-desktop:~$ 



# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=d5b95b91-e61a-4893-83b1-a7bc6ff8e45f       ext3     defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=1AA0957DA0956055 /media/hda6     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda6
UUID=CC4C9E524C9E36E4 /media/hda7     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda7
UUID=CEFCA586FCA56A03 /media/hda8     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda8
UUID=83b46589-641f-4132-bbf7-1d39e9139ed0 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

### Post by dcstar on 2007-12-15
> **warrior24 said:**
> I am new to ubuntu about 4 months and I noticed that my  /dev/hdc1  ext3 has this error. Should it look like this? 

I have read similar problems but I get lost on how to fix it.
.........
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
**UUID=d5b95b91-e61a-4893-83b1-a7bc6ff8e45f       ext3     defaults,errors=remount-ro 0       1**
# /dev/hda5
UUID=1AA0957DA0956055 /media/hda6     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda6
UUID=CC4C9E524C9E36E4 /media/hda7     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda7
UUID=CEFCA586FCA56A03 /media/hda8     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda8
UUID=83b46589-641f-4132-bbf7-1d39e9139ed0 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

In a terminal:

```
gksudo gedit /etc/fstab
```

and add in the "/" character:

```
UUID=d5b95b91-e61a-4893-83b1-a7bc6ff8e45f   **  / **      ext3 defaults,errors=remount-ro 0       1
```

---

### Post by warrior24 on 2007-12-15
Sweet worked like a charm I was stressing out over it. I contimplated reinstalling gutsy boy am I glad I didnt.   thanks a gazzillion times dcstar

I have two more questions 

if you notice in my screen shot my /dev/hdc9  ext3 is not auto mounted it was originnaly an ntfs but I formated it to ext3 to git rid of my ntfs but I have to mount it every time I want to use it. I tried sudo nautilus and changing the permissions but I still have to put in my password. Would it be safer to use as a fat for storing pictures.

Last question are there any good Ubuntu noob books that go in depth?

---

### Post by dcstar on 2007-12-15
> **warrior24 said:**
> Sweet worked like a charm I was stressing out over it. I contimplated reinstalling gutsy boy am I glad I didnt.   thanks a gazzillion times dcstar

I have two more questions 

if you notice in my screen shot my /dev/hdc9  ext3 is not auto mounted it was originnaly an ntfs but I formated it to ext3 to git rid of my ntfs but I have to mount it every time I want to use it. I tried sudo nautilus and changing the permissions but I still have to put in my password. Would it be safer to use as a fat for storing pictures.

Last question are there any good Ubuntu noob books that go in depth?

When you make changes to partitions post-install the UUID changes, you can either find the new UUID or just install the **pysdm** package and use it (System-Administration-Storage Device Manager) to mount your partitions.

I know there are some good Ubuntu books about, but I can't recommend any myself, best to go to Amazon.com and have a look at the user reviews for what is available now.

---

