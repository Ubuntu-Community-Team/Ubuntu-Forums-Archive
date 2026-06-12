---
title: "WinXP and Feisty dual boot - where I'm at..."
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by stil on 2007-08-05
Hello people... I'm still deciding whether to go through with this.

I started off by installing WinXP with two NTFS partitions. I installed XP onto the small 3.5gig partition. I then deleted the large partition during Feisty install process and converted the unused space into ext3 / + a swap

I probably should have read up before I attempted this. I'm worried that if I get WinXP going through grub it'll 'pack a sad' and screw with the partition table in a bad way.

This is the output from sudo fdisk -l

```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2               1       19456   156280288+   f  W95 Ext'd (LBA)
/dev/sda5           18996       19456     3702951    7  HPFS/NTFS
/dev/sda6               1       18752   150625345+  83  Linux
/dev/sda7           18753       18995     1951866   82  Linux swap / Solaris

Partition table entries are not in disk order

```

I don't really know how to interpret this...

I've modified menu.lst with this addition

```

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root

title           Microsoft Windows XP Professional

root    (sda5)
savedefault
makeactive
chainloader     +1
```

This returned an error code #23 :confused:

I'm considering dumping XP altogether. If that comes about, how would I go about merging the NTFS parition into Linux?

---

### Post by logos34 on 2007-08-05
I doubt you'll be able to boot windows like that--on a logical partition (unless there's another bootable windows on a primary partition).  Might be best to start over and install purely ubuntu (root + swap and possibly a separate /home), or if you want windows put it on  a ~10 GB or so primary at the front of the disk.  XP and ubuntu coexist just fine in dual boot.

---

### Post by Majorix on 2007-08-05
Does the computer even boot at all? You don't seem to have a partition with a boot flag...

---

### Post by stevebakerj on 2007-08-05
> **stil said:**
> 
```

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root

title           Microsoft Windows XP Professional

root    (sda5)
savedefault
makeactive
chainloader     +1
```

This returned an error code #23 :confused:


Shouldn't this be

hd0,1

---

### Post by stil on 2007-08-05
> **Majorix said:**
> Does the computer even boot at all? You don't seem to have a partition with a boot flag...

I'm using it *right now*. Maybe it's going to explode in my face at any moment... :lolflag:

Sorry, but I had to... :)

I think I'll just re-install with ubuntu only.

---

