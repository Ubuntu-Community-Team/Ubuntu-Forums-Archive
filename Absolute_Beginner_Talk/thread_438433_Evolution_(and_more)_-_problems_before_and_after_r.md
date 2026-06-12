---
title: "Evolution (and more) - problems before and after repartition"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by kevmartin on 2007-05-09
Something weird going on for me and I can't figure it out, so here's the symptoms.

My machine is dual boot XP and Feisty.  Running well until recently when Evolution started failing to complete its startup.  It seemed to get part way through synchronising mail and then stop.  After failed experiments trying to use Thunderbird (it didnt recognise Evolution as somewhere to import from as far as I could tell), I thought I would take a backup of my mail folders for safety's sake before messing around further.  That's when I noticed one of my mail folders is 1Gb+ in size but there was only 500Mb+ room left on the Linux partition.  The partition was 30Gb, but 20Gb is setup as a virtualbox - supposedly it only uses the space it needs and grows accordingly, so I'm not sure why it would be using so much space.

Anyway, since I had plenty of spare space on my XP and DATA partitions, I decided to resize my partitions.  I downloaded GParted livecd, and successfully added another 25Gb to my linux partition.  The process shuffled my drive letters around in windows which freaked me out until I found out that my data drive wasn't lost, it had just changed from E: to D:

But in Linux, things are not quite right.

Opening Places/Computer - all entries are listed with "desktop configuration file unknown"
Evolution - now gets 87% of the way through the synchronise instead of about 50% - then gets stuck
Drive space - opening /home shows 23.7Gb drive space free, but opening sda3 (previously my main Linux partition) shows 1.9Gb spare space and seems to be the Dell System Restore partition.

I'm very confused - can anyone help please?

---

### Post by kevmartin on 2007-05-09
I thought this might help - now I'm definitely thinking there will be an easy fix - for someone who knows how

FDISK:
> Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7       10205    81923467+   7  HPFS/NTFS
/dev/sda3           29788       30393     4867695   db  CP/M / CTOS / ...
/dev/sda4           10206       29787   157292415    f  W95 Ext'd (LBA)
/dev/sda5           10206       22672   100141146    b  W95 FAT32
/dev/sda6           22673       22736      514048+  82  Linux swap / Solaris
/dev/sda7           22737       29787    56637126   83  Linux

Partition table entries are not in disk order

Disk /dev/sdf: 82.3 GB, 82348278272 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1       10011    80413326    b  W95 FAT32

Disk /dev/sdg: 132 MB, 132251648 bytes
8 heads, 32 sectors/track, 1009 cylinders
Units = cylinders of 256 * 512 = 131072 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *           1        1009      129136    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(1023, 7, 32) logical=(1008, 7, 32)


FSTAB:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7 -- converted during upgrade to edgy
UUID=e02c22a8-12fc-458a-b18d-b16bf2fddc97 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda1 -- converted during upgrade to edgy
UUID=07D6-010B /media/sda1 vfat defaults,utf8,umask=007,gid=46 0 0
# /dev/sda2 -- converted during upgrade to edgy
UUID=1CF82850F8282B0A /media/sda2 ntfs-3g defaults,nls=utf8,umask=007,gid=46 0 0
/dev/sda3       /media/sda3     vfat    defaults,utf8,umask=007,gid=46 0       0
# /dev/sda5 -- converted during upgrade to edgy
UUID=191B-4887 /media/sda5 vfat defaults,utf8,umask=007,gid=46 0 0
# /dev/sda6 -- converted during upgrade to edgy
UUID=a2bc5abb-b7b6-4418-b2f8-c481766fc81e none swap sw 0 0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
none /proc/bus/usb usbfs devgid=1002,devmode=664 0 0


---

### Post by kevmartin on 2007-05-11
Well my Evolution fixed itself (mostly) after I gave it all the extra disk space to play with, as I had hoped - it just took another boot or two to manage it.

However, I still see the problem opening Places/Computer:  all entries are listed with "desktop configuration file unknown"

Ive tried googling as well as ubuntuforums - found one other person with the problem, but no solutions.  Surely it has to relate to the changed partition names since the change of partition sizes - but how to fix it?

ANy help greatly appreciated. Thanks.

---

