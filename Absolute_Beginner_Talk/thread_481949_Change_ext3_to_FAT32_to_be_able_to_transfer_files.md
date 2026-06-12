---
title: "Change ext3 to FAT32 to be able to transfer files"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by Specter043 on 2007-06-23
I have a 120 GB HD paritioned with Ubuntu and Windows.  I also have an 80 GB hooked up.  Right now it has a copy of Ubuntu on it, but I was told by a friend making it FAT32 would allow me to transfer files easily between the Windows Partition and the Ubuntu Partition.  How would I go about doing this?  And if this isn't what I need to do to be able to use it as a 'shared' HD, then what should I do?

---

### Post by forestpixie on 2007-06-23
Hi I have ext2ifs installed on my win partition - allow sme to read and write to my linux partition from within windows.

Oh and you might want the mountdiag tool (from same place) if you get problems accessing.

[http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html)

[http://www.fs-driver.org/troubleshoot.html](http://www.fs-driver.org/troubleshoot.html)

Good luck

---

### Post by moredhel on 2007-06-23
Also, make sure you don't give your linux partitions the same drive letter as some things that aren't connected, like mass storage devices etc. When that happened it's bad xD

EDIT: so drive letter Z would be safest :D

---

