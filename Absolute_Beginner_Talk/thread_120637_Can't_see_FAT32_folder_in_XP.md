---
title: "Can't see FAT32 folder in XP"
date: 2006-01-23
forum: Absolute Beginner Talk
---

### Post by aflatun on 2006-01-23
I am completely new to Ubuntu. I literally installed it 48 hours agon. I can't see a FAT 32 folder in XP.

Here are the details.

I am working with two hard drives and they are divided as follows:

Hd1 ~ 13 GB
/dev/hde1 * NTFS /media/hde1 ~10 GB
/dev/hde2   Linux / ~2.7 GB

HD2 ~ 160 GB
/dev/hdf1 fat32 /media/hdf1 ~40 GB 
/devhdf2 linux /home ~115 GB
/dev/hdf3 swap ~5 GB

Note: I recently installed a 160 GB internal harddrive but XP only allowed me to access 128 GB.

The fat32 folder use to be an NTFS folder and I could mount it in Ubuntu. I used Gparted to convert that to a FAT32 and can now use it in Ubuntu. But I can't see it in XP. 

I tried using DISKPART in DOS to see what was going on:
List DISK says there are two disks:
Disk 0 Online 13 GB (Free 0 B)
Disk 1 Online 128 GB (Free 0 B)

When I select Disk 0 and ask to list partitions, they are properly listed with 
Partition Type Size
Partition 1 Primary 9 GB
Partition 2 Unknown 3499 MB

When I select Disk 1 and ask for partitions, it just lists one partition
Partition 1 Primary 128 GB

Any suggestions?

---

### Post by Joeb on 2006-01-23
It sounds like the fat32 partition isn't initialized correctly.  If, while in XP, if you go into the Disk Management Tool (right click on my computer and select management and then select disk management under storage), does it show up as a fat32 partition?  You may need to reinitialize it (which will erase any information on it).  You can check out this link for more info: [http://www.seagate.com/support/kb/disc/howto/install_xp_disk_mgmt.html](http://www.seagate.com/support/kb/disc/howto/install_xp_disk_mgmt.html)

---

### Post by aflatun on 2006-01-24
[IMG]http://www.aflatun.com/ComputerMngt[/IMG]

[IMG]http://www.aflatun.com/DeviceProp[/IMG]
 
These are the screen shots from the Disk Management Tool.

It does not show up as a fat32 partition. But Ubuntu recognizes the partitions just fine and lets me save things to them. Do I need to format the FAT32 partition in linux? I have the /home directory in Ubuntu on this so I really don't want to format the second drive. Help.

---

### Post by Nrvnqsr on 2006-01-24
windows won't recognize FAT32 that is formatted by Linux, the only way is to format the drive is by windows instead. **But** if you try to format the partition, it will only format anything under 32GB, anything larger than that it will automatically format it to NTFS

---

### Post by Joeb on 2006-01-26
[QUOTE=aflatun]

It does not show up as a fat32 partition. But Ubuntu recognizes the partitions just fine and lets me save things to them. Do I need to format the FAT32 partition in linux? I have the /home directory in Ubuntu on this so I really don't want to format the second drive. Help.[/QUOTE]

Unless you have some Windows partitioning tool, I don't think you will be able to use the full drive as a fat32 under Windows.  Even if you do, I don't think that I would put my /home directory on it, since fat32 doesn't handle linux permissions.

It sounds like what you are trying to do is to be able to share stuff between Windows and Linux, and because of the write issues with NTFS, you are using fat32.

What I would suggest, is putting your /home directory on a linux partition (the type of which is up to you).  Then, under Windows, create your fat32 partition.  Once that is created, then back in Linux, make a symbolic link in your home directory to the partition.  When you want to access it under linux, you just access the symbolic link, which makes it look like any other directory.


Joeb

---

### Post by aflatun on 2006-01-30
Thank you to everyone who responded. Here is how I resolved the issue based on some advice here and experimentation. The first drive still have two partitions, one NTFS with XP on it and other ext3 for the / directory.  I formatted my second drive and created a 20 GB FAT32 in Windows and left the rest of the space unallocated. Then in Ubuntu install I created an ext3 partition for /home and also a small swap space. But I kept the total size of space used under 128 GB although I have a 160 GB harddrive. 

(I tried to use the whole space but then Windows XP stopped recognizing the drive, my hard drive manual says that this is because I have a old BIOS and can only use upto 128 GB unless I upgrade the BIOS?!) 

This seems to have worked just fine. I can use the 20 GB FAT32 space in both Windows and and Ubuntu.

---

