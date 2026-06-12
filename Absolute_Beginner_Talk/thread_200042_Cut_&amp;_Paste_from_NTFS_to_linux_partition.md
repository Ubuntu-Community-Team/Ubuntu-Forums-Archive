---
title: "Cut &amp; Paste from NTFS to linux partition?"
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by tubunu on 2006-06-19
How do I go about cutting a file/files from a Windows NTFS and pasting it to my /home directory? I can copy and paste fine, but when I try to access the cut option it is greyed out. I have quite a few things to move to my linux partition and would like to free up space on windows one. Any advice? Thanks.

---

### Post by anaconda on 2006-06-19
Ubuntu doesn't have write support for NTFS partitions.

So you can only copy, not cut, because it would delete the files..and make changes.. which isn't supported.

Boot to windows, if you want to delete files from NTFS

---

### Post by msandersen on 2006-06-20
You could try [this guide]("http://www.ubuntuforums.org/showthread.php?t=142481") on enabling write support on NTFS partitions. NTFS is a proprietary format, and the Linux kernel doesn't have reliable write support for it, so it is turned off. There are 2 ways of getting write support, this guide is for one of them.
Or simply log into Windows and delete the files there.

---

### Post by dvarsam on 2006-06-20
You could also try this:

[http://www.ntfs-linux.com/](http://www.ntfs-linux.com/)

It is a product that helps you write to NTFS Partitions!

But you have to pay for it!

At the same time, it would be nice to know whether it works successfully 100% of the time...

If it really does, I would propably go ahead & buy it too!
(but I would want somebody to confirm that it works fine at _all_ times!!! - I wouldn't want to risk loosing my NTFS data files...)

Good Luck!

---

