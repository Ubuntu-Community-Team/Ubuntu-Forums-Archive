---
title: "Partitions and Touchpad click"
date: 2007-09-12
forum: Apple Intel Users
---

### Post by omax on 2007-09-12
Hi guys...

I have a couple of partitions on my Macbook C2D.

1. The Mac OSX partition
2. Xubuntu Partition
3. Windows XP Partition
4. FAT32 Storage Partition

The thing is, the last partition... FAT32 shows up in Linux. But not in Windows or Mac OSX.
In Windows it says that there is no partition. That it's free space but I can't create a new partition.
In linux the flags of the partition is: mstfres

How could I fix it?

Second question: The touchpad of my macbook works excellent under Mac OS and Windows.
But there is one problem in Linux. That it accept touch as a click. How can I disable that?
Does gsynaptics work on Mac to?

Happy for answers :)

Omax

---

### Post by pxwpxw on 2007-09-12
> **omax said:**
> Hi guys...

I have a couple of partitions on my Macbook C2D.

1. The Mac OSX partition
2. Xubuntu Partition
3. Windows XP Partition
4. FAT32 Storage Partition

The thing is, the last partition... FAT32 shows up in Linux. But not in Windows or Mac OSX.
In Windows it says that there is no partition. That it's free space but I can't create a new partition.
In linux the flags of the partition is: mstfres

How could I fix it?

Omax

To answer, - my current gpt and mbr partition tables, explanation below:
```

ubuntu:~$ sudo parted /dev/sda p

Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name                  Flags  
 1      20.5kB  210MB   210MB   fat32        EFI System Partition  boot   
 2      210MB   20.1GB  19.9GB  hfs+         Apple_HFS_Untitled_1         
 3      20.2GB  28.8GB  8590MB  ext3         uxroot1                      
 4      28.9GB  41.7GB  12.8GB  fat32        XP                    msftres
 7      67.3GB  76.0GB  8701MB  fat32                              msftres
 6      76.0GB  78.0GB  2026MB  hfs+                               hidden 
 5      78.0GB  80.0GB  2000MB  linux-swap                                

ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  EFI GPT
/dev/sda2              26        2442    19406616   af  Unknown
/dev/sda3   *        2458        3503     8389124   83  Linux
/dev/sda4            3519        5076    12502320    b  W95 FAT32

```
==========

The 1st 4 partitions use up the 4 primaries windows limit (when there is no extended/logical system). xp can't see the others.

Macosx can mount fat32 using a terminal command
```

 sudo mkdir afolder
 sudo mount -t msdos /dev/disk0s4 afolder

```

There are also several utilities to automount linux partitions in windows and macosx, I don't know if that also solves the 4 primaries limit for xp.
Google "extfs windows" or "extfs macosx"

I just made the xp partition fat32.

---

### Post by omax on 2007-09-12
So there is a limit to how many partitions Windows can handle? I must say, stupid Microsoft.

Ok so here's the deal then. Is it possible for me to merge the Windows partition (which also is FAT32) with my FAT32 partition.

```
ubuntu:~$ sudo parted /dev/sda p

Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name                  Flags  
 1      20.5kB  210MB   210MB   fat32        EFI System Partition  boot   
 2      210MB   37.8GB  37.6GB  hfs+         Apple_HFS_Untitled_1         
 3      37.9GB  45.3GB  7340MB  ext3         Linux                        
 5      45.3GB  66.9GB  21.7GB  fat32                              msftres
 4      66.9GB  80.0GB  13.1GB  fat32        Windows                      

Information: Don't forget to update /etc/fstab, if necessary.             

ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  EFI GPT
/dev/sda2              26        4595    36700160   af  Unknown
/dev/sda3            4611        5504     7168000+  83  Linux
/dev/sda4   *        8136        9730    12803120    c  W95 FAT32 (LBA)

```

As you see, the last partition I created (the FAT32) is located before the Windows partition.

Is it possible to merge them?
Thank you for your answer pxwpxw

---

### Post by pxwpxw on 2007-09-12
> **omax said:**
> 
As you see, the last partition I created (the FAT32) is located before the Windows partition.

Is it possible to merge them?
Thank you for your answer pxwpxw

Yes I see, I think that makes merging impossible.
But the fat32 partitions are both above the others, so it might be possible to delete both in parted, and then reinstall xp making one large fat32 partition as the 4th primary if thats what you want. However,  that would depend on xp being able to get reinstalled, with Macosx and Linux already there, I cant really comment on possible problems there. However I did install XP after all the others here on my MacBook triple booting, with some juggling. 

You might need some other opinions on that.

---

### Post by cyberdork33 on 2007-09-12
> **omax said:**
> So there is a limit to how many partitions Windows can handle? I must say, stupid Microsoft.

Yes and no, it is really a limited enforced by the fact that you cannot create an extended or logical partition on a GPT disk... at  least not with bootcamp.

---

### Post by benanzo on 2007-09-12
GPT doesn't support extended/logical partitions but instead supports up to 128 primary partitions.  MBR doesn't support more that 4 primary partitions, but can have many extended/logical partitions.  Hence you see the problem with dual/triple booting MBR-dependent OSs in a GPT environment.

It is not safe to merge two vfat partitions if Windows is installed on one of them.  You'll likely have to remove both of them, then create a new partition and reinstall Windows.

---

