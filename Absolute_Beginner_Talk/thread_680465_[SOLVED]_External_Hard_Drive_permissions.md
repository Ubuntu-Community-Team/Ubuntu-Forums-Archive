---
title: "[SOLVED] External Hard Drive permissions"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by pete_zahuat on 2008-01-27
I just reformatted my external hd to ext3 and cannot put any files on it.  The drive reads correctly but when I try to put a folder into it, it says only root has the permission to write files.

Anyone know how to fix this?

---

### Post by dcstar on 2008-01-28
> **pete_zahuat said:**
> I just reformatted my external hd to ext3 and cannot put any files on it.  The drive reads correctly but when I try to put a folder into it, it says only root has the permission to write files.

Anyone know how to fix this?

Install the **pysdm** package and then use System-Administration-Storage Device Manager to mount the drive, you should be able to mount it in a way that you can write to it with that utility.

---

### Post by pete_zahuat on 2008-01-28
I need a little more help...I installed the package, and the partitions list says "sda,sdb"  which one do I choose? 

Sorry complete newb here..

---

