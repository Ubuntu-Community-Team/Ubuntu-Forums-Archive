---
title: "mounted drive desktop icon"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by Aberrix on 2006-10-18
I have a seperate hard drive that is used for file storage. It currently mounts as /media/storage However I also have a desktop icon which is nice but I dont want an icon on my desktop any longer... trying to clean things up...

How can I remove the desktop icon, but leave the drive mounted, etc.

Thanks in advance.

---

### Post by CatKiller on 2006-10-18
If you change the mount point to /mnt rather than /media then you'll still get the drive mounted, but get no icon on the desktop.

Or you can run **gconf-editor** and change the /apps/nautilus/desktop/volumes_visible key - although that will turn off cd icons too, I believe.

---

### Post by Aberrix on 2006-10-18
so anything mounted with /media shows up on the desktop?
as opposed to mounted with /mnt ?

---

### Post by meng on 2006-10-18
correct.

---

### Post by Aberrix on 2006-10-18
okay...

I did a sudo vi /etc/fstab, and changed it from /media/storage to /mnt/storage then did a sudo umount /media/storage and then a sudo mount /mnt/storage and I got a desktop icon again.... ?

my /etc/fstab is looking like this

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sdb5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda1       /mnt/storage  ext3    defaults,errors=remount-ro 0       2
```

---

### Post by Aberrix on 2006-10-18
?

---

### Post by meng on 2006-10-18
Well I'm surprised but the gconf-editor solution should still work!

---

### Post by Aberrix on 2006-10-18
I rebooted and it's now gone and mounted as /mnt/storage

so that DID in fact work, just needed a reboot :)

Thanks

---

### Post by meng on 2006-10-18
Ugh, having to reboot to solve a problem, that's so ... Windows :)

---

### Post by Aberrix on 2006-10-19
> **meng said:**
> Ugh, having to reboot to solve a problem, that's so ... Windows :)

no doubt :P

---

### Post by mcduck on 2006-10-19
> **meng said:**
> Ugh, having to reboot to solve a problem, that's so ... Windows :)
Running 'sudo mount -a' would have done the job without a reboot.. ;)

---

### Post by Aberrix on 2006-10-19
> **mcduck said:**
> Running 'sudo mount -a' would have done the job without a reboot.. ;)

ahh yes, I remember that command now.

thanks for the tip ;)

---

