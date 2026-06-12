---
title: "Please help me to read ntfs."
date: 2006-08-12
forum: Absolute Beginner Talk
---

### Post by jincast90 on 2006-08-12
Ive tried to make it possible to read my ntfs partition, but I just cant. Its located at media/hda1 so I put this into the terminal:
sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

And now what? I tried to go to the golder media/windows, but I didint have permission to do so. So what should I do?

---

### Post by JerMe on 2006-08-12
Add it to your /etc/fstab instead:

[http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only](http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only)

then **sudo mount -a** to mount everything in your /etc/fstab

---

### Post by jincast90 on 2006-08-12
> **JerMe said:**
> Add it to your /etc/fstab instead:

[http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only](http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only)

then **sudo mount -a** to mount everything in your /etc/fstab

When typing sudo mount -a it tells me this:

mount: /dev/hda1 already mounted or /media/windows busy
mount: according to mtab, /dev/hda1 is mounted on /tmp/disks-conf-hda1

Now what?

---

### Post by JerMe on 2006-08-12
sudo umount /dev/hda1 && sudo mount /dev/hda1

Post your /etc/fstab if that doesn't work

---

### Post by jincast90 on 2006-08-12
I have no idea if it works, becouse I dont know where to look if it succeded. Where should I be able to acces my ntfs partition from if it went right?

This is what my /etc/fstab looks like after sudo umount /dev/hda1 and afterwords sudo mount /dev/hda1

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1    /media/windows ntfs  nls=utf8,umask=0222 0    0

---

### Post by JerMe on 2006-08-12
go to /media/windows and see if you can access anything ;)

---

### Post by jincast90 on 2006-08-12
> **JerMe said:**
> go to /media/windows and see if you can access anything ;)

Ah it works.

Thanks alot mate!!

---

