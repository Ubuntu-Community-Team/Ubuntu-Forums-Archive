---
title: "[SOLVED] AAAArghhh Please help with mounting drives"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by hogwartsnigel on 2007-11-25
Hi here is my sudo fdisk -l print out

[I]Disk /dev/hda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1695d55b

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1            7687        8961    10241437+  82  Linux swap / Solaris
/dev/hda2           29708       38913    73947195    f  W95 Ext'd (LBA)
/dev/hda3   *        3825        7686    31021515   83  Linux
/dev/hda4            8962       29707   166642245   83  Linux
/dev/hda5           29708       38913    73947163+  83  Linux

Partition table entries are not in disk order

Disk /dev/hdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x01206277

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       30515   245111706   83  Linux

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00006a32

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14593   117218241   83  Linux

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0bc4063e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241    f  W95 Ext'd (LBA)
/dev/sdb5               2       14593   117210208+   7  HPFS/NTFS

Disk /dev/sdc: 120.0 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x045a7c70

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       14596   117242338+  83  Linux

Disk /dev/sdd: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00094df4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       30515   245111706   83  Linux[/I]

I am having a nightmare getting the discs to write..I get the permissions error and most of the drives are owned by root...how can I change them.
Up to now I haven't lost data because of rigorous back ups onto a usb drive and one internal correctly mounted.
computer file browser I have the following listed

Floppy Drive                        (No Problems)
Cd-Rom/DVD-Rom Drive        (no Problems)
CD-RW/DVD+ RW Drive          (No Problems)
*111.8GB Volume: disk          (Cannot write too, owned by unknown) *
*233.8gb Volume: Disk1         (cannot write too, Owned by root usb) media ext3
*233.8Gb Volume (2): disk-2   (Cannot write too, owned by root) media/ext3
*70.5Gb Volume: Disk-3          (cannot write too, Owned by root) Media/
Archived                             (owned by me!!!! yIPPEE) 120gB usb ext 3)
Everything Else                    (owned By Me Yipppe!! 111.8gb NTFS)
File System                          (owned by root...thats ok thoug...LOL)


Gparted summarises with the following identified drives

**/dev/hda (298.09GiB)**    = /dev/hda3 29.58gb  (ext3 boot)      mountpoint /
                                     /dev/hda1 9.77gb    (linux Swap)    
                                     /dev/hda4 158.92gb (ext3              mountpoint /home
                                     /dev/hda2 70.52gb   (extended)     lba flag?
                                    /dev/hda5  70.52gb   (ext2)            mountpoint /media/disk-3

**/dev/hdb1 (233.76GiB)** =  /dev/hdb1 233.76gb (ext3)            Mointpoitnt /media/disk-2

**/dev/sda1  (111.79GiB**)= /dev/sda1 111.79gb  (ext2)            mointpoint /media/disk

**/dev/sdb5 (111.78GiB**)= /dev/sdb1 111.79gb  (extended)      lba flag???
                                   /dev/sdb5 111.78gb  (ntfs)             mointpoitnt / //media/Everything else
[B]
/dev/sdc1   (111.81GiB) =     [/B]/dev/sdc1 111.81gb    (ext3)      mountpoint /media/Archived

**/dev/sdd1  (233.76 GiB) =    **/dev/sdd1 233.76gb    (ext3)      mountpoint/ /media/disk-1

Please can someone give me a walk through of changing ownership / Permissions and names of these discs


Thanks


Nigel


P.S. Tried to be as thorough as I could
Each of the non writable drives have a padlock icon...symbolic and have a padlocked lost and found file in their contents

---

### Post by bluepowder7 on 2007-11-25
psychocats tells you how to flip into root mode and set permissions on all mounted drives.

[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by hogwartsnigel on 2007-11-25
Thanks Blue I'll give it a try tonight.

Wish me luck
Please check back to see how I get on

Nigel

---

### Post by hogwartsnigel on 2007-11-25
Blue,
Thanks mate all resolved...I've also got my homework sorted for the next while as this resource is ace.
Blessings Mate.
Ubuntu rocks....but I still prefer tea to coffee

Thanks Again Nigel

---

### Post by jcsteele on 2007-11-25
please mark the thread as SOLVED with the thread tools menu.

//jcs

---

