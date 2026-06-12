---
title: "Read-only Thumbdrive help"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by Spirotot on 2007-12-13
Ok, so, I got this 1GB thumbdrive at a seminar (It's full of promo-/crapo-software...), but it's read-only (in fact, it shows up as a CD-drive when I plug it into my computer...). So, I'm wondering, how can I make this thumbdrive usable? I have succeeded in making a 540MB partition on the drive, since the CD-type partition only takes about 400-odd MB's. I've tried the Vista disk-partitioner-thing, and I've tried Gparted on Ubuntu, but haven't had any success with the CD-partition thing. Any help is appreciated.

---

### Post by PmDematagoda on 2007-12-13
What is the File System of the pen drive?

---

### Post by Spirotot on 2007-12-14
The 540MB regular partition is FAT32. The CD-type partition is "udf"... I've never heard of it before. :S

---

### Post by vanadium on 2007-12-14
You could use gparted to wipe the existing partitions, create a new partition and format it for example to fat32 (guarantees most wide compatibility). Gparted is on the live disc, but is not installed by default on your hard drive. You can install it through synaptics.

Be careful when using gparted. Be sure that, in the top right corner, you effectively select your USB.

---

### Post by Spirotot on 2007-12-14
> **vanadium said:**
> You could use gparted to wipe the existing partitions, create a new partition and format it for example to fat32 (guarantees most wide compatibility). Gparted is on the live disc, but is not installed by default on your hard drive. You can install it through synaptics.

Be careful when using gparted. Be sure that, in the top right corner, you effectively select your USB.

That's just the problem, though... I don't see the read-only partition of the thumbdrive in Gparted. Only the FAT32 partition shows up (it was previously "unallocated").

---

### Post by vanadium on 2007-12-14
Perhaps post the output here of "sudo fdisk -l" (we need only the part related to your USB stick). This might give an idea of how this drive is currently configured.

---

### Post by Spirotot on 2007-12-14
```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa8ae3a23

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192       12848   101662720    7  HPFS/NTFS
/dev/sda3           12849       14514    13382145   83  Linux
/dev/sda4           14515       14593      634567+   5  Extended
/dev/sda5           14515       14593      634536   82  Linux swap / Solaris

Disk /dev/sdb: 569 MB, 569901056 bytes
255 heads, 63 sectors/track, 69 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b9bdf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          69      554211    b  W95 FAT32
 
```

I don't see the "sdb2" (I think?) that should be the read-only storage. I'm also slightly confused as to why there's so many partitions on the "sda" disk... I thought there should only be the main Vista partition, and the Ubuntu partition (I'm dual-booting them... but I've been liking Ubuntu so much that it's really the only OS I use, now).

---

### Post by vanadium on 2007-12-14
Indeed, there is nothing more to see for your sdb in fdisk. I am checking here with a dvd in my drive, and that also won't show up in fdisk -l. Most likely, you will see it in the output of the "mount" command. Possibly, you won't be able to convert it.

---

### Post by Spirotot on 2007-12-14
> **vanadium said:**
> Indeed, there is nothing more to see for your sdb in fdisk. I am checking here with a dvd in my drive, and that also won't show up in fdisk -l. Most likely, you will see it in the output of the "mount" command. Possibly, you won't be able to convert it.

Not surprising... But stil, thanks for the help guys. At least I got 540MB out of it. :P

---

### Post by kidputer on 2008-01-24
You need to open the drive up and see which chip is in it.
Then download the manual for that flash chip.
Then find the write lock pin and wire it high or low to desired setting according to the chip documentation.
The one I disassembled had a jumper pin but without the pins for read-write, so I just soldered it closed and it is now read write.
waalaa-read write

---

