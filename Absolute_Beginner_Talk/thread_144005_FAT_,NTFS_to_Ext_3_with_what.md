---
title: "FAT ,NTFS to Ext 3 with what???"
date: 2006-03-13
forum: Absolute Beginner Talk
---

### Post by animesh on 2006-03-13
As suggested earlier i want to convert my FAT,NTFS to Ext 3 how do i do that?

In GParted the option of convert to is faded that is can't be applied even when i login as root.

---

### Post by bluevoodoo1 on 2006-03-13
Have you tried it with a Live CD? You can't change anything if the volume is mounted.

---

### Post by derelict on 2006-03-13
Can't you use [mkfs.ext3]("http://www.die.net/doc/linux/man/man8/mkfs.ext3.8.html")?

---

### Post by GoalieCa on 2006-03-13
The quick and easy solution is to backup your data, mkfs.ext3, and then copy the data back.

I'm not sure if a conversion from ntfs and fat to ext3 may be possible. Just thinking about how both file systems work make my head hurt trying to thing of how to write a program to safely convert.

---

