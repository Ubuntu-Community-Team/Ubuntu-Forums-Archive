---
title: "[SOLVED] Turn Windows Partiton in Extra Ubuntu Partition"
date: 2008-07-04
forum: Apple Hardware Users
---

### Post by dmitrijledkov on 2008-07-04
```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000070c4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  EFI GPT
/dev/sda2              26        5452    43580948   af  Unknown
/dev/sda3            5468        6553     8715820+  83  Linux
/dev/sda4   *        6553        7296     5971480    c  W95 FAT32 (LBA)

```

I want to reformat last partition into ext3 and make it automount into /home/user/temp.

How to do it in Gnu Parted? Will it break Mac booting (rEFIt installed)? 

Do I need to do anything else to make this "clean" & painless?
(Windows is no longer going to be there + it will change format)

Thank you in advance.

---

### Post by DonnieP on 2008-07-04
> **dmitrijledkov said:**
> 
I want to reformat last partition into ext3 and make it automount into /home/user/temp.

How to do it in Gnu Parted? Will it break Mac booting (rEFIt installed)? 

Do I need to do anything else to make this "clean" & painless?
(Windows is no longer going to be there + it will change format)

Thank you in advance.

In my experience, yes, you can use gparted and, no, it doesn't break rEFIt.  Personally, I like to boot to SystemRescueCD to run gparted, but there are certainly other ways to accomplish the same thing.  After running gparted and rebooting, you will have to run the “Partitioning Tool” from the rEFIt menu.

---

