---
title: "Mounting rw external ntfs hard drives"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by corwinspyre on 2007-04-04
Hi!  I was wondering how to mount my external usb hard drives formatted in ntfs in ubuntu (latest feisty, amd64).  I set my Windows partition to rw using ntfs-3g in my fstab:
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda6
UUID=99861045-668f-4331-8753-477326d2d896 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=F400E50000E4CAA6 /media/hda1     ntfs-3g    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=4f654c4d-5292-49f7-bb49-464eeb065bbf none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```.  Previously, I always put them in the fstab, but I don't know how ubuntu does it (since it is apparently not via fstab), so I figured I would ask to be sure I can or to find out if there is a better way to do what I want.  Thanks a lot for your help!<br /><br />
----------------------------------------<br />

----------------------------------------<br /><br /><br />
----------------------------------------<br />

----------------------------------------<br />

---

### Post by mssever on 2007-04-04
Have you seen [this thread]("http://ubuntuforums.org/showthread.php?t=217009")? I believe that Givre's patched version of pmount will do the trick. But I don't have a removable NTFS partition to test it on.

---

### Post by corwinspyre on 2007-04-06
Yep, that thread was basically what I was going to do.  I found, however, a tool called "NTFS Configuration Tool" in the Ubuntu packages via Synaptic that has in total two check boxes, one to make internal ntfs drives rw and one to make external ones rw.  It worked like a charm, though it turned out that one of my externals was dirty, so I had to run chkdsk via windows to get it to mount in other than ro (and it wouldn't mount at all after running the config tool until I fixed the errors)...just figured I'd post the solution inc ase others have the same curiousity

---

