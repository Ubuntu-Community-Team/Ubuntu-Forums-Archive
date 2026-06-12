---
title: "/home folder in two physical drives"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by ign on 2007-08-31
I 'm sure this has been answered elsewhere, but I haven't been able to find it, please point to another thread if this has been explained before.

I have an old PC unning Xubuntu that I'm using as a home file server (Samba). It has a 60 GB HD, where the system is installed, the shared folder is also in there, there is a second 120 GB HD with two FAT32 partitions with media files init.

I'd like to know if it's possible to make the contents of the second HD accesible from the shared folder on the first one. I've tride to simply make a shortcut using the GUI, but the access to the files  is too slow. Is there a more "pro" way of solving this?

Thanks for your help :)

---

### Post by srunni on 2007-08-31
You could make a symlink: ```
ln -s [folder to link to] [link]
``` The only thing is that I've had file permission issues with Apache when using symlinks. I don't know if this will happen with Samba. I'm sure you could always add directories in the other hard drive to the Samba shared list as well.

---

### Post by jombeewoof on 2007-08-31
assume shared folder is 
/home/myname/shared
assume fat32 partitions are /dev/hdb1 and /dev/hdb2
```

sudo umount /dev/hdb1
sudo umount /dev/hdb2
mkdir /home/myname/shared/drive1
mkdir /home/myname/shared/drive2
chown myname:myname /home/myname/shared/drive1
chown myname:myname /home/myname/shared/drive2
mount /dev/hdb1 /home/myname/shared/drive1
mount /dev/hdb2 /home/myname/shared/drive2

```

update fstab
```

sudo nano  /etc/fstab

```
find /dev/hdb1 and 2 and change their mount points

---

### Post by jombeewoof on 2007-08-31
> **srunni said:**
> You could make a symlink: ```
ln -s [folder to link to] [link]
```

can symlinks be shared? I didn't think so. 
actually I kind of just assumed not so I never tried. 
that would be a whole lot easier than my method

---

### Post by ign on 2007-08-31
Symlink works great with Samba, I can read/write from my laptop.
Thanks!

---

### Post by Magneticgravity on 2007-08-31
Are you really IGN!?

---

