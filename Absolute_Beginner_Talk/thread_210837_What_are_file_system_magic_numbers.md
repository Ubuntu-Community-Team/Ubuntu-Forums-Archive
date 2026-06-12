---
title: "What are file system magic numbers?"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by vinayasurya on 2006-07-07
Can anyone explain me simply what are file system magic numbers? I googled but the explanations were very complex. Also i want to know what this magic number does with linux? Also where inode table exists for reiser fs or it uses some other mechanism?

---

### Post by wombat20 on 2006-07-07
> **vinayasurya said:**
> Can anyone explain me simply what are file system magic numbers? I googled but the explanations were very complex. Also i want to know what this magic number does with linux? Also where inode table exists for reiser fs or it uses some other mechanism?

Not sure what you mean by "magic numbers".  Can you give an example?

In one notation the numbers on the end refer to partitions, whereas the letters are physical disks, so:

/hda1
is partition 1 on Hard Disk A.

and so on...

---

### Post by richlv on 2008-02-18
this is quite an old thread, but in case anybody else stumbles upon it :
partition types have numbers assigned, that you can view by launching fdisk against a disk and typing 'l'.

these seem to be a different thing than filesystem magic numbers - for example, you can view filesystem magic number for ext2/3 filesystems with 'dumpe2fs /dev/<filesystem> | grep "Filesystem magic number"'.

---

