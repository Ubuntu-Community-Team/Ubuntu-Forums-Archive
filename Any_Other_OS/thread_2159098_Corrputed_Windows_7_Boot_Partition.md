---
title: "Corrputed Windows 7 Boot Partition"
date: 2013-07-01
forum: Any Other OS
---

### Post by Systmfdwn147 on 2013-07-01
Hello all, I tried to boot onto my hard drive with windows 7 installed on it and got an error saying that windows 7 was inaccessible. After trying to get it to work I was not successful. Later on I opened up gparted and saw this:

[[IMG]http://s18.postimg.org/wkfjbntn9/Screenshot_from_2013_07_01_18_23_30.jpg[/IMG]]("http://postimg.org/image/wkfjbntn9/")

I'm at a loss for how to correct this without completely reinstalling windows.

---

### Post by oldfred on 2013-07-01
That is really a Windows 7 issue.
       [http://www.sevenforums.com/](http://www.sevenforums.com/)

But NTFS does have a backup PBR or partition boot sector. You can often recover the Boot Sector with testdisk.

This is specifically for those who installed grub2's boot loader to the PBR, but the solution is the same.
Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

OR:
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

---

