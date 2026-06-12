---
title: "Newbie Question....."
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by Christopher on 2007-07-25
For the longest time I've been wondering, windows needs to be defragged every now & again. Why not linux? Thank you in advance.

---

### Post by FleetAdmiral74 on 2007-07-25
Well I can't tell you exactly why...I don't even know how in depth an answer you want, but here goes. 

First thing, its a different file system. ext3 (usually) vs ntfs. ext3 handles overhead and some other stuff differently, more efficiently obviously, and does not need the extra maintenance that ntfs requires. It does however, run a disk check every so often on boot up to make sure nothing is wrong, and will list contiguous file space.

The one thing you don't want to do is completely fill up your disk...please, like like 5% free at all times. Otherwise, it can cause issues, like not even being able to boot up and having to use a live CD.  

And if you want a good read...[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

Hope this helps

---

### Post by Christopher on 2007-07-25
Very nice thank you for the info & the link. ;)

---

### Post by ZacDavis on 2007-07-25
Windows needs to be defragged because it sucks...duh.  In reality if my memory serves me, it has something to do with the NTFS and the way Windows manages and stores data, which would be in a very bad way as you can by the way everything and defragmented, also it spreads out the files a cross the drive.

---

### Post by FleetAdmiral74 on 2007-07-25
> **ZacDavis said:**
> Windows needs to be defragged because it sucks...duh.  In reality if my memory serves me, it has something to do with the NTFS and the way Windows manages and stores data, which would be in a very bad way as you can by the way everything and defragmented, also it spreads out the files a cross the drive.

Yep, the problem is they leave no space after a file. So as soon as that file gets bigger, they have to write it to another location on the HD. Thats the simple explanation anyways. ext3 leaves a bit of space for natural expansion.

---

### Post by Christopher on 2007-07-25
awsome TY for the info.

---

