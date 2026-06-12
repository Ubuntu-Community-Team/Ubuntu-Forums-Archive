---
title: "Formatting to NTSC?"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by TJM2482 on 2007-03-13
Hey everyone, I have two hard-drives. Ubuntu is on my 80gb, and I want to format my 200gb drive to NTSC using Ubuntu software.

Problem is, the program wont let me format to NTSC (Only FAT and a couple other options).

Is there a way to format to NTSC? (I dont know how to install other programs, im new to Linux so I dont know the coding.)

---

### Post by taurus on 2007-03-13
Did you use gparted to format it to ntfs?  And make sure you unmount it first before you can format it.

---

### Post by Mr. C. on 2007-03-13
NTSC=National Television Systems Committee
NTFS=Windows NT+ file system

You can't with gpartd.  Read:

[http://www.gnu.org/software/parted/features.shtml](http://www.gnu.org/software/parted/features.shtml)


If you format to NTFS, be aware that write support is poor.  Are you trying to create a disk that will work in both environments (for read and write) ?

MrC

---

### Post by mi_were on 2007-03-13
> **TJM2482 said:**
> Hey everyone, I have two hard-drives. Ubuntu is on my 80gb, and I want to format my 200gb drive to NTSC using Ubuntu software.

Problem is, the program wont let me format to NTSC (Only FAT and a couple other options).

Is there a way to format to NTSC? (I dont know how to install other programs, im new to Linux so I dont know the coding.)

Can I assume that you mean NTFS? If so simply using windoze and be done with it.

---

### Post by qpwoeiruty on 2007-03-13
You don't want to format to NTSC, but NTFS. NTSC is a television format, NTFS is a filesystem that Windows uses

Why do you need NTFS, instead of,  say, FAT32, which is more easily readable by both Windows and Linux systems?

---

### Post by TJM2482 on 2007-03-13
> **taurus said:**
> Did you use gparted to format it to ntfs?  And make sure you unmount it first before you can format it.
I havnt formatted it yet, im trying to. 

I used the stock program (System > Administrator > Disks) to try to, but it only gives me the option for FAT32, JFS, XFS, ReiserFS, Entended 2, and Entended 3.

---

### Post by TJM2482 on 2007-03-13
> **qpwoeiruty said:**
> You don't want to format to NTSC, but NTFS. NTSC is a television format, NTFS is a filesystem that Windows uses

Why do you need NTFS, instead of,  say, FAT32, which is more easily readable by both Windows and Linux systems?
Ah yes, NTFS, sorry.

I tried to install a copy of XP onto my other drive, and it requested a drive "formatted for XP", when it was FAT32....

Is there a way to format to NTFS?

---

### Post by qpwoeiruty on 2007-03-13
You can format the drive directly from the XP install CD. If it said something about not being the correct type, it's probably seeing your first HDD formatted as ext3 or whatever and complaining.

Make sure you're choosing the right drive when you install XP. If you want to be really safe, unplug the Ubuntu HDD and then install XP. It should find the remaining HDD and not have a problem.

Note that you'll have to fix grub if you want to have it dual boot. XP's bootloader can't start Ubuntu.

---

### Post by x1a4 on 2007-03-13
> **TJM2482 said:**
> Is there a way to format to NTFS?

Try *cfdisk*.  It's a command line tool to partition and format hard drives with support for non-Linux file systems.  Read the *cfdisk* man page for info.

---

### Post by TJM2482 on 2007-03-13
I need a way to do it in Linux though, if it's possible. If not i'll have to put the drive in a Windows PC and format it then.

---

### Post by qpwoeiruty on 2007-03-13
What I'm saying is that if you're just installing XP, you can format to NTFS as part of the installation process.

Hit "Enter", when the screen says "To set up Windows now..."
You'll see your hard drives and partitions listed.
Scroll down until you see something like "XXXX MB Disk 1 at ID 0 on...". 
There should be a line with "Partition # [FAT32] ...". 
Press "L" to delete that partition, and then "C" on the now "Unpartitioned Space" to create a new partition. 
Choose "Format the partition using the NTFS file system" and hit enter.
After that, it's just a normal XP install. It's not necessary to format the drive first.

---

### Post by TJM2482 on 2007-03-13
> **qpwoeiruty said:**
> What I'm saying is that if you're just installing XP, you can format to NTFS as part of the installation process.

Hit "Enter", when the screen says "To set up Windows now..."
You'll see your hard drives and partitions listed.
Scroll down until you see something like "XXXX MB Disk 1 at ID 0 on...". 
There should be a line with "Partition # [FAT32] ...". 
Press "L" to delete that partition, and then "C" on the now "Unpartitioned Space" to create a new partition. 
Choose "Format the partition using the NTFS file system" and hit enter.
After that, it's just a normal XP install. It's not necessary to format the drive first.
I dont "have" the XP disc, which is why I gotta format the drive before....

---

### Post by qpwoeiruty on 2007-03-13
I'm assuming that you have a ghosted backup or some kind of recovery CD then.

Try this:

sudo cfdisk /dev/hdb
Choose Delete, then New/Primary <enter>, then Bootable, then Type and enter the correct partition identifier number  I think 07 is it for NTFS. Then Write...

Ed: Note. I'm assuming the drive to be hooked up as Disk 1 of IDE0. If you're suing SATA or something else, it may be different (like sda, etc). Substitute the correct drive for /dev/hdb

---

