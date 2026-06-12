---
title: "ext3 versus FAT32 (dual-boot XP/Ubuntu data partition)"
date: 2006-03-18
forum: Absolute Beginner Talk
---

### Post by psquared89 on 2006-03-18
I'm setting up a dual-boot system and I was wondering if people thought it was better to have a seperate FAT32 partition for Ubuntu and WinXP to read, or if something like [this](http://www.fs-driver.org/index.html) (an XP ext2/3 driver) would be better.  I know that the XP driver doesn't preserve permissions, but this is only for a home computer, so I'm not worried about that.

If it makes a difference, the dual boot will be done on two HDs, a new 200GB HD for Ubuntu (a Seagate, only $30 from CompUsa, a steal!) and an existing 120GB HD with XP already installed.  I'd like the shared partition to be on the 200GB HD as the Windows drive is already ~2/3 full.

Any advice/knowledge on the subject is appreciated!

EDIT:  With a little more hunting, I found [this](http://ext2fsd.sourceforge.net/index.htm) also.  It's a different XP ext3 read/write driver.

---

### Post by Ramses de Norre on 2006-03-18
I use the first driver you mentioned in windows and it works perfect.
FAT is really inferior to ext3.

---

### Post by adamkane on 2006-03-18
You haven't really described what you want. If you want full read-write access between Ubuntu and Windows, see:
[http://www.ubuntuforums.org/showthread.php?t=142481](http://www.ubuntuforums.org/showthread.php?t=142481)

The best policy is to run Windows and Ubuntu on different machines, but it's your data. Remember to always store your data on a non-OS partition.

This topic has been covered many times, so you've got some reading to do.

---

