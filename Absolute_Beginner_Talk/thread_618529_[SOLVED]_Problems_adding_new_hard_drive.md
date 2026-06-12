---
title: "[SOLVED] Problems adding new hard drive"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by jonnywombat on 2007-11-20
My machine has it's primary partition on an IDE HDD, but I had a spare sata device kicking around so I fitted it.

I followed the tutorial at [http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux) and all was good. The drive was mounted successfully, appeared on the desktop and I was able read and write to/from it.

My problems started after a reboot... The drive no longer showed up on my desk top.

Fdisk - l produces


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00090144

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19457   156288321   83  Linux

Disk /dev/hda: 120.0 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf959f959

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5226    41977813+   7  HPFS/NTFS
/dev/hda2            5358       14596    74212267+  83  Linux
/dev/hda4            5227        5357     1052257+  82  Linux swap / Solaris

Partition table entries are not in disk order

and  my   /etc/fstab reads....

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=cc80fcab-2f92-49e0-bfcf-0d0f4363af83 /               ext3    defaults,erro$
# /dev/hda1
UUID=7A18461D1845D931 /media/hda1     ntfs    defaults,umask=007,gid=46 0      $
# /dev/hda4
UUID=bbbd4f19-8e98-438a-81c4-61c36c542b82 none            swap    sw           $
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/sda1 /storage ext3 defaults 0 0


Both of which are as per the tutorial..

I am no expert with the terminal (in fact I suck), but I tried sudo mount /storage which produces

mount: /dev/sda1 already mounted or /storage busy
mount: according to mtab, /dev/sda1 is already mounted on /storage


When I had finished the tutorial the first time the additional drive showed up in the "places" sidebar of the file browser...

There is now a folder called storage under / within filesystem, which has the same contents which i transfered onto the sata drive, but a look at the properties show it is not the additional drive..

I have read through a number of threads but tbh nothing seems to make much sense to me. Any help in locating my missing drive greatly appreciated.

Jonny

---

### Post by MegaJim on 2007-11-20
"There is now a folder called storage under / within filesystem, which has the same contents which i transfered onto the sata drive, but a look at the properties show it is not the additional drive.."

That is because your fstab instructs mount to be at /storage, why do you not believe it is the same drive?

---

### Post by jonnywombat on 2007-11-20
Thanks for your reply
Ok thats my bad that is the correct drive (i misread the free space by a factor of 100gb oops).. 

However why is /storage now missing from the places sidebar in file browser.. and can I add it again?

---

