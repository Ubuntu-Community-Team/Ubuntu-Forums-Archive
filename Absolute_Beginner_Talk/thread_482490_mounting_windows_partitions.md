---
title: "mounting windows partitions"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by debone on 2007-06-23
I just started with ubuntu edgy.
The windows partitions (sda1 and sdb1) are already seen by the Nautilus as disk and disk1.
However they are  not listed in fstab.
If I mount them  I've to type my password, then the icons appear on the desktop and all works well.
How can I let these partitions mount automatic?

I tried to modify fstab with 

/dev sda1	/media/winc	ntfs	nls=utf8,umask=0222 0    0
/dev sdb1	/media/wind	ntfs	nls=utf8,umask=0222 0    0
and created the directories. 
However, no success.

Anyone has a clue?

---

### Post by raja on 2007-06-23
In the fstab entry you are missing a slash in /dev/sda1 - hope thats just a typo?

If you are planning to write those drives too, you should install ntfs-3g and ntfsconfig - it makes it easy to mount them.

---

### Post by debone on 2007-06-23
In a way it was a type was a typo...  ;).
Thanks for helping out, it works now ;)

---

