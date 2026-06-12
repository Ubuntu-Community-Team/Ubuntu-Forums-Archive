---
title: "[SOLVED] Requesting help on choosing filesystem"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by m9ke on 2007-08-18
HI all-could use some pointers from the community re choosing a filesystem for a new (second) hard drive.  

Running Ubuntu 7.04 (Fiesty Fawn).  The original (first) drive is 20GB.  The added (second) drive is 500GB.  When I installed Fiesty, I followed all Installer defaults, so I think the original drive is what ever the installer defaults to.

I have installed the new hard disk, and am ready to format, partition and make its mountpoint.  Looked  around and found a document explaining exactly how to do this  at [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

WRT choosing filesystems it says:

> Drives that are going to be used only under Ubuntu should be formatted using the ext3 filesystem. For sharing between Ubuntu and Windows, I would recommend the FAT32 filesystem. If you are new to filesystems and partitioning, please do some preliminary research on the two before you attempt this procedure.

I am never going to install Windows on this box.  However I had already installed Wine on it before adding the new (second) hard disk, and installed a Windows app or two.  There will be .flac files and potentially windows files stored on the new drive.

For the new (second) drive, would you recommend ext3 or FAT32, and, so that I can learn more, what is your reasoning on this?

---

### Post by taurus on 2007-08-18
You cannot install Ubuntu on a fat32/ntfs filesystem.  You need to use ext3 filesystem.  And if you want to share stuff between Ubuntu and Windows, then create another partition and format that partition as either fat32 or ntfs.

But if you don't have Windows on that machine, then format it as ext3 since it's much better filesystem than either fat32 or ntfs.

---

### Post by m9ke on 2007-08-18
Thanks, Taurus.  Since I don't have Windows on this box, and won't ever, it sounds like ext3 is the best filesystem for the second drive, even if I put windows files on it.

---

### Post by taurus on 2007-08-18
Yes, you can put whatever files on the second harddrive, even Windows stuff.

---

### Post by DeHorde on 2007-08-19
And if for whatever reason you ever want to access the harddisk from windows (XP), check this page: [http://www.fs-driver.org/](http://www.fs-driver.org/) There's a FAQ about ext3 (the default filesystem in ubuntu) you might want to read just to know what's what.

---

### Post by se7en on 2007-08-19
Either Ext3 or [ReiserFS]("http://en.wikipedia.org/wiki/ReiserFS") is what I would choose. I have minimal experience with ReiserFS but I've heard nothing but good things about it.

If it were an external drive (in case you ever wanted to know), FAT32 would be your best bet for cross platform compatibility with both OS X and Windows

---

### Post by m9ke on 2007-08-24
Thanks, all for helping me sort this out.  Went with ext3 and all is working fine.

Marking Solved

m9ke

---

