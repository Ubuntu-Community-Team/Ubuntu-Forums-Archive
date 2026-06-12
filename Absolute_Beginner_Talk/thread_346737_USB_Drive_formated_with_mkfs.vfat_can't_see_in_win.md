---
title: "USB Drive formated with mkfs.vfat can't see in windows."
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by ADT on 2007-01-26
I was looking through the forums and didn't come across my problem.
I formatted a usbdrive on xubuntu using the command:

```

sudo mkfs.vfat -I -n USBDRIVE /dev/sda

```

I can read and write to the usbdrive on xubuntu, however when I plug in the usbdrive
in windows it is mounted but I can not access it.

I used windows control panel > administrative tools > computer management
and then opened Disk management to see what was wrong.
Windows sees the usbdrive formated using linux as Unallocated space.

I then used windows to format the usbdrive as fat32 even though I had already formated the drive on linux as fat32.

Is there something more needed to add to the command

sudo mkfs.vfat -I -n USBDRIVE /dev/sda

to allow the usbdrive to be seen using windows.

It defeated the point of formating a fat32 usbdrive using linux if I can't access it under windows. 

Cheers.

---

### Post by diepruis on 2007-01-26
What does ```
 fdisk -l /dev/sda 
``` say?

Oh, and try partitioning with ```
 sudo mkfs.vfat -I -n USBDRIVE /dev/sda1 
```

(note the 1 after "/dev/sda")

---

### Post by ADT on 2007-01-26
Thanks for the reply.

I tried fdisk -l on the usbdrive after I formated it using mkfs.vfat

```

fdisk -l
Disk /dev/sda:	10.0GB, 10056131072 bytes
64 heads, 32 sectors/track, 9590 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes

Device Boot          Start     End       Blocks           Id	            System

```


I tried fdisk -l on the usbdrive after I formated it using windows disk manager

```

fdisk -l 
Device Boot          Start     End       Blocks           Id	            System
/dev/sda1                1        1222     9815683        c	            W95 FAT32 (LBA)

```


Windows disk manager seems to add a new partition sda1 onto the usbdrive.


Partitioning the usbdrive using the following command

```

sudo mkfs.vfat -I -n USBDRIVE /dev/sda1
mkfs.vfat 2.11 (12 Mar 2005)
/dev/sda1: No such file or dircetory

```

---

### Post by diepruis on 2007-01-26
The command you were using was incorrect, the one I gave you should work after creating the partition /dev/sda1

For help on creating that partition, see man fdisk, you can also try cfdisk or gparted.

---

### Post by ADT on 2007-01-26
Thanks,
I created the partition on the usbdrive using:

```

sudo mkfs.vfat -I /dev/sda

```


Then I used fdisk to creat a new partition on the usbdrive:
```

sudo fdisk /dev/sda

```

Add a new partition (option n)
```

Command (m for help): n

```


Choose Primary Partition
```

Command action
         e   extended
         p   primary partition (1-4)
p

Partition number (1-4): 1
First cylinder (1-9590, default 1):
Using default value 1
Last cylinder or +size or +sizeM or +sizeK (1-9590, default 9590):
Using default value 9590

```

Then I used the option "w" to write the changes to the disk. 
```

Command (m for help): w
The partition table has been altered!

Calling ioclt() to re-read partition table.
Syncing disks.

```

Then I checked if everything had been created:

```

fdisk -l
Disk /dev/sda: 10.0 GB, 10056131072 bytes
64 heads, 32 sectors/track, 9590 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes

Device Boot	Start	End		Blocks		Id		System
/dev/sda1		1              9590	               9820144		83		Linux

```

And then I used the command:
```

sudo mkfs.vfat -I -n USBDRIVE /dev/sda1

```

This time the /dev/sda1 partition existed so the command worked.

I still can not access the usbdisk on windows even though windows can see the usbdrive as fat 32
The problem is that it sees the filesystem as:       healthy [unknown partition].
I read up about this and when windows disk management displays a partition as healthy [unknown partition] it means that the partition has been toggled to be hidden.
Is there anyway using linux to unhide a partition when you create it. 

Thanks for the help.

---

### Post by diepruis on 2007-01-26
I can find nothing about "hidden" partitions in the documentation for fdisk or mkfs. I think when you partitioned the device with fdisk, you chose the wrong type for the partition. This is substantiated by your fdisk -l output showing "System" as "Linux". Try using cfdisk to change the partition type to 0B and reformat.

---

### Post by ADT on 2007-01-26
Thank you very much for the help.
I used cfdisk to change the FS type from "LINUX" to "W95 FAT32 (LBA)".
And I can now access the usbdrive from a windows operating system.
I had gone down the wrong track for solving the problem by myself as my idea of hidden partitions was completely wrong. 
At least I discovered that you can change hidden Fat32 partitions to normal Fat32 on a windows operating system by using a windows startup disk and then running a free partition magic PowerQuest tool called ptedit.exe which is a partition table and boot record editor.

---

### Post by diepruis on 2007-01-26
Great, happy to help.

---

