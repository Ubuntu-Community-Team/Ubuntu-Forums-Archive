---
title: "Best file system for moving between Ubuntu/MacOS/Windows"
date: 2010-01-07
forum: Apple Hardware Users
---

### Post by jamesey on 2010-01-07
I have an external hard drive that needs to be readable and writable between MacOSX, Ubuntu, and Windows. I also need to work with files over 4gb in size (which can't be done with Fat32, which happens to work with all 3 OS's)

I tried MacOS journaled, that didnt work. Before I start reformatting and doing a bunch of guess and check, I wanted to know if the answer was known.

---

### Post by Revolutionary101 on 2010-01-07
You could use NTFS it works well with Linux today, and it can work with Mac OS with a little tinkering. To make it Mac compatible, go here.

[http://www.lifehack.org/articles/lifehack/how-to-read-and-write-ntfs-windows-partition-on-mac-os-x.html](http://www.lifehack.org/articles/lifehack/how-to-read-and-write-ntfs-windows-partition-on-mac-os-x.html)

or here

[http://forums.macrumors.com/showthread.php?t=785376](http://forums.macrumors.com/showthread.php?t=785376)

I think that would be your best bet at a file system that works on all 3 main OSs.

---

### Post by Bucky Ball on 2010-01-07
Ntfs

---

### Post by jamesey on 2010-01-08
thanks! I didnt realize NTFS would be a simple answer, but it is.

---

### Post by Revolutionary101 on 2010-01-08
Glad I could help and don't forget to mark the thread as solved.

---

### Post by jamesey on 2010-01-12
My Windows and Ubuntu machines can read and write to my external hard drive formatted in NTFS. My Mac OS machine can only read. I installed MacFuse, but still can't get MACOSX to write to NTFS. 

I know this is a MAC OS issue, but maybe someone here will know what I have to do.

---

### Post by Tu1J4kXk8NUhMz on 2010-01-13
> **jamesey said:**
> My Windows and Ubuntu machines can read and write to my external hard drive formatted in NTFS. My Mac OS machine can only read. I installed MacFuse, but still can't get MACOSX to write to NTFS. 

I know this is a MAC OS issue, but maybe someone here will know what I have to do.

You need the NTFS-3G read/write driver as well. There's a link to it in the Lifehack link above. Also, you need to make sure to install MacFUSE BEFORE you install the R/W Driver. MacFUSE is a platform within OS X which facilitates interaction with different file systems. Those file systems require drivers, so if you install the other way around MacFUSE probably won't recognize the driver.

Oh, and to answer the OP, NTFS does work well between the three. You should know, though, that NTFS is read quite slowly in Mac OS X. I find that FAT32 works quite well...though I don't think I'd use it for anything but flash drives and compact hard drives (files must be under 4gb as you point out, and FAT32 isn't alway the most secure answer).

---

### Post by Bucky Ball on 2010-01-13
> **jamesey said:**
>  

I know this is a MAC OS issue, but maybe someone here will know what I have to do.

What you need to do is post a thread with a descriptive title describing your issue. :)

---

