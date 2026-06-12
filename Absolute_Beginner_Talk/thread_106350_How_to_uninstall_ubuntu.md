---
title: "How to uninstall ubuntu ??"
date: 2005-12-20
forum: Absolute Beginner Talk
---

### Post by JnMrno on 2005-12-20
hi,
Hey, I was asked to uninstall ubuntu of a pc, I'd like to know how can I do that, putting back the Hard disk usable by the windows partition.

---

### Post by cstudent on 2005-12-20
Can you give some more info. Is Ubuntu on a machine with one hard drive? Is it dual boot with Windows? If we know a little more we can talk you through it.

---

### Post by JnMrno on 2005-12-20
Ok, it has 1 hard disk, with two partitions, one ubuntu and the other one Windows, before installing ubuntu, one was able to enter the two partitions from windows, I want it to be that way again.

---

### Post by cstudent on 2005-12-20
The short answer is you need to delete your linux partition so that it can be formated again with a file system XP recognizes. You'll also have to repair the MBR (master boot record). I don't know if you have an XP install disk. If so you can use it in recovery mode to take care of everything. The link below from Microsoft can explain it.

[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx)


If you have a live cd you can handle the deletion of the partition. You'll still need to come up with a way to fix the MBR. An older startup disk for Win98 or ME can do it with fdisk /mbr.

This thread can help you answer some questions about using a live CD.

[http://www.ubuntuforums.org/showthread.php?t=103367](http://www.ubuntuforums.org/showthread.php?t=103367)

---

### Post by JnMrno on 2005-12-20
thanks i´ll check it out ?

---

