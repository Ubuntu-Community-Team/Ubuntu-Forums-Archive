---
title: "USB Jumpdrive not working"
date: 2005-05-27
forum: Absolute Beginner Talk
---

### Post by pravit on 2005-05-27
I'm trying to get my USB jumpdrive working with Ubuntu. It detects it properly, and even opens it up so I can see the contents, but it seems it isn't writing to it correctly. I can copy and paste files in to it, no problem, but then I take it out, put it back in, and the files are gone. It seems I have no write permissions. I tried doing this(it mounts to /media/usbdisk):
chmod 777 /media/usbdisk
chmod 777 /media

but it didn't do anything. Also added a line in /etc/fstab for sda1(found a line somewhere) but it didn't do anything. I'd appreciate any help. Thanks!

---

### Post by 23meg on 2005-05-27
can you post the line you added to your fstab? you should mount it with the rw option.

---

### Post by pravit on 2005-05-27
/dev/sda1 /media/usbdisk auto noauto,user,umask=000 0 0

edit: I got it working with /dev/sda1 /media/usbdisk vfat auto,rw,user 0 0. Thanks!

---

### Post by 23meg on 2005-05-27
you're welcome; happy that you got it working.

---

