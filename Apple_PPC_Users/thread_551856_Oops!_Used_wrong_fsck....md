---
title: "Oops! Used wrong fsck..."
date: 2007-09-15
forum: Apple PPC Users
---

### Post by AriK2 on 2007-09-15
I have a faulty HD that had some contact with a magnet. I was checking if I could rescue some files on my Linux PC.

I could mount the partiton and heres the fdisk output:

```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  EFI GPT
Partition 1 does not end on cylinder boundary.
/dev/sda2              26       17257   138412032   af  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sda3   *       17274       19458    17542960    c  W95 FAT32 (LBA)
Partition 3 does not end on cylinder boundary.

```

Why is the partition id unknown? Doesn't the fdisk know about mac partitions?

Anyway, I could see all the files and when I tried to copy them to another drive the system locks up. Nothing happens and I need to do a forced reboot.

I thought of doing a fsck on the partition, but I accidentally executed the hfsck instead of hpfsck. Now the partition won't mount anymore. Is there a way of restoring the hfs+ header? I think the hfsck did something to it?!

How does a clean header look like? Can someone post one so I could compare it to my hd?

Thanks!

---

### Post by pxwpxw on 2007-09-16
**AriK2**

That fdisk listing is what you would expect from fdisk on a pc looking at a GPT/MBR partitioned hard disk form a Apple MacIntel which had Macosx and Windows on it (no linux), looks normal to me.

I have an xubuntu PC here which can mount and read both HFS and HFS+ partitions on an external which has an Apple Partiton Map partitioning scheme. (fdisk cannot handle that at all).
I don't see why there would be a problem in copying files from the af partition, given that you could see them.

I cannot find any "hfsck", I can find hpfsck in the hhsplus pacckage.
Don't know what you mean by "header"

You might do better in the Apple Intel Users forum.

---

