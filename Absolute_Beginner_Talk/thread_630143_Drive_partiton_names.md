---
title: "Drive partiton names"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by Namingishard on 2007-12-03
All my partitions shows up fine but they have names like sda1 and two are named sda5.
Is there a way I can rename them to something different?
Having odd names like this makes it hard to remember which is which, Especially when two have the same name.

---

### Post by red_Marvin on 2007-12-03
As devices they will always have those names, but when you use them you can decide what name is used when they are mounted, like (example only):
*sudo mount /dev/sdb1 /media/music*
This would mount the device sdb1 (normally the first partition of the second hdd) so you can access its content in the folder /media/music.

!1 The mountpoint have to exist prior to mounting (*sudo mkdir /media/music* in this case)

---

### Post by Namingishard on 2007-12-03
That'll work, Thanks.

---

### Post by Namingishard on 2007-12-03
Follow up question.
sdb1, sda1 ect stay in the the "Places" list. Is there anyway to get em off of there?

---

### Post by WorldTripping on 2007-12-03
If you rename the volume label, then the name will appear on the desktop etc when mounted, rather that the generic 'disk', 'disk-1'.

[https://help.ubuntu.com/community/RenameUSBDrive]("https://help.ubuntu.com/community/RenameUSBDrive")

[http://ubuntuforums.org/showthread.php?t=423245&highlight=volume+label]("http://ubuntuforums.org/showthread.php?t=423245&highlight=volume+label")

You also have to edit fstab to tell your machine where to mount the drive.

The mount point does not have to exist beforehand using this method.

I think to stop stuff appearing in 'Places', set the mount point to /dev/mnt/ rather than /dev/media.

---

