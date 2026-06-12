---
title: "Help! Windows Partition Unallocated"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by Hillbilly Tilley on 2007-04-23
Here is what I have done.  I had edgy and xp dual booting from same drive.  With feisty I wanted to dual boot with xp on one drive and feisty on a separate hard drive.  With the live cd and gparted I deleted the ext3 partitions and resized the ntfs partition to full hard drive size.  Then installed feisty on the other hard drive.  Now in xp I show only part of the hard drive and in ubuntu I show the whole first drive as unallocated.  Is there any way without destroying xp to fix this?

---

### Post by solarix on 2007-04-23
> **Hillbilly Tilley said:**
> Here is what I have done.  I had edgy and xp dual booting from same drive.  With feisty I wanted to dual boot with xp on one drive and feisty on a separate hard drive.  With the live cd and gparted I deleted the ext3 partitions and resized the ntfs partition to full hard drive size.  Then installed feisty on the other hard drive.  Now in xp I show only part of the hard drive and in ubuntu I show the whole first drive as unallocated.  Is there any way without destroying xp to fix this?


Could XP boot? that´s in General the most important Question. You see only part of the Partition in XP ?

Is that right?

I personally would have a look with a tool like Partition Magic or Testdisk on the Partition Table, it could be that the Partition Table is damaged, if you´re lucky it migth not.

But you should check this first, Ubuntu wouldnt see the NTFS Partition if the Partition is damaged.

You will find Testdisk here [http://www.cgsecurity.org/wiki/TestDisk]("http://www.cgsecurity.org/wiki/TestDisk")


But be careful. :)

---

