---
title: "200G Volume"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by alphaniner on 2007-12-27
I installed Xubuntu with the alternate CD, made one partition on my slave drive and mounted it as /media/bucket.  In File Manager, it is showing up in my left frame (where userfolder, trash, desktop, etc. show up) as 200G Volume.  Is there a way to change this without reformatting the drive?  Also, is this the default behaviour for stuff mounted in /media?  Because I made a partition on my Ubuntu box after install and just mounted it in / and it doesn't show up like that, but my NTFS partitions which existed before installation did.

Lastly, I saw a lot of unanswered threads on this but, does anyone have any idea why my IDE HDDs and CDROM are showing up as sd_ instead of hd_?  This is with the alternate CD, a Live CD install of Xubuntu on the exact same hardware recognized them as hd_ devices.  Thanks.

---

### Post by bone2006 on 2007-12-27
/media will put a shortcut on your desktop while /mnt won't by default.  Open up fstab and take a look in there.  You don't need to format

SD should be for SCSI, SATA, and sometimes USB devices.  I really haven't compared liveCD to installation, but I'd assume it would change to be honest.   Things are mounted in ram, so I'd assume that where things are mounted would change from liveCD to installing on a partition.

---

