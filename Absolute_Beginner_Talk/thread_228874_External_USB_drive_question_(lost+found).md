---
title: "External USB drive question (lost+found?)"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by cheway on 2006-08-03
Hi all,

I have a 40 gig external USB drive that I want to use for backup - I formatted the drive with the ext3 file system, and it's appeared on the desktop, everything is good.

However, there is a folder called "lost+found" on the disk (I haven't put it there, the disk has only just been formatted afterall), and I cannot move or delete it. What is it??

Also, I cannot transfer my files to this drive without root permission - is there any reason for this? I want this drive to just behave like an ordinary flash disk, and allow me to plug/unplug and allow file transfers so that I can do my backup.

Thanks.

---

### Post by bonzodog on 2006-08-03
Do not worry about the lost and found folder on the disk...it is needed by the filesystem, to put bad files or clusters in a fsck. It shouldn't really be taking up any room on the disk.

---

