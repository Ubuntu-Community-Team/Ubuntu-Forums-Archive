---
title: "Ext 3 vs Fat 32?"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by cwrann on 2007-09-03
I have an external hard drive that was formated to NTFS and is now wiped clean and ready to be reformatted. I use this hard drive to get and give files to both Mac and Windows computers. I know that Mac, Windows and Ubuntu can read and write in FAT 32. I also know that you can Install a driver for windows to read and write in EXT 3, I don't know if there is one for Macs.

The computers I share files with are not my own. 

Would it be better to reformat this hard drive with EXT 3 or FAT 32?
Why is EXT 3 better for Ubuntu, Is it better for the others as well?
If there are drivers for both the other OS's to read and write in EXT3 can I have them on the external hard drive and be able to quickly install them on others computers?

---

### Post by taurus on 2007-09-03
There is a driver to read ext2/3 for mac, [https://sourceforge.net/projects/ext2fsx/](https://sourceforge.net/projects/ext2fsx/).

---

### Post by bvmou on 2007-09-03
Ext 3 has many basic design advantages as far as data integrity, etc, but if you are just using this to share files FAT 32 is likely to be much easier.  You can also have a fat32 partition on the disk specifically for sharing and a journaled one like ext3 for your own backups.

---

### Post by cwrann on 2007-09-03
I ended up using the FAT 32 file system because it sounds like it would be less of a hassle for the people who I am sharing files with but when I reformated it using Gnome an error message pops up saying that I cannot mount the device because:

The volume uses the fat32 file system which is not supported by your system.

---

### Post by nowshining on 2007-09-03
ext 3 is better fat32 has a size limit up 65000 or so folders/files where it starts to degrade - NTFS + ext 3 should be rid of this and unlimited plus NTFS + ext are easier to maintain and use.. I higly suggest ext3 for linux...

---

### Post by nowshining on 2007-09-03
in other words the default for feisty 7.04...

---

### Post by cwrann on 2007-09-03
I understand that ext 3 is the superior file system for linux, For my internal hard dive I use ext 3, however this external hard drive is used to share folders with people who have computers that do not have linux based system. Thats the reason I went with FAT 32 for my external hard drive. Now that I have converted it to FAT 32 from NTSF (Ubuntu used to be able to read it in NTSF) I cannot mount the drive at all. I thought that FAT 32 was automatically supported in Ubuntu, Is there something I need to modify in order to mount this drive?

---

### Post by nowshining on 2007-09-03
a filesystem should have nothing to do with sharing a file sharing should work just fine as long as the file format itself is in the supported operating systsm format and can read it, example uisng an windows exe file needs not to look at the underlining filesystem but whether the operating system itself can support it.

May you can give some example of what you want to share..

WAIT n/m i get what you mean typing the above lolz.. :) um.... lolz... :)

---

### Post by stmiller on 2007-09-04
> **taurus said:**
> There is a driver to read ext2/3 for mac, [https://sourceforge.net/projects/ext2fsx/](https://sourceforge.net/projects/ext2fsx/).

This driver is buggy for write support. Reading is okay, but use at own risk for writing, IMO.


Most people recommend [ntfs-3g]("http://www.ntfs-3g.org/") for this sort of thing.

Stable ntfs read/write support for Mac, Windows, Linux.

---

### Post by bvmou on 2007-09-04
Maybe try vfat?  I should have been more clear about this to the extent possible given my (very) limited understanding.  File Allocation Tables are the original storage format that stored data in fixed 12, 16, then 32 bit blocks.  You may remember weird file names like Spread~t.xls and so on, that was a constraint of the title being stored in a discreet block with a limited size.  To avoid that limitation the standard became Virtual File Allocation Tables.  This is still a 32 bit file allocation table but it has some user-transparent super-structure.  My suggestion would be to try VFAT and report back success or failure, I am curious about how this goes and apologize for answering with incomplete information.

Also there is some Microsoft patent trolling that may have pushed FAT support into the non-free repositories, you can read about that and other specifics here [on wikipedia.]("http://en.wikipedia.org/wiki/File_Allocation_Table")

---

### Post by cwrann on 2007-09-04
I would love to try vfat or any other type of file system however what I need is a file system that I can read and write on with my ubuntu system as well as the Mac and windows systems used by others without them having to do anything special. I need to be able to plug my usb external hard drive into their computers and give and receive files. I think that FAT 32 is the best file format for this right now, even though ext 3 seems to be the best over all.

My new problem is that when I reformated to FAT 32 I thought that my computer would automatically mount it but it cannot and says that FAT 32 is not supported by my computer.

---

### Post by bvmou on 2007-09-05
I think that FAT32 proper has been deprecated in Windows and Mac as well as Linux and that VFAT is the solution on all three.  VFAT is an extension to FAT32 that has been used since the mid-90's, you may want to reformat to it.

---

### Post by anaconda on 2007-09-05
I dont like using fat32 in linux, because you can't have bigger than 4GB files, and the other annoying thing when you click a .txt file (or .pdf?) it will ask "do you want to display or execute?", because every file in fat32 partition will be marked as executable! 

so maybe ntfs would be best for you?

ext3 isn't good IF you want to use your hd  in several windows machines, which aren't yours.  

OK! maybe ext3 isn't for you, but if you try it sometime.. remember to run  
tune2fs -m 0
on it. otherwice you will lose 5% of the drives space reserved for root user..

---

### Post by cwrann on 2007-09-05
I am using gparted for my formating and partitioning, gparted does not give me a vfat format option, any suggestions?

---

### Post by lukemack on 2007-09-12
Did you get a solution / answer to this? I want to share an external usb drive between ubuntu and windows. I don't want to use NTFS because then I cant take the drive away and use it on another  system - windows stops you doing that and you have to go through the pain of taking ownership of the drive etc. Also, if you use ntfs-3g, if you forget to remove hardware safely, it won't mount in linux, it leaves trash folders on the drive etc etc - all very messy. I don't care about security on this drive. I want ease of use and portability. It would be nice if my brother's mac could access it too.

i thought i would therefore format the drive to fat32 to make life easier but ubuntu will only mount it as read only. is vfat the answer here? am i missing something?

i created a /mnt/usb directory and did mount -r /dev/sdb1 /mnt/usb but can't write to the drive. it shows in the df list:

/dev/sda1     ext3   112396676   4618660 102068520   5% /
varrun       tmpfs      517520       232    517288   1% /var/run
varlock      tmpfs      517520         0    517520   0% /var/lock
procbususb   usbfs      517520       104    517416   1% /proc/bus/usb
udev         tmpfs      517520       104    517416   1% /dev
devshm       tmpfs      517520         0    517520   0% /dev/shm
/dev/scd0  iso9660     2291232   2291232         0 100% /media/cdrom0
/dev/sdb1     vfat   244136352        32 244136320   1% /mnt/usb


(its the last entry)


thanks for any replies.

---

