---
title: "Installation problem, partitioning stage."
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by VictorGavrish on 2006-09-09
I've already installed Ubuntu once, and it went okay. Except now that I try to repeat the exprience (I muddled up my existing system so much I decided it was easier to reinstall everything than to try to repair the existing installation) when I get to stage five of the installation process (partitioning), the system hangs up almost worse than Windows 98's blue screen of death.

Currently, my hard disks are partitioned this way:

Disk 1: 300 GB SATA HDD:
1. 30 GB FAT32 for my Windows installation;
2. The rest in FAT32 for shared files.
Disk 2: 120 GB SATA HDD:
1. 2 GB Linux swap (also used for Windows's page file using SwapFS driver for Windows)
2. 30 GB of unallocated space, used to be ext3 Linux root, but deleted somwhere in the process of trying to rectify the problem with PartitionMagic;
3. The rest in FAT32 for shared files.

All partitions are primary, I don't have extended partitions.

I've also tried to delete the swap partition with PartitionMagic, but it didn't do any good, so I restored it because it's used by Windows paging file.

---

