---
title: "kubuntu permissions"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by treborblack on 2006-08-28
Have added a second hard drive and spent the best part of three hours playing about all to no avail.

i cannot write to the drive as myself. however if i type in the konsole kdesu konqueror i can then drag and drop files. so format and mount point wise i'm happy. below is my fstab. what have i done wrong with the hdb1 line?

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda1 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
/dev/hda5 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/hdb1 /mnt/storage ext3 defaults 0 0

---

### Post by JNowka on 2006-08-28
Did you create /mnt/storage as root?  My guess is that you did.

Open the Konsole and enter command "sudo chmod 777 /mnt/storage"

You should be able to use the other drive now as anyone

---

### Post by treborblack on 2006-08-28
JNowka that did the trick:D thankyou ever so.

---

