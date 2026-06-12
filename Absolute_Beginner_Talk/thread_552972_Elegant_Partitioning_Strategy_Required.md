---
title: "Elegant Partitioning Strategy Required"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by theboxseat on 2007-09-17
Hi Guys this is my first post on this most excelllent forum :)

I have long wanted to migrate to Linux ( for all the usual reasons ) and I have decided to use Ubuntu (Primarily because of the Ubuntu Philosophy) I am not quite ready to become a heavy user of VMware and still will want to run Windoze, as I work from home.

Using windoze, I have always kept my data separate from the O.S; relying on ghost 2003 to backup the OS to a separate NTFS partition.

I am wanting each OS to be installed in isolation (hidden on primaries) with the each bootloader being installed onto the O.S. system partion.

The IPL in the MBR will be occupied by OSL2000 bootloader.

So none of my operating systems will see each other.

I have 2 GB DDR800 ram and 2 160GB SATA drives.

To prevent screwups, I am intending the first HDD to be only for O.S, split into 4 primaries;

On HDD1:

[INDENT][LIST=1]
[*]DOS
[*]XP 64
[*]XP 32
[*]Linux
[/LIST][/INDENT]

I will want to give Linux plenty of room as I will be learning the applications of VM ware. At this stage, please don't diss me for the windoze requirements.

On HDD2:

[INDENT][LIST]
[*]Windoze Swap
[*]Linux Swap
[*]Linux Home Partition
[*]Ghost Partion          20GB
[*]Linux system partion ???
[*]Downloads:             20 GB
[*]Apps  - M$:             30GB
[*]Games - M$:            25GB
[*]Video                       10GB
[*]Data                        10GB
[/LIST][/INDENT]

I believe that there are applications that allow Linux and Windoze to access NTFS and Ext3 partitions repspectively. Can this be confirmed, because it is very important.


As you can see I am reasonably clear in what I want to end up with, I am just unsure how to get there!

In particular:
[LIST]
[*]If the above strategy is optimal
[*]The formats for each partition
[*]The location of each partition
[/LIST]

I have spent ages doing searches, but have been unable to resolve without help from you guys

Thanks in advance

---

### Post by Spike-X on 2007-09-17
Although I don't have all the answers, I can help you with a couple of things.

> **theboxseat said:**
> At this stage, please don't diss me for the windoze requirements.

Nobody's gonna do that. A lot of us are still dual-booting for various reasons.

> **theboxseat said:**
> I believe that there are applications that allow Linux and Windoze to access NTFS and Ext3 partitions respectively. Can this be confirmed, because it is very important.


Yes, there are.

Here's how I have my HDs set up, if it's any help:

HD #1 (boot drive) partitioned as follows -

hda1: WinXP install & apps + swap NTFS (not sure if it's possible to install Windows swap on a separate partition, I've never tried)
hda2: Ubuntu install ext3
hda3: Ubuntu /home ext3
hda4: linux-swap

Keeping your /home on a separate partition is a good idea so that when you need to reinstall/upgrade, you keep all your documents and settings, fonts, config files for various apps, etc.

I also have two dedicated storage drives, both NTFS. Files written under Ubuntu can be read by Windows and vice versa.

---

### Post by Steve1961 on 2007-09-17
> I believe that there are applications that allow Linux and Windoze to access NTFS and Ext3 partitions repspectively. Can this be confirmed, because it is very important.

Yes, there are drivers that allow rw to ntfs from linux and rw from windows to ext3.  Without these drivers you can still acess ntfs from linux, but you can't write to it.  

I'm not sure about how optimal your setup is, although it's probably a good idea to have a separate home partition.  The rest is about personal choice, and I tend to just use a single partition for / and a single swap partition.  Personally I also use fat32 partitions for sharing data between windows and linux as both read and write to it without an issue, and it doesn't require any special setting up - the only downside being the 4gb file size limit, although I can't say that really affects me.

> (not sure if it's possible to install Windows swap on a separate partition, I've never tried)

It is and it tends to be more efficient

here's my setup just for reference:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10443    83883366    7  HPFS/NTFS
/dev/sda2           10444       19929    76196295    f  W95 Ext'd (LBA)       - sda contains XP and a fat32 data partition
/dev/sda5           10444       19929    76196263+   b  W95 FAT32

Disk /dev/sdb: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4665    37471581   83  Linux
/dev/sdb2            4666        4870     1646662+   5  Extended     -sdb contains Ubuntu / partitions and swap partition
/dev/sdb5            4666        4870     1646631   82  Linux swap / Solaris

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
16 heads, 63 sectors/track, 155061 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       52014    26215024+  83  Linux
/dev/sdc2           52015       55207     1609272    5  Extended   -sdc contains Debian /, swap, and Vista partition
/dev/sdc3           55208      155061    50326416    7  HPFS/NTFS
/dev/sdc5           52015       55207     1609240+  82  Linux swap / Solaris

---

### Post by antoz on 2007-09-17
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

