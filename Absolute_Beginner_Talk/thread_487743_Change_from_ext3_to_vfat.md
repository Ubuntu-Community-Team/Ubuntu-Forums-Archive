---
title: "Change from ext3 to vfat"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by dhar2112 on 2007-06-29
I have formatted my external hard drive to ext3, but realized now that since it's a media drive, I'd probably need it to work in Windows, as well.  How do I reformat it to vfat, or is that the way I want to go to get it to work in both O/S?

Thanks!

---

### Post by Outrunner on 2007-06-29
There's a program for Windows that you can use to read ext3(or was it just ext2?), I think. Not sure what it's called, however. You can use Gparted to reformat the drive, by the way

---

### Post by Cypher on 2007-06-29
The program to access EXT3 filesystem in Windows is called [FS-Driver]("http://www.fs-driver.org/").

And VFAT is limited in size, so you really either want EXT3 or NTFS on there anyway..

---

### Post by hardyn on 2007-06-29
You can get a pretty big VFAT drive, but i don't know if there is a way to convert filesystems without a reformat.  It has worked well for my external media drives.

it is limited to files smaller than 4gb, but that is VERY rare for me, i don't know about you.  I don't believe there is any reasonable drive size limit, MS imposes a 32GB limit (i have 320GB VFAT drive), but this is arbitrary, and has nothing to do with the FAT32 spec.

---

