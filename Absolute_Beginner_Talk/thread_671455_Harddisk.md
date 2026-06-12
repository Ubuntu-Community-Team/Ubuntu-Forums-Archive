---
title: "Harddisk"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by tomor on 2008-01-18
I have two hard-disks in my computer. In one of them is ubuntu installed and the other one contains just files but its ntfs partition. In Gnome I used to see it in Computer even that it always told me that it cant be mounted. In Kubuntu now I cannot see the first partition of that hard disk anymore. I want to format that hard disk but don't know how to. Help would be appreciated..

---

### Post by zakirs on 2008-01-18
try installing gparted it may help ...but be careful select the right device

> sudo apt-get install gparted

---

### Post by cecure on 2008-01-18
The first step should be to find your partition layout, try running the command:
```
sudo fdisk -l
```

and post the out put.

Here is an example of mine:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         874     7020373+   b  W95 FAT32
/dev/sda2   *         875       30400   237167595    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x12345678

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       48641   390708801    c  W95 FAT32 (LBA)
/dev/sdb2   *       48642       60471    95024475   83  Linux
/dev/sdb3           60472       60801     2650725    5  Extended
/dev/sdb5           60472       60801     2650693+  82  Linux swap / Solaris


As you can see I have 2 hard drives sda & sdb.  On the far right are the filesystems on those partitions.

if you want to format the one harddisk, first determine its name and then run:

```
sudo fdisk /dev/yourharddrive(sda or sdb)
```

press 'm' to see the available commands, you want to delete every partition on the harddrive and then write the table to disk.

Good Luck

---

### Post by tomor on 2008-01-18
> 
tomor@tomor:~$ **sudo fdisk -l**

Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x416c416b

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        9566    76838863+  83  Linux
/dev/hdc2            9567        9729     1309297+   5  Extended
/dev/hdc5            9567        9729     1309266   82  Linux swap / Solaris

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4cb34cb2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4846    38925463+   7  HPFS/NTFS
/dev/sda2            4847        9729    39222697+   f  W95 Ext'd (LBA)
/dev/sda5            4847        9729    39222666    7  HPFS/NTFS


> 

tomor@tomor:~$ sudo fdisk /dev/sda

The number of cylinders for this disk is set to 9729.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): m
Command action
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the dos compatibility flag
   d   delete a partition
   l   list known partition types
   m   print this menu
   n   add a new partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)

Command (m for help): d
Partition number (1-5): 1

Command (m for help): d
Partition number (1-5): 2

Command (m for help): d
No partition is defined yet!

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.
tomor@tomor:~$ sudo fdisk -l

Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x416c416b

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        9566    76838863+  83  Linux
/dev/hdc2            9567        9729     1309297+   5  Extended
/dev/hdc5            9567        9729     1309266   82  Linux swap / Solaris

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4cb34cb2

   Device Boot      Start         End      Blocks   Id  System


This is what happened until now. How can I make it "visible" in Computer now ?? ]

---

### Post by tomor on 2008-01-18
ok i created two partitions with that gparted tool and still it doesnt appear in Storage Media.

I see this in terminal now: 

> 
tomor@tomor:~$ sudo fdisk -l

Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x416c416b

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        9566    76838863+  83  Linux
/dev/hdc2            9567        9729     1309297+   5  Extended
/dev/hdc5            9567        9729     1309266   82  Linux swap / Solaris

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4cb34cb2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4462    35840983+  83  Linux
/dev/sda2            4463        9729    42307177+  83  Linux



---

### Post by cecure on 2008-01-18
I am sorry perhaps this question is a little dumb.  But you do know that formatting the drive erases all data on it.

---

### Post by vikram on 2008-01-18
you need to mount them [https://help.ubuntu.com/community/Mount?highlight=%28mount%29]("https://help.ubuntu.com/community/Mount?highlight=%28mount%29")

sudo mkdir /dir1
sudo mkdir /dir2
sudo mount /dev/sda1 /dir1
sudo mount /dev/sda2 /dir2

now you can 'see' them eg.

ls /dir1

make sure you have the right permissions like so

sudo chown -R *yourusername* /dir1
sudo chown -R *yourusername */dir2

---

### Post by tomor on 2008-01-19
> **cecure said:**
> I am sorry perhaps this question is a little dumb.  But you do know that formatting the drive erases all data on it.

Of course. I wanted all my data to be erased. But anyway thanks i think i understood what should i do now.

---

