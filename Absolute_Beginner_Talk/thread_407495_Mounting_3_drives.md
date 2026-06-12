---
title: "Mounting 3 drives"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by garyed on 2007-04-12
I have 3 HD's , 1 ide CD & 1 SCSI cd
Until reading the posts I assumed I wasn't supposed to be able to see my Windows drives  in Linux. Right now I can only view the Linux partition.
I've read some of the online turorials about mounting HD's but I'm still a little confused.  
Can someone explain what these lines in fstab mean & what they should read in order to view my drives. 
I assume by the results of fdisk that Edgy knows all my drives are present.  


Results of fstab =

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb2
UUID=d2e3c25d-b6ea-4564-b0bf-248d0f5acc67 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=d575235f-ff00-4195-8256-2ca76d20ec51 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
~
~
~


results of fdisk -l =


Disk /dev/hda: 8455 MB, 8455200768 bytes
255 heads, 63 sectors/track, 1027 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1027     8249346    c  W95 FAT32 (LBA)

Disk /dev/hdb: 30.7 GB, 30738677760 bytes
255 heads, 63 sectors/track, 3737 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        2311    18563076    c  W95 FAT32 (LBA)
/dev/hdb2   *        2312        3674    10948297+  83  Linux
/dev/hdb3            3675        3737      506047+   5  Extended
/dev/hdb5            3675        3737      506016   82  Linux swap / Solaris

Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1        9729    78148161    c  W95 FAT32 (LBA)

---

### Post by jhenager on 2007-04-12
An easy way to see your Windows drive is with diskmounter, 
[https://help.ubuntu.com/community/AutomaticallyMountPartitions#head-f59428cd4d1c1b020a3a06bae2242b3d7f45a06d](https://help.ubuntu.com/community/AutomaticallyMountPartitions#head-f59428cd4d1c1b020a3a06bae2242b3d7f45a06d)
or you can follow this guide.
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by george29 on 2007-04-12
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

should have all the info you need to mount your drives 


[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html) is a more in depth look at /fstab.

---

### Post by aberry5555 on 2007-04-12
ok, the lines in fstab are simply used to tell Linux what part of a hard-drive to use and where to put it in the system. so, for instance, if you wanted to mount your FAT32 partition in to your hard-drive you would choose a folder you want to be able to see it in (say /FAT i.e. a folder called FAT which is viewable at the very top of the hard-drive) you would type in the following:

firstly you would make the folder (case-sensitive) called FAT in your hard-drive, then you would open fstab and add, at the bottom;

```
/dev/hdb1 vfat /FAT
```

---

### Post by garyed on 2007-04-12
Thanks for the help.
Things are making a little more sense now.
I haven't got it yet but I think I'm close. I hope <g>

---

### Post by garyed on 2007-04-12
Okay, Now I can only read my hdc1(80 gig) drive.
All 3 windows drives show up on the destop now with thew correct Label but they all end up being my 3rd drive(80 gig) when I try to access them or check the properties. I assume I've got a number wrong in fstab.
Anyone know what I did wrong. 
 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb2
UUID=d2e3c25d-b6ea-4564-b0bf-248d0f5acc67 /               ext3    defaults,error
s=remount-ro 0       1
# /dev/hdb5
UUID=d575235f-ff00-4195-8256-2ca76d20ec51 none            swap    sw            
  0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1    /media/windows vfat  iocharset=utf8,umask=000  0    0
/dev/hdb1    /media/windows vfat  iocharset=utf8,umask=000  0    0
/dev/hdc1    /media/windows vfat  iocharset=utf8,umask=000  0    0

/etc/fstab (END)

---

### Post by taurus on 2007-04-12
> **garyed said:**
> Okay, Now I can only read my hdc1(80 gig) drive.
All 3 windows drives show up on the destop now with thew correct Label but they all end up being my 3rd drive(80 gig) when I try to access them or check the properties. I assume I've got a number wrong in fstab.
Anyone know what I did wrong. 
 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb2
UUID=d2e3c25d-b6ea-4564-b0bf-248d0f5acc67 /               ext3    defaults,error
s=remount-ro 0       1
# /dev/hdb5
UUID=d575235f-ff00-4195-8256-2ca76d20ec51 none            swap    sw            
  0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1    /media/windows vfat  iocharset=utf8,umask=000  0    0
/dev/hdb1    /media/windows vfat  iocharset=utf8,umask=000  0    0
/dev/hdc1    /media/windows vfat  iocharset=utf8,umask=000  0    0

/etc/fstab (END)

You need to mount your partitions at different mount points, not the same one for all three partitions.

```

/dev/hda1    /media/hda1  vfat  iocharset=utf8,umask=000  0    0
/dev/hdb1    /media/hdb1  vfat  iocharset=utf8,umask=000  0    0
/dev/hdc1    /media/hdc1  vfat  iocharset=utf8,umask=000  0    0

```
Then, create those three new mount points and reboot your machine.

```
sudo mkdir /media/hda1 /media/hdb1 /media/hdc1
```

---

### Post by justleen on 2007-04-12
you mount them all on the same directory.../media/windows 

create seperate dirs in /media, and place the name of those dirs in fstab.

---

### Post by garyed on 2007-04-12
It worked!!!!!!!!!!!
Thanks to everybody.

---

