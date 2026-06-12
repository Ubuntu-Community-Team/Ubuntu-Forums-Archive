---
title: "Partition Question"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by Hillbilly Tilley on 2006-08-03
I have installed unbuntu with xp on a dual boot.  I let the install pick the partition size which was 40gig for windows and 40 gig for  unbuntu.  Now I need more space for xp.  How do I repartition the hard drive so windows can have 60 gig and unbuntu will have 20gig without really messing up things.
     I also have a second drive which I would like to be able to use and share between both os's.  Anyone have a simple solution?

Thanx

---

### Post by Third Thoughts on 2006-08-03
> **Hillbilly Tilley said:**
> I have installed unbuntu with xp on a dual boot.  I let the install pick the partition size which was 40gig for windows and 40 gig for  unbuntu.  Now I need more space for xp.  How do I repartition the hard drive so windows can have 60 gig and unbuntu will have 20gig without really messing up things.

Any sort of partition software should work. You'll want to run it from a Live CD so that all your partitions are unmounted. You can use the Dapper LiveCD and gParted, or check out the System Rescue CD [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page) which has QtParted, or go with the PCLinuxOS CD [http://www.pclinuxos.com/news.php](http://www.pclinuxos.com/news.php) which has Disk Drake. To the best of my knowledge you can shrink Ubuntu's ext3 filesystem without hurting any data. Making the Windows NTFS partition bigger should be fine too, although you probably want to defrag in Windows first.

> 
I also have a second drive which I would like to be able to use and share between both os's.  Anyone have a simple solution?
Thanx

There are a number of solutions. The easiest would probably be to format that hard drive as a FAT32 partition. Both Linux and windows can read/write to FAT32 without any tweaking. However FAT32 is an ancient filesystem. If you're willing to do a little tweaking, you have two choices. You can format it as an ext3 system, which is the Linux default, and then install Ext2fs ([http://e2fsprogs.sourceforge.net/ext2.html](http://e2fsprogs.sourceforge.net/ext2.html)) to give Windows read/write support for ext2 and ext3 filesystems. Or you can format it as NTFS, Windows native file system format, and use ntfs-3g ([http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)) to give Ubuntu read/write support for NTFS formatted drives. Be warned that ntfs-3g is technically beta software, though from what I've heard it has no significant problems.

~Andrew S.

---

### Post by Hillbilly Tilley on 2006-08-07
Thanks for the help...but I ran into a snag. 
    First is started Unbuntu live cd and found the gnome partition program under system-administration.  I successfully resized the swap file.  Then I tried to shrank the unbuntu partition.  Here is where the problem starts.  I cannot put the free space before the unbuntu partition it will only let me put it after the partition.  Then when I try to enlarge the windows partition with the free space taken from unbuntu it says the partition is maxed out.
     My hard drive is like this  35g ntfs, 33g ext3, and 2g swap.  When I resize the ext3 it makes a space between the ext3 and swap where I cannot use it to enlarge the ntfs space.  It is like there is an unmoveable wall between the ntfs and the ext3.  There is a grayed out button for putting the space before the partition, but it will not let me use it.

Any suggestions?

---

