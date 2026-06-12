---
title: "Windows won't read my external hard drive"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by Dapman01 on 2007-10-22
My Vista won't read my external hard drive after I put ubuntu on it.
I need to take ubuntu off of the external drive (I'm putting it on a dedicated machine) and make the external drive a backup drive again, how do I do so

---

### Post by Lord_Dicranius on 2007-10-22
The reason Windows won't read your external hard drive is because Ubuntu uses a file system that Windows is unable to read.  As for getting Ubuntu off of it, after you plugin the external hard drive and it shows up in My Computer, right-click on it and select format.  This'll allow you to completely overwrite the external hard drive with a file system that Windows will be able to read (NTFS, FAT32).

---

### Post by gary0 on 2007-10-22
If you want windows to read a linux partition/drive, you need to install on windows ext2IFS. Do a google for it.

Gary.

---

