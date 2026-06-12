---
title: "[SOLVED] Changed disk to dynamic, Grub will not load"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by DingsBumps on 2008-01-20
Yesterday, while I was moving my music from my old computer to my new one, I realized I ran out of room on my vista partition (I was using vista at that moment), so I figured I would create a new partition to keep my media on. I used Vista's disk partitioning tool to create a new FAT32 partition in the unused space on my HD. During that process, a box popped up saying that my disk would have to be changed from basic to dynamic and that no other OSes would be able to boot.

Of course, I just clicked ok because I figured that... well... I don't know what I was thinking but I clicked OK. After I made my new partition, I put all my music on it, shut down my computer, and went to bed.

This morning, I click my power button, and as usual, something along the lines of "Grub loader v.1.5 is loading" (something like that, but not that text exactly). But grub never loads, my screen doesn't move from there. 

So I think, this should be simple, just pop in the ubuntu CD and click fix MBR. But there is no magical Fix MBR button and I don't know where to go from there.

I used the live CD and I was looking through a couple guides for re-installing GRUB and after following some instruction, I realized my computer no longer has a /boot/grub directory, which I beleive is bad. 

ls /boot give me:
```
ubuntu@ubuntu:~$ sudo ls /boot
abi-2.6.22-14-generic             memtest86+.bin
config-2.6.22-14-generic          System.map-2.6.22-14-generic
initrd.img-2.6.22-14-generic.bak  vmlinuz-2.6.22-14-generic
```

Anyone have any ideas? Please?

---

### Post by cecure on 2008-01-20
I can't see vista erasing the grub folder altogether.  At boot does grub give you any errors?

I am not sure but is it possible that you have a /boot partition and it just isn't mounted.  Try ```
sudo fdisk -l
```
and post it.  That will let us see your partition layout... maybe even see what vista has done.

---

### Post by DingsBumps on 2008-01-20
sudo fdisk -l gives:
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x71317131

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686   42  SFS
/dev/sda2            5100        5100         234+  42  SFS
/dev/sda3            5100       11554    51843072   42  SFS
/dev/sda4           11554       19458    63487799+  42  SFS

Disk /dev/sdb: 6144 MB, 6144284160 bytes
255 heads, 63 sectors/track, 747 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1           5       40131    0  Empty
/dev/sdb2               6         747     5960115    b  W95 FAT32

```

The second device is my ipod.

---

### Post by DingsBumps on 2008-01-20
The exact message is "GRUB Loading stage1.5"

A google search on this cause me to use my ultimate boot CD to fix the MBR.

So now, I have a working Vista/XP bootloader.

I will go find out how to re-install GRUB and I'll mark this thread as (semi-)solved.

---

