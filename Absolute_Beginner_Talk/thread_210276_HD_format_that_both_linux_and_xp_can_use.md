---
title: "HD format that both linux and xp can use?"
date: 2006-07-06
forum: Absolute Beginner Talk
---

### Post by nightanole on 2006-07-06
I have some 400gb hd's that have iso's on them and i need for both xp and linux to read and write to.  Is there a format that will make both os's happy?  fat32 wont work due to small partition size and 4gb limit on files.  I dont mind if i have to install a driver for xp to read the linux format or vis versa.  ntfs looks alittle unsafe for having linux access it.

---

### Post by Iarwain ben-adar on 2006-07-06
Hi,
well, there's some program for Xp that it can read Ext2 =)
i think it's called fs-driver or something like that :D

Here's the link to the program : [http://www.fs-driver.org/download/Ext2IFS_1_10b.exe](http://www.fs-driver.org/download/Ext2IFS_1_10b.exe)

Maybe you could format them to Ext2 :D


Iarwain

---

### Post by LKRaider on 2006-07-06
Yes, it is better to use ext2 or ext3 on the partition, and install the driver on windows. NTFS support is not reliable on linux yet.

Some ext drivers:
[http://ext2fsd.sourceforge.net/](http://ext2fsd.sourceforge.net/)
[http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm](http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm)
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

