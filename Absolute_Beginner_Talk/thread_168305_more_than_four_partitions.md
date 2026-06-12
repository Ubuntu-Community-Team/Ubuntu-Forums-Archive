---
title: "more than four partitions?"
date: 2006-04-30
forum: Absolute Beginner Talk
---

### Post by dragonflyFZX on 2006-04-30
hi, 

i have a laptop with a 100GB hard disk.  Of course, it came with windows pre-installed, so i immediately added kubuntu. Now i want to create some space for fat32 to transfer files between ubuntu and window, something like a shared data drive.  But gparted tells me i can only have 4 primary partitions.  

My setup is the following.  First there is about 80MB of fat16, the dell utility space, whatever that may be. Next there is about 30gig ntfs, for windows.  Then, there is about 30gig unallocated, which was where i wanted to make the fat32 partition. Then there is about 30 gig reiserfs with kubuntu.  Then there is sda4 which is an extended partition holding sda5, linux swap of about 1giga.

How can i do what i want to do, ie create this fat32 partition without having to go through a reinstall?

---

### Post by daschl on 2006-04-30
[QUOTE=dragonflyFZX]hi, 

i have a laptop with a 100GB hard disk.  Of course, it came with windows pre-installed, so i immediately added kubuntu. Now i want to create some space for fat32 to transfer files between ubuntu and window, something like a shared data drive.  But gparted tells me i can only have 4 primary partitions.  

My setup is the following.  First there is about 80MB of fat16, the dell utility space, whatever that may be. Next there is about 30gig ntfs, for windows.  Then, there is about 30gig unallocated, which was where i wanted to make the fat32 partition. Then there is about 30 gig reiserfs with kubuntu.  Then there is sda4 which is an extended partition holding sda5, linux swap of about 1giga.

How can i do what i want to do, ie create this fat32 partition without having to go through a reinstall?[/QUOTE]

hm well you can have more than 4 partitions. they are called "logical partitions". you have to create one extended partition, which holds the information for the logical ones. (you don't have to create an extended partition for your own, the program does this for you). so put the kubuntu installer cd rom in the drive and edit your partition table manually. create partitions and choose "logical". 

well, there is only one point i don't remeber exactly, maybe an other user can reply to it: does / or /boot need to be primary?. if they don't need do be primary devices, i can't see a problem :)

---

### Post by dragonflyFZX on 2006-04-30
ok, i tried that, but it is less straigtforward...  The unallocated space gets marked as unusable during manual editing of the partition table.  I also dont see where you could choose logical.  There is something like the LVM (logical volume management).  But i dont know what it is and i dont want to screw things up...

---

### Post by daschl on 2006-04-30
the problem is that you can only have 4 primary partitions. the extended also counts as primary. so - in fact - you can only have 3 primary partitions where you put data on it. 

can you please give us more specific information about the partition layout?

something like this:
```

michi@mainsys:~$ sudo fdisk -l /dev/hda
Password:

Disk /dev/hda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1           4       32098+  83  Linux
/dev/hda2               5        1828    14651280   83  Linux
/dev/hda3            1829        1921      747022+  82  Linux swap / Solaris
/dev/hda4            1922       36481   277603200   83  Linux

```

(maybe from the ubuntu-live cd or so...)

---

### Post by dragonflyFZX on 2006-05-01
```
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          10       80293+  de  Dell Utility
/dev/sda2   *          11        3923    31431172+   7  HPFS/NTFS
/dev/sda3            8517       12009    28057522+  83  Linux
/dev/sda4           12010       12161     1220940    5  Extended
/dev/sda5           12010       12161     1220908+  82  Linux swap / Solaris

```
this is the layout of the disk.  As you can see, there is unallocated space sandwitched between sda2 and sda3. That is the unallocated space I want to format in fat32.  I already have an extended partition, the one holding the linux swap.  How can i set the unallocated space in the extended partition?

---

### Post by mozetti on 2006-05-01
I'm pretty sure all your logical partitions have to be physically contiguous -- meaning your current setup won't work because the extended partition (sda4) is at the end of the drive, but your free space is seperated from the extended partition by the primary partition sda3.

One solution would be to physically move sda3 forward on the disk, so sda1,sda2,sda3 are all back-to-back, then make your extended partition (sda4) use the rest of the space (from sda3 to the end of the disk). Then, make your logical partitions in the contiguous free space in the extended partition.

---

