---
title: "NTFS Write permissions"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by Sprucey on 2006-07-20
Hi,

I'm new to Linux & I'm having trouble accessing to my windows NTFS partition.

I can access the partition & display all of the partition contents. I can even open jpg's, word docs etc, but when I try to amend a file (a word doc for instance) on the partition it tells me that I dont have permission!!

I'm mounting this partition automatically using fstab:

/dev/hdb1 /mnt/storage ntfs nlis=utf8,umask=0222 0 0

I have tried changing the umask entry to 000 (I read somewhere that 000 gives write access to all users, where 0222 only gives write access to root & read to all other users)& adding "ro" before "ntfs" all to no avail.

Am I doing something wrong?

PLease help.

---

### Post by sjhstorm on 2006-07-20
At present NTFS is read only, Paragon have a new driver that cant write to NTFS although I believe it is a bit hit and miss at present. Xandros has implimented this in their latest Xandros 4 distribution, although reading their forum some people are still having problems.

You could always set up a fat partion that both windows and ubuntu can read/write to.

---

### Post by qdvubun on 2006-07-20
try this new driver
[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

---

### Post by PriceChild on 2006-07-20
Please be VERY aware that NTFS writing is still experimental!!!

The open source community doesn't have the complete specs from MS and is guessing.

Backup ALL data on the ntfs partition before attempting ANY writing.

---

