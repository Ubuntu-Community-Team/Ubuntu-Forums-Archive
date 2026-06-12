---
title: "CFDisk / FDisk / help"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by matthewboh on 2006-10-20
I'm slowly getting there - thanks to all the help at these forums.  

Right now, I just added a new disk drive.  I formatted it with the tools that came with the disk drive, and they only allowed NTFS.  I would like to change it to ext3.  I tried running cfdisk, but was unsure which of the types to select.  Also, it mounts it on /dev/hdb1 which is a read-only file system.  How do I change the permissions, or do I try to change it to mount on /dev/hdb which is read/write/execute for everyone?

Thanks!

---

### Post by .t. on 2006-10-20
You cannot write to NTFS currently. It is too dangerous. However, to format as ext3, run "sudo mkfs.ext3 <device-to-format>". Then edit your fstab, accordingly, changing the line for the partition from "ntfs" to "ext3". You'll need to use "sudo nano /etc/fstab" to do that.

---

### Post by matthewboh on 2006-10-20
That was the missing piece!  Worked like a champ.

---

