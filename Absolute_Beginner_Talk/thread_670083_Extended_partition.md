---
title: "Extended partition"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by davesbrain on 2008-01-17
I'm a bit confused about the 'extended partition' that I have.   I thought Ubuntu used 2, one for filesystem and one for swap.   HDA is XP, the HDB is Ubuntu, and the scsi at the bottom is storage/backups.

```
davejr@davejr-desktop:~$ sudo fdisk -l

Disk /dev/hda: 15.3 GB, 15367790592 bytes
255 heads, 63 sectors/track, 1868 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc77ec77e

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1867    14996646    7  HPFS/NTFS

Disk /dev/hdb: 15.0 GB, 15020457984 bytes
255 heads, 63 sectors/track, 1826 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000affe2

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1744    14008648+  83  Linux
/dev/hdb2            1745        1826      658665    5  Extended
/dev/hdb5            1745        1826      658633+  82  Linux swap / Solaris

Disk /dev/sda: 18.3 GB, 18351959040 bytes
255 heads, 63 sectors/track, 2231 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7864361e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2231    17920476    7  HPFS/NTFS
```

---

### Post by camnor on 2008-01-17
What happened is when Ubuntu formatted your harddrives it put your swap file in an Ext partition, which is a partition that houses other partitions, because you can only have 4 partitions one one hard disc, so it makes you able to create as many partitions as nessecary. Hope this helped :KS

---

### Post by davesbrain on 2008-01-17
So I take it that it's perfectly 'normal'.   On a side note I noticed that the cylinders were different between hda and hdb even though they are identical drives(Maxtor51536H2).  When I installed it, I just went with auto in the bios.  And if I do need to change it manually in the bios to the same cylinders as my first hda drive, would that hose this installation?  It is a bit noisy whereas my XP drive(hda) has always been silent.

---

### Post by camnor on 2008-01-18
I am not very familiar with palying with the bios and the cylinder settings, so I can't provide you with any instruction there.  And i do believe that reason why the cylinder nubmers are slgihtly different is because the drives format to a different size depending on how the formatting was done in the factory( you know how there is always those little labels on hard drives that say 160GB* *Actual size may vary after formatting) but that might not have anything to do with it.  Other than that, your drive is absolutely normal! Enjoy Ubuntu!

---

### Post by davesbrain on 2008-01-18
Oh, believe me I AM!   Just making sure everything is okey dokey before liftoff.
There should be a couple of my screengrabs over in that section.
You guys in the forums are great by the way.

---

