---
title: "[SOLVED] how do i mount ntfs partition at startup?"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by vvvladut on 2008-02-08
Contents of /etc/fstab:

```
proc /proc proc defaults 0 0
# Entry for /dev/sda2 :
UUID=f81bec26-d0a2-4154-9ab0-9e0a906ba7b7 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda1 :
UUID=903418093417F148 /media/windows ntfs-3g defaults,locale=en_GB.UTF-8 0 1
# Entry for /dev/sda3 :
UUID=29ae6f64-5781-4352-91f7-5b14413f2641 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
```

I have another ntfs hard drive at /dev/sdb1 with one ntfs partition. How do I make it mount at start up? Do si just copy the line for sda1 and change the device name and mount point? What about the UUID?

Thanks!

---

### Post by Rocket2DMn on 2008-02-08
```
/dev/sdb1 /media/sdb1 ntfs-3g defaults,locale=en_GB.UTF-8 0 0
```
Don't forget to make the mount point first (you don't have to call it /media/sdb1 - you can get more creative than that).
```
sudo mkdir /media/sdb1
gksudo gedit /etc/fstab
sudo mount -a
```

---

### Post by vvvladut on 2008-02-08
Thanks...but what about the UUID part, don't I need that?

---

### Post by Rocket2DMn on 2008-02-08
No, that's just another way of identifying the partition.  You can if you want, though.
```
ls -l /dev/disk/by-uuid/
```

---

### Post by vvvladut on 2008-02-08
Thank you, that worked perfectly!

Can I ask one more question please? How do I get rid of the icons that get placed on my desktop for each ntfs partition? Can I make Gnome stop adding those?

Many thanks!

---

### Post by jan quark on 2008-02-08
run this
```

gksudo gconf-editor
```

navigate to apps > nautilus > desktop

check or uncheck the box to make the icon visible or hidden

---

### Post by vvvladut on 2008-02-08
Thank you, perfect!

---

### Post by jan quark on 2008-02-08
cool 
always a pleasure to help

---

