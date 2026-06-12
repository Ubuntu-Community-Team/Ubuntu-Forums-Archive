---
title: "ext3 from Windows"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by weaver4 on 2007-01-05
Is there any driver/utility that will let me use Linux ext3 linux partitions on my dual boot system.

---

### Post by earobinson on 2007-01-05
[http://www.fs-driver.org/](http://www.fs-driver.org/) has worked for me in the past but I think you only get root access

---

### Post by CroEragon on 2007-01-05
Yes just root. It still works but can cause problems. When you install it you get two new drives. Swap is always unaccessible. Root partition sometimes returns window that ask you to format partition. DON'T TO THAT. You will delete your Ubuntu. I have seen many people doing it. It seams obvious but if you dont think it can happen

---

### Post by ajgreeny on 2007-01-05
You could also look at explorefs2 (do a google search for it), which will not let you write to ext3 but you can read and export from it to work on any files.  OK you will have to then re-import when you get back to ubuntu, but I can guarantee that it is totally safe.

---

### Post by livingtarget on 2007-01-05
I have Paragon Ext2FS v3, it costs money but you may be able to get it from some P2P network. It works very well and IMO beats most of the other drivers/utilities out there.

This will let you read/write and all, but it's probably better not to write extensively to it.

---

