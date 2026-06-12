---
title: "need help mounting second hdd"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by firedancer on 2007-09-01
Hi , the second has a vfat partitions which contains some data i need to back-up and then i can use it how i want 



i tried mounting the partition , but i did something wrong 


after fdisking a few times now it looks like this  
Disk /dev/sda: 40.0 GB, 40016019456 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4660    37431418+  83  Linux
/dev/sda2            4661        4865     1646662+   5  Extended
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *         784        2358    12651187+  83  Linux
/dev/sdb2             386         783     3196935    b  W95 FAT32
/dev/sdb3            2359        2434      610470    5  Extended
/dev/sdb5            2359        2434      610438+  82  Linux swap / Solaris

Partition table entries are not in disk order


so sow it shows me this  (above)  after adding sdb1 as the vfat partition  
so i changed it (below) , but i'm getting an error


 dmesg | tail
[   52.651680] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   52.652217] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[   52.652741] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[   52.914841] NET: Registered protocol family 10
[   52.915008] lo: Disabled Privacy Extensions
[   52.915102] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   53.087863] [drm] Setting GART location based on new memory map
[   53.088414] [drm] writeback test succeeded in 1 usecs
[  714.800729] FAT: invalid media value (0xf6)
[  714.800878] VFS: Can't find a valid FAT filesystem on dev sdb2.





this needs to be fixed , 



 /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=5ff359cc-bd13-44ab-a5a9-4885f2cd7278 /               ext3    defaults,erro$
# /dev/sda5
UUID=a881e468-b115-4f0f-b0f7-089ded561932 none            swap    sw           $
/dev/sdb2       /fat_files      vfat auto,umask=000 0    0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0



well , i can't do it :(   

can anyone guide me 

would be appreciated :)

---

### Post by firedancer on 2007-09-01
well now  sdb1 is mounted, 

i guess i have to add it to my fstab in order for it to mount at bootup
can anyone tell me the rite way to do this , don't wanna mess up constantly , just need to learn once


and for my vfat partition , i need to back up the data , 

got it from someone , im can keep the hdd , but the person needs what's on it .    

and i don't have windows anymore , actually i tried booting the hdd with fat32 partition, but that didn't go , so i 'm not sure wether it still is good  or whatever

---

### Post by Arwen on 2007-09-01
All of your partitions in sda,sdb aren't in your fstab,you have sda1,sda2,sda5,sdb1,sdb2,sdb3,sdb5 are all of them right?Cause in your fstab you only have sda1,sda5,sdb2.Your new vfat is sdb2,isn't it?

---

### Post by Arwen on 2007-09-01
A useful link someone gave me in this forum:[here]("http://ubuntuforums.org/showthread.php?t=283131")

This is what I have in my fstab for a vfat partition:
/dev/sda3 /media/sda3 vfat  iocharset=utf8,umask=000  0    0

---

### Post by firedancer on 2007-09-01
ok first i had that , but it didn't mount , then suddenly , sdb1 mounted by itself , i didn't create it either , so i'm not hoping that i'm messing up my fstab


do i have to unmount it , mkdir , etc.. then add it to my fstab , 

ok i'll try the link

---

### Post by firedancer on 2007-09-01
thanks for the link :popcorn:




nicely solved !

---

