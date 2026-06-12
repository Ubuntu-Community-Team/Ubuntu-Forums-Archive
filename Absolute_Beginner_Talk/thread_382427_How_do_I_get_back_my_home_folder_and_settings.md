---
title: "How do I get back my home folder and settings?"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by tikbjamin on 2007-03-12
So I did a clean install of Ubuntu 6.10 and made sure to NOT reformat my /home partition which was resized slightly smaller.  I don't see my documents folder in my /home folder and my Bookmarks and other settings for Firefox are not available.  I did save some of my documents but would love to get back my emails as well as my very important Firefox bookmarks and other settings.

How do I get back my home folder and settings?  

Here is my fdisk output.


Disk /dev/hda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         851     6835626   83  Linux
/dev/hda2            1024        4866    30868897+   5  Extended
/dev/hda5            1024        4605    28772383+  83  Linux
/dev/hda6            4606        4866     2096451   82  Linux swap / Solaris

Disk /dev/hdb: 540 MB, 540868608 bytes
255 heads, 63 sectors/track, 65 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1          65      522081    5  Extended
/dev/hdb5               1          65      522049+  83  Linux


Thanks,
TBJ.

---

### Post by Najand on 2007-03-12
Do you know in what partition your /home is?
If so (for example /dev/hdb1), add a line to your fstab:
/dev/hdb1  	/home  	ext3  	defaults  	0  0
And restart your computer.

---

### Post by tikbjamin on 2007-03-12
That was easy.  Thanks, Najand.  I noticed computer was a little sluggish at first, mainly Ok now.  Had to reinstall Firefox, Thunderbird, Flash, etc. but settings and data were intact.

Thanks again,
TBJ.

> **Najand said:**
> Do you know in what partition your /home is?
If so (for example /dev/hdb1), add a line to your fstab:
/dev/hdb1  	/home  	ext3  	defaults  	0  0
And restart your computer.

---

