---
title: "usb flash write privileges"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by mistergq on 2007-05-27
I installed Kubuntu on a 4 gig thumb drive for a laptop that the HDD controller failed on.  It saved the laptop and my wife uses it now.

however, we are having a problem with a second thumb drive having write pages.  Files can be read from the thumbdrive, but we are not able to write to the second thumb drive.  I am not sure what the command line is to change the privilege to allow any user to write to the drive.

---

### Post by Viskovitz on 2007-05-28
The mount information of the second hard drive is probably in /etc/fstab. You can change the default permissions there. Can you please write the output of:
```
cat /etc/fstab
```

---

### Post by mistergq on 2007-05-28
>  # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sda2
UUID=873e1fb5-e570-4ed0-aecc-f21ec63449bf / ext2 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/sda1
UUID=e5b43e6a-2fdb-4413-ab05-f38e600a0ada none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/sdb1 /media/usb2 auto users,atime,auto,rw,nodev,noexec,nosuid 0 0



Here is the results of your request.  Its the sdb1 thumb drive.

---

### Post by Viskovitz on 2007-05-29
Well, I'm not an expert, but that option rw there should mean that write access is possible. Maybe you don't have the correct permissions to write to the folder? 
Doing an 
```
ls -l /media/usb2
``` 
should give you who's the owner and what the permissions are.

---

