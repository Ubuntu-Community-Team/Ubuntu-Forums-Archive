---
title: "Mount External HD for All Users"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by villindesign on 2006-09-03
Hello,

I have an external hard drive that contains much data. I want to share read write permissions with other users. If I make a new account, the new user can not access the drive when I am still logged in. I want to be able to let remote users access the drive at the same time I can access the drive.

The drive is automatically mounted in /media

Does anyone know how I should implement this?

Thanks, Britt

---

### Post by xyz on 2006-09-04
Run the following command in a console and post the output:
```
sudo gedit /etc/fstab
```

that way we can identify your external HD and see what permissions it's got.

---

### Post by villindesign on 2006-09-04
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

I sorta thought that since it was automounted, it would not have an entry in fstab. I even thought that I would have to start manually mounting the drive if I wanted it to be rw for myself and others. So, with the above fstab file, what should I do? Thanks.

Britt

---

