---
title: "USB LaCie disk - only read-only!"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by rasmusbp on 2006-07-26
Hi 

I've bought a LaCie 250 GB external USB disk and it mounts perfectly, when I plug it in. Only problem is that I don't get permission to write anything on it. I've searched the forums and help pages, but I can't find any advice that I understand. ](*,) 

I'm very new to Linux and Ubuntu, so can someone please guide me through this - or refer me to something easily understandable? 

The disk is formatted as NTFS, since it has to be shared with XP and it has to contain files of 4GB+. 

Thank you!

---

### Post by Kobalt on 2006-07-26
Hello,

Ubuntu 6.06 doesn't come with NTFS write support natively. You will have to install a few things to be able to write on your disk...
You can find a good method of doing so [here]("http://www.ubuntuforums.org/showthread.php?t=217009"). :rolleyes: 

Cheers !

---

### Post by jordilin on 2006-07-26
NTFS is not very well supported by Linux. In any case, see this howto:
[http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs+3g](http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs+3g)

---

### Post by justinflavin on 2006-07-26
just reformat the Lacie drive as FAT32 , and you'll be able to read and write to it from both Ubuntu and XP.

---

### Post by Engnome on 2006-07-26
> **justinflavin said:**
> just reformat the Lacie drive as FAT32 , and you'll be able to read and write to it from both Ubuntu and XP.

> The disk is formatted as NTFS, since it has to be shared with XP and it has to contain files of 4GB+.

fat32 can't handle files bigger than 4gb.

My external is formatted with a 300 gb fat32 and a 100gb ext3 for those big files. Maybe you could have something similar but with ntfs.

---

### Post by rasmusbp on 2006-07-31
thanks everyone for your comments and advice. i tried following the ntfs-3g howto as suggested by jordillin, and it works perfectly now. i've kept the whole disk ntfs in order to put +4GB files on it...(and share it with xp)

cheers!!

---

### Post by jordilin on 2006-07-31
I would partition your usb hard drive in two parts. One in ntfs for you m$ win box and another part in ext3 for your linux one.
Edit: Well, if the ntfs-3g solution works, then Ok:D

---

### Post by Frank Golden on 2006-07-31
> **rasmusbp said:**
> thanks everyone for your comments and advice. i tried following the ntfs-3g howto as suggested by jordillin, and it works perfectly now. i've kept the whole disk ntfs in order to put +4GB files on it...(and share it with xp)

cheers!!
By NTFS not being well supported in linux it is meant that
"use at your own risk" (of drive corruption, damage etc.). A better scheme is format to ext3 and use a free utility to access in XP. See link below.

[http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)

Read instructions on web site before use.
A lot of linux experts don't recommend writing to NTFS from linux. Thank Bill Gates. NTFS is proprietary and any solutions
were "reverse engineer" solutions.

---

### Post by n.arciss.us on 2006-09-23
Does any one know if Mac supports ext3?? This would be ideal for my Lacie drive.

---

