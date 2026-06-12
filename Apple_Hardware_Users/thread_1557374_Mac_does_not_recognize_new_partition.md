---
title: "Mac does not recognize new partition"
date: 2010-08-20
forum: Apple Hardware Users
---

### Post by azure kitsune on 2010-08-20
I just installed Ubuntu 10.04 on my Macbook Pro 6,2. Then I used GParted on the Live CD to create another partition that would be shared between the two operating systems.

The problem is that the Mac OS won't recognize the new partition. It will recognize the Ubuntu partition as sda0d4, but not the one I created afterwards. When I load up Disk Utility in Mac, it doesn't find the partition and instead labels it as free space.

Does anyone know how I can fix this problem? Thanks!

---

### Post by linuxopjemac on 2010-08-21
what filesystem did you create on the shared partition?

---

### Post by azure kitsune on 2010-08-21
I have tried NFTS, FAT32, ext2, and ext3, and none of them worked. Attached are screenshots of me trying ext3. There is a screenshot of GParted, and Disk Utility (Mac).

Here is what Partition Inspector says:

*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    154673819  Mac OS X HFS+
 3      154675200    154677247  GRUB2 BIOS Boot
 4      154677248    311307569  Basic Data
 5      953827328    976773119  Linux Swap
 6      311307570    953827244  Basic Data

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2 *       409640    154673819  af  Mac OS X HFS+
 3              1    154677247  ee  EFI Protective
 4      154677248    311307569  83  Linux

MBR contents:
 Boot Code: GRUB

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+, active

Partition at LBA 154675200:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 3, type GRUB2 BIOS Boot

Partition at LBA 154677248:
 Boot Code: None
 File System: ext4
 Listed in GPT as partition 4, type Basic Data
 Listed in MBR as partition 4, type 83  Linux

Partition at LBA 953827328:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 5, type Linux Swap

Partition at LBA 311307570:
 Boot Code: None
 File System: ext3
 Listed in GPT as partition 6, type Basic Data

---

### Post by srs5694 on 2010-08-23
> **azure kitsune said:**
> Here is what Partition Inspector says:
...
Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2 *       409640    154673819  af  Mac OS X HFS+
 3              1    154677247  ee  EFI Protective
 4      154677248    311307569  83  Linux


This may not be the root cause, but you've got two overlapping type-0xEE ("EFI Protective" in this utility) MBR partitions. This is Bad, with a capital B. See my reply (post #8) in [this thread](http://ubuntuforums.org/showthread.php?t=1556993) for more details and how to proceed. In brief, you've got to eliminate partition #3, and I recommend going to a conventional protective MBR rather than the hybrid MBR you've got now, since a hybrid MBR buys nothing but touble (such as this problem) in a Linux/MacOS dual-boot configuration.

---

### Post by azure kitsune on 2010-08-23
Thank you so much! I got everything to work now!

Yep, the sda3 partition was definitely causing the problem. I deleted it using fdisk and Mac was able to detect all the other partitions correctly. But then I got into a bunch of trouble with Ubuntu (which is probably due to other reasons), so I ended up reinstalling Ubuntu, following the instructions here: ( specifically posts #62 and #72 )

[http://ubuntuforums.org/showthread.php?t=1468240&page=7](http://ubuntuforums.org/showthread.php?t=1468240&page=7)

And everything is working fine now. Thank you for pointing me to the cause of the problem!

---

