---
title: "Cant boot XP anymore after dual-boot install"
date: 2006-07-09
forum: Absolute Beginner Talk
---

### Post by illadelphian on 2006-07-09
Linux newbie on the block....help me out guys!
I had XP installed initially (sda2 NTFS).  Then I installed Dapper in sda3 EXT, but I don't have an option to boot windows again. I can only boot linux.

here is my sudo fdisk -l
device     boot End Blcoks Id System
/dev/sda1                      w95 fat32
/dev/sda2                      hpfs/ntfs
/dev/sda3   *                  linux   
/dev/sda4                      swap

my dmesg | tail showed NTFS- fs error (device sda2): ntfs_fill_super(): Not an NTFS volume.

My guess is that I messed up the master boot record.  I can provide more info.....

---

### Post by molly_001 on 2006-07-09
Please see this thread -- another user with the same problem on this particular evening.

This thread is located at:
[http://ubuntuforums.org/showthread.php?t=212351]("http://ubuntuforums.org/showthread.php?t=212351&goto=newpost")

---

