---
title: "Dual Boot, Dual Disc, Dual Access"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by flyguido on 2007-03-20
I am new to Ubuntu.  I have Dapper Drake and Windows XP.  I have two hard drives.

I want to be able to choose which OS to use when I boot up, and access the same audio, video, and image files from either system.

Right now I have Ubuntu installed on my smaller hard drive.  This hard drive has three partitions.  Ubuntu is on the first partition in ext3 (about 15 GB).  The second partition is in FAT32 and is empty (about 77 GB).  The third partition is "linux-swap" and is about one GB.

My larger hard drive has at least five partitions, but I am not sure what order they are in.  There are two in FAT32 - a 15 GB one and a 190 GB one.  The 15 GB FAT32 partition is empty but the 190 GB one has all my valuable audio, video, and image files.  There is also a 15 GB ext3 partition, on which Ubuntu is installed, and a 15 GB NTFS partition, on which Windows XP is installed.  If I boot from this disc, XP will always boot (XP was installed after Ubuntu).  Finally there is also a small swap partition on this disc.

I can run Windows XP or Ubuntu, but only if the certain hard drive is the master drive.  I would like to be able to choose which OS to use without opening up the computer and changing the physical settings on drives.  I have been able to access GRUB when booting Ubuntu, but it does not recognize my Windows XP installation.

Also, I can only access files on the same hard drive as my operating system.  So when I'm in Ubuntu, I can't access any of my audio, video, or image files, and when I'm in Windows XP, I can't access my smaller hard drive.  I want to be able to access files on both drives from either operating system.

---

### Post by zvacet on 2007-03-21
[http://ubuntuforums.org/showthread.php?t=275728&highlight=grub]("http://ubuntuforums.org/showthread.php?t=275728&highlight=grub")
And for second maybe try Samba.
[https://help.ubuntu.com/community/SettingUpSamba?highlight=%28samba%29]("https://help.ubuntu.com/community/SettingUpSamba?highlight=%28samba%29")

---

### Post by confused57 on 2007-03-21
> **flyguido said:**
> I am new to Ubuntu.  I have Dapper Drake and Windows XP.  I have two hard drives.

I want to be able to choose which OS to use when I boot up, and access the same audio, video, and image files from either system.

Right now I have Ubuntu installed on my smaller hard drive.  This hard drive has three partitions.  Ubuntu is on the first partition in ext3 (about 15 GB).  The second partition is in FAT32 and is empty (about 77 GB).  The third partition is "linux-swap" and is about one GB.

My larger hard drive has at least five partitions, but I am not sure what order they are in.  There are two in FAT32 - a 15 GB one and a 190 GB one.  The 15 GB FAT32 partition is empty but the 190 GB one has all my valuable audio, video, and image files.  There is also a 15 GB ext3 partition, on which Ubuntu is installed, and a 15 GB NTFS partition, on which Windows XP is installed.  If I boot from this disc, XP will always boot (XP was installed after Ubuntu).  Finally there is also a small swap partition on this disc.

I can run Windows XP or Ubuntu, but only if the certain hard drive is the master drive.  I would like to be able to choose which OS to use without opening up the computer and changing the physical settings on drives.  I have been able to access GRUB when booting Ubuntu, but it does not recognize my Windows XP installation.

Also, I can only access files on the same hard drive as my operating system.  So when I'm in Ubuntu, I can't access any of my audio, video, or image files, and when I'm in Windows XP, I can't access my smaller hard drive.  I want to be able to access files on both drives from either operating system.

Boot into Ubuntu, open a terminal(Applications---Accessories---Terminal), enter:
```
sudo fdisk -l
```
the -l is a small "L"
this will show your partition tables on both hard drives

Since you're able to boot Ubuntu from the smaller drive, once you determine which partition Windows is installed on your larger drive, you can add an entry to boot Windows from grub, something similar to what's listed in this thread:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

For Linux to be able to access other partitions, they must be mounted...see this thread for mounting various filesystems:
[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

For Windows to be able to recognize ext3 filesystems, you need this driver:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

Linux & Windows can read & write FAT32 partitions, hence some use it to share data between the 2 OS.  Linux can read NTFS, but not write to(unless you install a driver, which is beta or use at your own risk).

If your Linux partition on your larger drive is intact, you should be able to add an entry to grub on your smaller drive to boot it.

Hopefully, this helps give you some idea of what to do.

Added:  You might also want to post the output of these 2 files:
```
cat /boot/grub/menu.lst
```
menu.lst is short for menu.list
and
```
cat /boot/grub/device.map
```

If I understand correctly, you get a grub menu when you boot to your smaller drive, but not when booting to your larger drive with Windows.

---

