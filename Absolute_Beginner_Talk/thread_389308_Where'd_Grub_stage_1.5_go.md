---
title: "Where'd Grub stage 1.5 go?"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by driant on 2007-03-20
Hiya! I've spent the last couple of weeks trying to figure out this weirdness on my own, and it's just not happening.

I'm trying to dual-boot XP and Edgy on my laptop. There's 1 120GB SATA hd partitioned as follows:

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100        5479     3052350   82  Linux swap / Solaris
/dev/sda3           12035       14593    20555167+   b  W95 FAT32
/dev/sda4            5480       12034    52653037+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
```

Basically, an NTFS partition, and ext3 partition, and a fat32 partition to share files between the two. Now, for the most part, I can switch between the two just fine. However, Grub seems to just...misplace stage 1.5 every once in awhile when I switch from XP back to Edgy.

I'll boot up, get the "Grub loading stage 1.5" message, with a newline and blinking cursor, and that's pretty much it. No disk access, keyboard doesn't respond, nothin'. What I do then is throw in a liveCD and reinstall grub from the grub shell:

```
$ sudo grub
grub> root (hd0,3)
grub> setup (hd0)
```

And then everything's cool, until I randomly switch back from XP to Edgy one day, and it's gone again!

It seems to happen on Windows Updates and/or app installation on the XP side. I'm not quite clear on whether or not stage 1.5 lives in the first couple of sectors after the MBR on the first partition, or in /boot along with everything else on the fourth partition. If it's the former, would doing...well, anything that writes to the XP partition destroy that?

I don't know. I've looked everywhere and haven't been able to find anybody with the same issue: Grub's basically giving up without any error output before stage 2 loads.

Any ideas?

---

### Post by driant on 2007-03-20
Heh. I just realized (the "Partition table entries are not in disk order" bit from fdisk should've clued me in :P) that the ext3 partition and the fat32 drive partition are actually swapped. That is, I've got:

NTFS -> Swap -> ext3 -> fat32

not

NTFS -> Swap -> fat32 -> ext3

Am I correct in thinking that Grub's root should be (hd0,2) instead of (hd0,3), then?

---

### Post by alienexplorers on 2007-03-20
When you boot from the liveCD and run Sudo Grub, what does find /boot/grub/stage1 list as your root drive.

---

### Post by lamalex on 2007-03-20
isnt grub usually hd(0,0) usually? since it is before all of the other partitions? Idk, i'm just throwing it out there.

---

### Post by driant on 2007-03-20
find /boot/grub/stage1 from a live cd returns (hd0,3)

---

