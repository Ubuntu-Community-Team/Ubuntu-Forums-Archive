---
title: "Ubuntu not seeing all hard drives"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by CCIEMD on 2008-03-24
Hi all,

I'm trying to figure out why Ubuntu doesn't seem to be recognizing all of my hard drives.  My computer has 7 physical hard drives installed.  One drive is being used and the Linux drive.  The remaining 6 drives are configured as a (fake)raid for Windows.  I would like to be able to use dmraid to see the Windows partitions on the 6 drive fakeraid, however, Ubuntu seems to only see 3 hard drives total. Any suggestions?

Output of "sudo fdisk -ls":
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6607fee8

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000020

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00096176

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        2432    19535008+  83  Linux
/dev/sdc2            2433       10942    68356575   83  Linux
/dev/sdc3           10943       12158     9767520   82  Linux swap / Solaris
/dev/sdc4           12159       91201   634912897+   7  HPFS/NTFS

```

Thanks in advance.

Richard

---

### Post by Squish on 2008-03-25
I am wondering too

BTW, is this software or hardwar raid?

Ive had my go at installing ubuntu on raid before, but I have not had the luck to boot multiple os's off a raid, as it always detects them as individuals. Would it be better to setup ubuntu first in this case?

---

### Post by CCIEMD on 2008-03-25
This behavior is definitely a change from Feisty.  If I boot from a Feisty Live CD, all 7 hard drives are seen (sda - sdg).

RAID can be confusing.  Virtually all motherboards which support RAID, really support fakeraid.  A Windows device driver sees the RAID as a single drive, but all the work is done in software.  This is a fakeraid setup (i.e. RAID configured in the BIOS off an Nvidia 2200Pro chipset).  Windows doesn't see the individual hard drives, just the RAID.  Linux should see the individual drives.

Richard

---

### Post by Squish on 2008-03-25
Oh shees, mind fart
Fake Raid = software raid


Anyhoo, 

*Bump*
Somebody out there has to have an answer

---

### Post by CCIEMD on 2008-03-26
I think there must have been a regression in the SATA code.  All 7 hard drives (/dev/sda through /dev/sdg) are correctly detected in Feisty (kernel 2.6.20) but are not seen when booting with Gutsy (2.6.22) or Hardy (2.6.24).  Interestingly, Fedora 8 (2.6.23) also only sees the first three drives, but Fedora 9 Beta (2.6.25rc) correctly detects all 7 drives.  

This looks like a bug to me that has already been fixed in the kernel.  Unfortunately, I'm having a hard time finding where the fix might be.  As it has already been fixed, hopefully the fix can be backported into 2.6.24 for the Hardy release.  I filed a bug on this.

[https://bugs.launchpad.net/ubuntu/+bug/206901](https://bugs.launchpad.net/ubuntu/+bug/206901)

Richard

---

