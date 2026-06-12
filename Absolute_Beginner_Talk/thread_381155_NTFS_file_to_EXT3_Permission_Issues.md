---
title: "NTFS file to EXT3 Permission Issues"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by robinlennox on 2007-03-10
Hi all,

Just a quick one....

Will I have any permissions issue if I copy my files to an EXT3 partition and try to use them on a Windows Machine?

If I set-up the relient user and groups?

Regards

A Noob

---

### Post by mikewhatever on 2007-03-10
Windows can not read fro nor write to ext3. You need to install some additional drivers or create a FAT32 partition. Ubuntu can read from NTFS but can't write to. More drivers are available for that.

---

### Post by robinlennox on 2007-03-10
I have setup Samba....

And I managed to copy files from a Windows NTFS partition on a windows computer to my Ubuntu Server EXT3 partion without a problem.

How is that possible?

---

### Post by taurus on 2007-03-10
> **mikewhatever said:**
> Windows can not read fro nor write to ext3. You need to install some additional drivers or create a FAT32 partition. Ubuntu can read from NTFS but can't write to. More drivers are available for that.

Actually, Windows can read and write to ext2/ext3 just fine with [http://www.fs-driver.org](http://www.fs-driver.org).

---

### Post by robinlennox on 2007-03-10
OK, I am using Sambasmb.... I guessing the permissions from my work group would be copied across without any issue?

---

### Post by mikewhatever on 2007-03-10
Right, but fine is a questionable word here. From what I heard, it works great for some and doesn't work for others.

---

