---
title: "Win98/Ubuntu dual boot"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by Shador5529 on 2006-11-16
Basically I have two PCs.  A newer Win XP system (my primary pc) and an older Win 98 system that I use for backups.

The Win 98 system has an 80 GB disk, partitioned into 5 sections.
 C: = Where Win 98 is
 D: through G: (I use these to back up data from the main PC over a small LAN connection I set up.)

Basically, I want to install Ubuntu on the Win 98 PC in a dual boot config.  That way I don't have to try to get XP to talk to Ubuntu, I can just boot to 98 when I want to backup over the LAN.

So my question is, How do I install Ubuntu to dual boot on the Win 98 system.  Also, will Ubuntu be able to read my existing drives? (They are all FAT32, I think).

Thanks,
     Mike

---

### Post by lapsey on 2006-11-16
when installing, the partitioner will help you make another partition from whatever is available and you can tell it not to touch any of the existing partitions. dual boot should be set up automatically, since it searches for existing operating systems.

---

### Post by bulldog on 2006-11-16
> **Shador5529 said:**
> Basically I have two PCs.  A newer Win XP system (my primary pc) and an older Win 98 system that I use for backups.

The Win 98 system has an 80 GB disk, partitioned into 5 sections.
 C: = Where Win 98 is
 D: through G: (I use these to back up data from the main PC over a small LAN connection I set up.)

Basically, I want to install Ubuntu on the Win 98 PC in a dual boot config.  That way I don't have to try to get XP to talk to Ubuntu, I can just boot to 98 when I want to backup over the LAN.

So my question is, How do I install Ubuntu to dual boot on the Win 98 system.  Also, will Ubuntu be able to read my existing drives? (They are all FAT32, I think).

Thanks,
     Mike

You must have space available for Ubuntu on that disk.
Should say about 10GB would do nicely.
If that's no problem just install Ubuntu in the free space.

Ubuntu can read and write to FAT32 partitions,but NTFS is read only!!

---

