---
title: "[SOLVED] Force drives to mount on system start up"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by Colemanvt on 2008-01-16
ok I know there are a lot of threads up for the same type of problem but I still can't get any relief.

I have 3 external hard drives and 2 internal drives

Gutsy is on one of the internal drives.

2 of the externals were online when I installed Gutsy and they show up everytime I boot up

The other is an external sata that only mounts if I double click and give my root password.

Same situation with my other internal hard drive.

I don't know what else to say it would be greatly appreciated if someone could shine some light on this problem.

my fstab currently looks like so...
[PHP]
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=c046bed3-90f3-4bd3-8b52-9be1eb09e81b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=96cd73a0-6e98-4f85-8e80-26d0d30ea9a9 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
[/PHP]

---

### Post by thelatinist on 2008-01-16
Please post the output of the following command:

```
sudo fdisk -l
```

That's a lowercase L, not the numeral 1.

---

### Post by Colemanvt on 2008-01-16
[PHP]colemanvt@ubuntudesk:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b6b59

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdb: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00550055

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4985    40041981    7  HPFS/NTFS
/dev/sdb2            4986        8866    31174132+  83  Linux
/dev/sdb3            8867        9039     1389622+   5  Extended
/dev/sdb5            8867        9039     1389591   82  Linux swap / Solaris

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00900090

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       24321   195358401    7  HPFS/NTFS

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc485c485

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       30401   244196001    7  HPFS/NTFS

Disk /dev/sde: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd4f70547

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1       36483   293049666    7  HPFS/NTFS
[/PHP]

Yeah sorry about that I don't know why i didn't to begin with >_< I'm a 2 month old ubuntu newblet don't hate to hard :-D

---

### Post by thelatinist on 2008-01-16
Well, you need to add lines in fstab for each of the partitions on your internal hard drive that you want mounted automatically.

1) Use the following command to create a mount point for this drive (change *mountpoint* to a name that is not already in use and will be easy to recognize and remember):

```
sudo mkdir /media/*mountpoint*
```

2) Use the following command to back a back up of your fstab file in case something goes wrong:

```
sudo cp /etc/fstab /etc/fstab.bak
```

3) Use the following command to open fstab for editing:

```
sudo gedit /etc/fstab
```

Add one of the following line (depending on filesystem type) to your fstab to cause it to automatically mount (replace *sda#* with the name of the device you wish to mount and *mountpoint* with the mountpoint you created in step 1):

**For ext3:**
```

/dev/*sda#* /media/*mountpoint* ext3 defaults,errors=remount-ro 0 1
```

**For NTFS:**
```
/dev/*sda#* /media/*mountpoint* ntfs-3g defaults,nls=utf8,umask222 0 0
```

**For Fat32 or Fat16:**
```
/dev/*sda#* /media/*mountpoint* vfat user,utf8,fmask=0111,dmask=0000 0 0
```

**For reiserfs:**
```
/dev/*sda#* /media/*mountpoint* reiserfs nodev,nosuid 0 0
```

Things are more problematical for the external hard drives, because they may not always be there (and because their device name may change).  Do you know which device isn't getting mounted automatically?

Off-topic: it's customary to use the [CODE] tag when posting terminal commands, etc., rather than the [PHP] tag.  It's the # button.

---

### Post by Colemanvt on 2008-01-16
Cool thanks so much I'm going to write all that down :-D

I got the internal to mount up quite nicely but the external didn't feel like it but that's ok I don't guess I need that one up on boot up just mainly the internal.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=c046bed3-90f3-4bd3-8b52-9be1eb09e81b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=96cd73a0-6e98-4f85-8e80-26d0d30ea9a9 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sda1 /media/500GB_irock ntfs-3g defaults,nls=utf8,umask222 0 0
/dev/sdc1 /media/200GB_WD ntfs-3g defaults,nls=utf8,umask222 0 0
```

That's what my fstab looks like now I added the bottom two lines and did a mkdir for both of the mountpoints of course. think there's possibly anything I did wrong?

SECOND EDIT: Scratch that I'm a moron I made the folder 500GB_Irock and put in the fstab irock. Linux and it's damn case sensitivity! So all is perfect now thanks thelatinist that was a great little how to you threw at me

---

### Post by thelatinist on 2008-01-17
Glad I could help!  Don't forget to mark this thread [Solved] using the thread tools.  Happy Ubuntu-ing.

---

