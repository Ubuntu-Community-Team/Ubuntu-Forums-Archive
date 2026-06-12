---
title: "[SOLVED] Mounting problem"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by squirage on 2007-09-30
Hi

I'm running a dual HD system and installed Ubuntu on what is now called sdb. I mounted the Windows drive from the GUI but could not even see the remaining windows partition on the second drive.

I followed some how to's for a manual mount and get this message:

mount: wrong fs type, bad option, bad superblock on /dev/sdb5,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Running dmesg | tail gives:

[17183313.552000] NTFS-fs error (device sdb5): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17183313.552000] NTFS-fs error (device sdb5): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17183313.552000] NTFS-fs error (device sdb5): ntfs_fill_super(): Not an NTFS volume.

For some reason I can't fdisk right now, but it was showing up before.
Any thoughts?

System Specs
Toshiba Satellite A135-S4477
Dual Boot: Vista Home Premium (Longhorn)/ Ubuntu 6.10 (Edgy-Eft)
Intel® Core™ Duo 2 T5200 1.60GHz 1.60GHz
2048MB SDRAM PC4200 DDR2
180GB SATA HDD (80GB Primary + 100GB Secondary)
Mobile Intel® 945GM Express Chipset
Intel® Graphics Media Accelerator 950 with 8MB-256MB dynamically allocated shared graphics memory, v7.14.10.1132 (updated 8-6-07)
Matshita DVD-RAM UJ-850S ATA 

Thanks in advance.

---

### Post by pheeror on 2007-09-30
Are you really sure it's NTFS partition on /dev/sdb5 ? I bet it isn't.

Fdisk shows info about partition table, not about real data on that partition.

This says more about what filesystem occupies that partition.
```

file - < /dev/sdb5

```
your output:
```

/dev/stdin: x86 boot sector, Microsoft Windows XP Bootloader NTFS, code offset 0x5b, OEM-ID "NTFS    ", sectors/cluster 8, reserved sectors 0, Media descriptor 0xf8, heads 255, hidden sectors 58589055

```

btw. from your description it looks you have NTFS on sda ....

---

### Post by Pumalite on 2007-09-30
From Terminal post:
sudo fdisk -lu

---

### Post by fdrake on 2007-09-30
what was your mount command ? remember that u cannot write a ntfs partition without the use of fuse and other software. mounting the partition with a write option may cause probls.

---

### Post by squirage on 2007-10-01
Hi pheeror,

The file command gave me this:
```
sean@sean-laptop:~$ file - </dev/sdb5
bash: /dev/sdb5: Permission denied
sean@sean-laptop:~$ sudo file - < /dev/sdb5
bash: /dev/sdb5: Permission denied
```

Being such a newbie to Linux I run into permission problems a lot and still haven't quite figured out the work arounds.

I'm guessing that, had permission not been denied I would have seen something along the lines  of your output code.

And yes, sda does show as NTFS.

Hi Pumalite,

sudo fdisk -lu returns:

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     3074047     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *     3074048   156301311    76613632    7  HPFS/NTFS

Disk /dev/sdb: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    88518149    44259043+   f  W95 Ext'd (LBA)
/dev/sdb2   *    88518150   195366464    53424157+  83  Linux
/dev/sdb5             126    83939624    41969749+   7  HPFS/NTFS
/dev/sdb6        83939688    88518149     2289231   82  Linux swap / Solaris

```

Thanks, that was the  output that I had seen before but lost how to do again when I wrote the  post.

Hi fdrake,

I forget where I saw it right now, but I followed some type of how to that created /media/newdisk and then I used the mount /dev/sdb5 command and it keeps on telling me about bad blocks.

Right now I think part of the problem is I go past the point of mental fatigue and try things I'm not totally ready for. I have a lot of learning to do.

One thing that I did do yesterday was install gparted to get a graphical look at what was going on and it was somewhat revealing. This is what sdb looks like in gparted: (see attached png).

When I installed Ubuntu I got lazy and let the installer do most everything, the only thing I did was manually set the ext3 partition to about half the size of the existing disk to leave room for the windows stuff that was on there. So it looks like it split the disk into sdb1 (which has the swap file and the ntfs file and then sdb2 which is my working linux drive.

It would be nice if I could recover this info, but it's not the end of the world if I can't. The next thing would be to recover the physical space.

Sorry it took me so long to reply, I needed to step away from the computer for my sanity.

Thanks.

---

### Post by Pumalite on 2007-10-01
I think your sdb5 is corrupted. Check with rescuecd:[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)
Or et a Knoppix and examine it:: [http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)

---

### Post by squirage on 2007-11-20
Hi,

  Just wanted to update as solved. Thanks to Pumalite I was able to restore the lost/ corrupted partition on my sbd drive.

  I ended up using the system rescue cd, for some reason I could not use the keyboard with Knoppix.

So the issue was having it be unrecognizable to the system. Once that was taken care of it mounted easily.

Thanks again.

---

### Post by Pumalite on 2007-11-20
You are welcome. Good luck. Glad you got it fixed!

---

