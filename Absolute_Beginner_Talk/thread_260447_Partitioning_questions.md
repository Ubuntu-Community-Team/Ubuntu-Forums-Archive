---
title: "Partitioning questions"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by crokett on 2006-09-18
My existing setup is 3 SCSI disks -
sda is 9Gb, single partition, windows XP
sdb is 76Gb, 4 partitions, 9Gb ext3, 20Gb NTFS, 20Gb NTFS and what is left NTFS.  Ubuntu is on sdb1
sdc is 9gig, 8Gb ext3 partition and 1Gb swap. 

I'd like to move ubuntu to its own disk.  How to do this without reinstalling? Software mirror then break the mirror? Also would have to create /swap somewhere else, at least temporarily.

I have another 76 gig disk I want to add and my Linux knowledge is somewhat rusty.  What I recall recommended is partitions for: 

/boot
/home
/tmp
/usr
/var

How big do each of those need to be? And once they are created, fstab need updating for /home and /.  Would the rest also go in fstab to mount the new filesystems under the proper directories? Can they all go on sdc?  Ideally I have the full 76gig available on the 2nd disk for data so I'd rather just have symlinks in /home to get to actual data so it can remain more or less static and I can thrash disks if I need to in future.

---

### Post by wieman01 on 2006-09-18
I have done similar stuff recently. There are basically 3 things you need to take account of:

1. GRUB (master boot record needs updating)
2. /boot/grub/menu.lst
3. /etc/fstab

You can copy/move/resize partitions using GParted (Gnome Partition Editor). It's fairly easy & safe as far as I have experienced it.

As for the size, this is what I have got:

/[root] : 10 GB
/home : 5 GB
/[swap] : twice the size of my RAM
/data : remaing HD space

That being said, I have never tried to merge partitions as you're trying to do (var, tmp, usr, etc.). But I reckon a normal "copy" command would do once the root partition has been created.

---

### Post by crokett on 2006-09-18
I will install the new drive then boot the live CD and do all my work from there.  I will get the install booting off the new drive before I delete the old partition.

---

### Post by wieman01 on 2006-09-18
That's a sensible move. Although it's generally safe to copy &  move partitions I would not take a risk either, if you have a choice. I did not have a choice because my external backup drive is full... But I closed my eyes and had luck twice. ;-)

Let us know how it goes. Here is a good link if you have questions concerning GRUB:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by crokett on 2006-09-19
Gparted did not work.  

It was able to resize the partition that Ubuntu is currently installed on but failed at copying to another disk.  It may have something to do with the swap partition on that disk. After thinking about it over a beer, I decided the install is not that old and I can just reinstall.  I will organize things a bit better on this new install.

---

### Post by wieman01 on 2006-09-19
It's too bad you'll have to reinstall. But a beer helps sometimes to make things a bit easier. ;-)

Let me know ifyou still want to try something else. It surprises me GParted did not do the job. I have made good experience with it.

---

### Post by crokett on 2006-09-19
Well at the moment the install is not working.  It asks for the keyboard layout then when I hit 'next' sits there and doesn't do anything.  I let it sit for about half an hour and no changes. :confused: Any way to open a terminal window and see what is happening?  The changes from the original install to now are adding a new HDD and having a printer connected.  I disconnected the printer but still no joy.

So I may be back to Gparted to resize the current install and then just to add a new partition for /home...

---

### Post by wieman01 on 2006-09-20
Can you attach a screenshot of your partions please? Just fire up GParted and take an image. Then I can propose a way of moving your partitions.

---

### Post by crokett on 2006-09-20
Here is what fdisk says 

```

# XP is installed on this disk
Disk /dev/sda: 9173 MB, 9173114880 bytes
255 heads, 63 sectors/track, 1115 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1114     8948173+   7  HPFS/NTFS

Disk /dev/sdb: 73.4 GB, 73407488000 bytes
255 heads, 63 sectors/track, 8924 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

# Linux is installed on /dev/sdb1
# rest of this disk is XP data
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         892     7164958+  83  Linux
/dev/sdb2            1276        3825    20482875    7  HPFS/NTFS
/dev/sdb3            3826        5482    13309852+   7  HPFS/NTFS
/dev/sdb4            5483        8924    27647865    7  HPFS/NTFS

Disk /dev/sdc: 9100 MB, 9100369920 bytes
255 heads, 63 sectors/track, 1106 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

#1Gb swap partition is here rest of disk is empty
   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        1106     8883913+  83  Linux

Disk /dev/sdd: 73.4 GB, 73407488000 bytes
255 heads, 63 sectors/track, 8924 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

# another partition is here that I can delete, rest of disk is empty
   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1         123      987966   83  Linux
/dev/sdd2             124        8924    70694032+  83  Linux


```

So I may just leave linux where it is and put /home on /dev/sdc with the swap partition.

---

### Post by wieman01 on 2006-09-20
This looks a bit confusing but here is what I think I have understood:
> 
/dev/sdb1 : x GB; /[root] partition
/dev/sdc1 : 1 GB; /[swap] partition
/dev/sdc2 : 8 GB; ext3 (free space)
/dev/sdd1 : x GB; /home partition

So you'd like to move **/home** from **/dev/sdd1** to **/dev/sdc2**, is that correct? Or is **/home** also on **/dev/sdb1**?

---

### Post by crokett on 2006-09-20
> **wieman01 said:**
> This looks a bit confusing but here is what I think I have understood:

So you'd like to move **/home** from **/dev/sdd1** to **/dev/sdc2**, is that correct? Or is **/home** also on **/dev/sdb1**?

/dev/sdd is a 70Gb drive and contains a 1Gb partiton formatted as swap.

/home is also on /sdb1.  I'd like to move it to /dev/sdd - that is as simple as creating a new partiton, copying the contents of /home and mounting it under /home? 

/dev/sdd1 is actually a swap partition - I'd also like Linux to start using that partition instead of /dev/sdc1.  Not sure how to do that.   Eventually I want /dev/sdc to contain a single partition - in future I want it to be a dedicated disk for video capture.

---

### Post by wieman01 on 2006-09-20
Ok, let's start with the easiest bit, ok? In order for Linux to recognize **/dev/sdd1** as your swap partition, we need to make the necessary changes in "/etc/fstab" as follows:
> sudo gedit /etc/fstab
From:
> **/dev/sdc1**       none            swap    sw              0       0
To:
> **/dev/sdd1**       none            swap    sw              0       0
Once you have done that it should be safe to restart the computer. Please make sure you make a safety copy of the file:
> sudo cp /etc/fstab /etc/fstab_backup
You can always reverse the changes using the Live CD. Don't worry. If this works, we'll continue from there.

---

### Post by crokett on 2006-09-20
I edited fstab and added lines for the swap partition on sdd as well as a new partition I created for /home.  I mounted the new partition under a temp directory and copied everything from the /home directory to it, then edited fstab to mount the new filesystem as /home.  that worked.  So I now have the swap partition on a new disk and /home on its own 15Gb partition. 

A question - disk manager had all my disks as inaccesible - could not modify them.  Using fdisk is not a problem but it would be nice to use disk manager.

---

### Post by wieman01 on 2006-09-20
> **crokett said:**
> A question - disk manager had all my disks as inaccesible - could not modify them.  Using fdisk is not a problem but it would be nice to use disk manager.
Terrific!

I don't quite understand the last question though... What are you trying to achieve? Do you want to change the disk labels? If so, I am not sure you do that to be honest.

---

### Post by crokett on 2006-09-21
No, I am thinking I can manage partitions - delete, create new ones, format, etc.

I thought about it though and what may be happening is Disk Manager may not want to mess with disks that have mounted partitions.  fdisk lets me work with those disks but says after I write the new partition table that before I can do anything with the new partitions I need to reboot.

---

