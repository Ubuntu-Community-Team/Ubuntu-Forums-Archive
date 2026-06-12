---
title: "File System Format"
date: 2005-12-26
forum: Absolute Beginner Talk
---

### Post by Shadow6363 on 2005-12-26
Alright, so I'm building a new computer that has a 74 GB as its main hard drive and two 120 GB in raid as secondarys.  On the main hard drive, I plan on triple booting between Windows Vista 64-bit, Windows XP 32-bit, and Ubuntu 5.10 64-bit.  On the raid, I plan on storing all my music and movies that I have and just about any other multimedia such as game backups.  Anyways, I was wondering what people would recommend I format the two 120 GB as.  I would like to be readable/writable under both Windows XP and Ubuntu; howver, I can not think of any formats that would allow me to do this.  NTFS is not writeable under Ubuntu, FAT32 has a 4 GB file size limit, and the two main linux file systems I'm considering (ext3, ReiserFS) need a program to be read under Windows XP.  If anyone knows any other file systems that would allow me to do what I want without necessarily opening the files through a certain program everytime or some setting I could set that would allow me to read/write in either os, please let me know.  Basically any solutions would be nice as I'm sure you guys will have better ideas on how to solve this than I do.  Thanks in advance.

---

### Post by gsdefender on 2005-12-26
If you are risky enough to use Captive on GNU/Linux, NTFS writing is possible. You get the original drivers from Microsoft and use them to read/write on your NTFS partition. It seems to me that there is no other workable aspect in the description you had given.

---

