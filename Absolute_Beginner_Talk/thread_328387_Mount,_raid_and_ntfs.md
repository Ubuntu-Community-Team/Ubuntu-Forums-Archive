---
title: "Mount, raid and ntfs"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by technoplume on 2006-12-30
I there, I'm brand new to linux.

Ok I'm trying to have acces to some file I have on a 2nd HD. My Problem is that it's NTFS and frankly I'm not sure were to go to acces it. I have look in Places\computer\ were I can find 2 optical reader, one filesystem and one that is named 19.5 G. This is the drive were linux is installed.

When I try to get the System\Adm\disk open it just stay grey, nothing happen.

Then I tryed qtperted, wich detect no drive at all. It does tell me that it might be because i'm not using the root. ? this one I'm lost.

Then I tried the terminal, Cause after all the Gnome partition editor and Devise manage do see and list all my HD. In GPE I only have the unmount option ??

But, I fell a bit of fear. Here is why. I have keep windows xp on a different raid partition. Compose of 2 disk western digital of 40 G. Then I have an other IDE 60G maxtor, wich I want to acces and the last 40G Maxtor as the linux files on it.

here is what I get from the sudo fdisk -l

Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: invalid flag 0xffffe9f7 of partition table 5 will be corrected by w(rite)

Disk /dev/hde: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/hde2            2551        9731    57681382+   f  W95 Ext'd (LBA)
/dev/hde5   ?       38237      124303   691320229+  cc  Unknown

Disk /dev/hdf: 40.0 GB, 40020664320 bytes
16 heads, 63 sectors/track, 77545 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

Disk /dev/hdf doesn't contain a valid partition table

Disk /dev/hdc: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        4791    38483676   83  Linux
/dev/hdc2            4792        4998     1662727+   5  Extended
/dev/hdc5            4792        4998     1662696   82  Linux swap / Solaris

Disk /dev/hdd: 60.0 GB, 60040544256 bytes
255 heads, 63 sectors/track, 7299 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1        7299    58629186    7  HPFS/NTFS

So I open the terminal and followed this page:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
I added the line:
/dev/hdd1       /Files          ntfs    nls=utf8,unmask=0222 0 0
when I tried mount -a
I got :
mount: /dev/hdd1 already mounted or /Files busy
mount: according to mtab, /dev/hdd1 is mounted on /tmp/disks-conf-hdd1

So I went to take a look at the /tmp path. and it give me a error message that I'm not authorised to see the content.

I would also know if I can access my 2nd partition on my RAID setup ?

Woah that a lot !:(

---

