---
title: "ntfs-3g"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by trickyzach on 2007-07-24
I have installed all the packages via package manager
The drives are NTFS
The mount fine without write access
I have booted into windows and run chkdsk
I have run ntfsfix

I still get this error in NTFS-CONFIG

Error: An error occurred when trying to configure /media/Backup, please retry. Thanks.

Any new ideas would be great =)

Thanks in advance

---

### Post by jcarlock on 2007-07-25
You can force the mount command to ignore errors and allow it to mount, but it doesn't sound like that is the error.  Remember when you mount that the /media/Backup directory must exist first and also you must be root, or using sudo, to mount devices.

Let me know.  Also if you can post the exact commands and errors you receive, that would help everyone.

JC

---

### Post by stchman on 2007-07-25
> **trickyzach said:**
> I have installed all the packages via package manager
The drives are NTFS
The mount fine without write access
I have booted into windows and run chkdsk
I have run ntfsfix

I still get this error in NTFS-CONFIG

Error: An error occurred when trying to configure /media/Backup, please retry. Thanks.

Any new ideas would be great =)

Thanks in advance

Go back into Windows and run a chkdsk /f on all NTFS partitions.  Then if you want to mount them with write capability follow this.

[http://www.stchman.com/part.html](http://www.stchman.com/part.html)

---

