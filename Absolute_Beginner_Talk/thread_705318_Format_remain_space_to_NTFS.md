---
title: "Format remain space to NTFS"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by ceecld on 2008-02-23
Hi,

Im looking to format the unallocated space on my HDD to NTFS for use in Vista/Media Centre.  The problem I have is that if i format the space in Vista i end up with a GRUB error 17 - which i can't seem to fix without reinstalling ubuntu.

What is the best/easiest way to this?

Cheers

---

### Post by taurus on 2008-02-23
Can you post the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```
Meanwhile, you can try using gparted in System -> Administration (if you don't have one, install it with synaptic or apt-get/aptitude) to format that partition to ntfs filesystem.

---

### Post by PmDematagoda on 2008-02-23
If by "unallocated space" you mean the MBR which is about 512kb in size, then formatting it to NTFS is really unwise since GRUB is then removed and would consequently mean that no OS would be allowed to boot.

---

### Post by ceecld on 2008-02-23
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        5228    41945715    7  HPFS/NTFS
/dev/sda3            5229       30401   202202122+   f  W95 Ext'd (LBA)
/dev/sda5           30140       30401     2104483+  dd  Unknown
/dev/sda6            5229        5750     4192902   82  Linux swap / Solaris
/dev/sda7            5751        8361    20972826   83  Linux

Partition table entries are not in disk order


I was looking at GParted however i doesn't have NTFS unless i boot from live CD

---

### Post by ceecld on 2008-02-23
> **PmDematagoda said:**
> If by "unallocated space" you mean the MBR which is about 512kb in size, then formatting it to NTFS is really unwise since GRUB is then removed and would consequently mean that no OS would be allowed to boot.

The remaining space is 167 GB

---

### Post by ceecld on 2008-02-23
im guessing i just need to add the ability ot GParted to perform the NTFS format... right?

Done... ntfsprogs from synaptic manager

---

