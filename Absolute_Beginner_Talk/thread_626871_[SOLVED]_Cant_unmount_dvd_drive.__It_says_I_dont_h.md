---
title: "[SOLVED] Cant unmount dvd drive.  It says I dont have permissions to....only root."
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by Tdukes on 2007-11-29
I cant even eject media due to this conflict.

---

### Post by master_kernel on 2007-11-29
Can you post a screenshot of the error? Also, does this happen constantly? Usually this will happen when Ubuntu locks the disk in for some reason. It can be fixed by rebooting.

---

### Post by Tdukes on 2007-11-29
[IMG]http://img.photobucket.com/albums/v618/Tommydukes/Screenshot-gnome-umount.png[/IMG]

[IMG]http://img.photobucket.com/albums/v618/Tommydukes/Screenshot-gnome-eject.png[/IMG]

[IMG]http://img.photobucket.com/albums/v618/Tommydukes/Screenshot-Error-kio_media_mounthel.png[/IMG]

---

### Post by lespaul_rentals on 2007-11-29
```
sudo umount /media/cdrom0
```

---

### Post by philinux on 2007-11-29
This is what my /etc/fstab looks like

```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```

scd0 is my dvd player.

check your fstsb

sudo gedit /etc/fstab

---

### Post by Tdukes on 2007-11-29
> **philinux said:**
> This is what my /etc/fstab looks like

```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```

scd0 is my dvd player.

check your fstsb

sudo gedit /etc/fstab

I dont see any issues


/dev/hdb        /media/cdrom0   udf,iso9660 user,auto,exec 0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,auto,exec 0       0

/dev/sdb5 /media/Media ext3 rw,suid,dev,exec,auto,user,async 0 0
/dev/sdc5 /media/Storage ext3 rw,suid,dev,exec,auto,user,async 0 0

---

### Post by Tdukes on 2007-11-29
> **lespaul_rentals said:**
> ```
sudo umount /media/cdrom0
```

ok, that got it unmounted.

---

### Post by nikoPSK on 2007-11-29
glad you got helped before I could come here ;)

---

### Post by Tdukes on 2007-11-29
Thanks guys.  Without this forum I would be one frustrated person.

---

### Post by nikoPSK on 2007-11-29
me too:lolflag:

---

