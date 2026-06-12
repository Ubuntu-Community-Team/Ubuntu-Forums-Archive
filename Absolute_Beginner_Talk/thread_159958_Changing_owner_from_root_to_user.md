---
title: "Changing owner from root to user"
date: 2006-04-13
forum: Absolute Beginner Talk
---

### Post by essendon on 2006-04-13
I just put in a new hard drive into my computer.  It has two partitions.  It is a slave to the drive that has ubuntu on it.  I fomatted the partitions with ubuntu and set a mount path.   The only thing is, I can't write to the drives as a user.  How can I change the ownership of the partitions from root to the user that I want?

---

### Post by taurus on 2006-04-13
You can change the permission in /etc/fstab, if you use it to mount second harddrive!  What does your /etc/fstab look like then?  Open a terminal (Applications -> Accessories -> Terminal) and paste the output of this command from the prompt...
```

more /etc/fstab

```

---

### Post by essendon on 2006-04-14
This is the result:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by taurus on 2006-04-14
Looks like you don't have your slave drive (two partitions) mount at boot!  Tell me what format/filesystem they are (/dev/hdb1 & /dev/hdb2) and where you would like to mount them!

---

