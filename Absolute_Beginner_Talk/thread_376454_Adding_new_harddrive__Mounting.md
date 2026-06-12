---
title: "Adding new harddrive / Mounting"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by Zero7 on 2007-03-04
Hi,
I have added a Hard Drive after installing Ubuntu 6.10. Ubuntu is installed in SATA Harddrive. Fdisk -l gives the following information.

Disk /dev/sda: 400.0 GB, 400087375360 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10241406    7  HPFS/NTFS
/dev/sda2            1276        1530     2048287+  82  Linux swap / Solaris
/dev/sda3            1531        7904    51199155   83  Linux
/dev/sda4            7905       48641   327219952+   5  Extended
/dev/sda5           14279       20652    51199123+   b  W95 FAT32
/dev/sda6           20653       27026    51199123+   b  W95 FAT32
/dev/sda7           27027       33400    51199123+   b  W95 FAT32
/dev/sda8           33401       39775    51207156    b  W95 FAT32
/dev/sda9           39776       48641    71216113+   b  W95 FAT32
/dev/sda10           7905       10454    20482812   83  Linux
/dev/sda11          10455       14278    30716248+  83  Linux

Partition table entries are not in disk order

Disk /dev/hda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        3684    29591698+   b  W95 FAT32
/dev/hda4            3685       36480   263433870    f  W95 Ext'd (LBA)
/dev/hda5            6098        6204      859446    b  W95 FAT32
/dev/hda6           12384       18612    50034411    7  HPFS/NTFS
/dev/hda7           18613       24811    49793436    7  HPFS/NTFS
/dev/hda8           24812       31003    49737208+   7  HPFS/NTFS
/dev/hda9           31004       36480    43993971    7  HPFS/NTFS
/dev/hda10           3685        6097    19382359+   b  W95 FAT32

Partition table entries are not in disk order
xxx@xxx-desktop:~$ 

 I followed few other threads similar to this issue and I could not get the hard drive to work.   I would like to get hda mounted, so that I can get access to all the files. Thanks a lot in advance for all the help.

---

### Post by Mr. C. on 2007-03-04
You don't want to mount the entire disk - you want to mount particular partitions.

What partition do you want mounted?

How are you trying to mount the partition?

MrC

---

### Post by Zero7 on 2007-03-05
> **Mr. C. said:**
> You don't want to mount the entire disk - you want to mount particular partitions.

What partition do you want mounted?

How are you trying to mount the partition?

MrC

Thanks! I want to mount all  partitions of hda series. ie hda1, hda4, hda5, hda6, hda7, hda8, hda9, hda10

If you could help me with detailed instructions that would be great.

Also, I'm not able to create mount points with mkdir command. I get Permission denied error.

---

### Post by rccharles on 2007-03-05
> **Zero7 said:**
> Hi,
I have added a Hard Drive after installing Ubuntu 6.10. Ubuntu is installed in SATA Harddrive. Fdisk -l gives the following information.

Disk /dev/sda: 400.0 GB, 400087375360 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10241406    7  HPFS/NTFS
/dev/sda2            1276        1530     2048287+  82  Linux swap / Solaris
/dev/sda3            1531        7904    51199155   83  Linux
/dev/sda4            7905       48641   327219952+   5  Extended
/dev/sda5           14279       20652    51199123+   b  W95 FAT32
/dev/sda6           20653       27026    51199123+   b  W95 FAT32
/dev/sda7           27027       33400    51199123+   b  W95 FAT32
/dev/sda8           33401       39775    51207156    b  W95 FAT32
/dev/sda9           39776       48641    71216113+   b  W95 FAT32
/dev/sda10           7905       10454    20482812   83  Linux
/dev/sda11          10455       14278    30716248+  83  Linux

Partition table entries are not in disk order

Disk /dev/hda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        3684    29591698+   b  W95 FAT32
/dev/hda4            3685       36480   263433870    f  W95 Ext'd (LBA)
/dev/hda5            6098        6204      859446    b  W95 FAT32
/dev/hda6           12384       18612    50034411    7  HPFS/NTFS
/dev/hda7           18613       24811    49793436    7  HPFS/NTFS
/dev/hda8           24812       31003    49737208+   7  HPFS/NTFS
/dev/hda9           31004       36480    43993971    7  HPFS/NTFS
/dev/hda10           3685        6097    19382359+   b  W95 FAT32

Partition table entries are not in disk order
xxx@xxx-desktop:~$ 

 I followed few other threads similar to this issue and I could not get the hard drive to work.   I would like to get hda mounted, so that I can get access to all the files. Thanks a lot in advance for all the help.

I assume it was /dev/hda

Try this page:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

You won't see the entries already in /etc/fstab.

Robert

---

### Post by Mr. C. on 2007-03-05
The HowTo listed should get your through the process.

It would be better, in my opinion, if you understood a little more about the partitions and file systems.  You mention that you want to mount /dev/hda4... but this can't be mounted.  Its only a place holder describing the other partitions.

Spend a little time trying to understand how these things work.  Here's a basic idea - look at the Week 4 Notes: Filesystems, Disks and Partitions

[http://cis68c1.mikecappella.com/calendar.php](http://cis68c1.mikecappella.com/calendar.php)

and take a look at the Lab and Homework there.  That should help you through the steps, and these steps will transfer to any Unix/Linux system in general.

Your permission denied message is occurring because you, as a normal user, do not have permission to create a directory in the place you want.  It is restricted to the root user.  Sudo or su to root and then create the directory you wish to use as a mount point.  Again, go review the Week 4 stuff I mentioned above.  I think you will find it very helpful.

MrC

---

### Post by Zero7 on 2007-03-05
Robert and MrC, Thanks a lot for great information. I will try working on it this week. Both the websites are really good. Thanks again!

---

### Post by anaconda on 2007-03-05
to mount any of them manually you need to do this (in terminal):

sudo mkdir /media/hda1
sudo mount /dev/hda1 /media/hda1

(after the first sudo it will ask your password..)
This will first create the folder /media/hda1 and then mount your hda1 partition to it.. should also appear to your desktop.

The same commands work with all the other partitions too.. just change the number.

If you want them to be mounted automatically during each boot you will have to add them to your /etc/fstab -file..

---

### Post by Zero7 on 2007-03-14
Could get some time today to try again. I get "can't find /dev/hda1 in /etc/fstab or /etc/mtab" error when I try to mount using "sudo mount /dev/hda1 /media/hda1" command. TIA for the help.

---

### Post by Mr. C. on 2007-03-14
Use either the mount point or the file system to mount if entries are in /etc/fstab.  Eg:

mount /media/hda1

or

mount /dev/hda1

The entries must be in your fstab for this shortcut to work.  Otherwise, you need to supply the correction options to the mount command.  Eg: 

mount -t vfat /dev/hda1 /media/hda1

All of this is done as root, of course.

MrC

---

