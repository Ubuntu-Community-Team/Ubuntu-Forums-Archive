---
title: "[SOLVED] need file permissions"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by staticvoid on 2007-11-28
So,

I can't write to this disk and I can't seem to change the file permissions,

chmod 777 /media/disk -R
chmod: changing permissions of `/media/disk': Read-only file system


its just a USB pendrive. yesterday I could write to it now I can't.

Please help, its urgent..

sv

p.s. I've tried right click and changing permissions in root as well, I just don't know whats going on. I can't even write stuff to it when I am in root. So is there a command I can put in that will tell me who exactly owns the disk? thanks

---

### Post by staticvoid on 2007-11-28
Ok, and this is strange:

[IMG]http://i71.photobucket.com/albums/i123/broinjc/screenshot1-2.png[/IMG]

---

### Post by hyper_ch on 2007-11-28
what file system is on the usb stick?

---

### Post by qqzhenyi on 2007-11-28
what is the filesystem of the USB drive? maybe you mounted it read-only?

---

### Post by staticvoid on 2007-11-28
its now FAT32, i reformatted it with windows. And it works now.
I probably did mount it read only.

I still don't get why I could not change the file permissions. I mean: How can I mount is read & Write? not read only...

I'll mark this thread as solved, since I listed the command to chmod file permissions.

sv

---

### Post by qqzhenyi on 2007-11-28
maybe u need to add something to your /etc/fstab file:
```
/dev/hd<xX> /mnt/usb vfat users,noauto,uid=1000,gid=100,fmask=0113,dmask=0002,locale=en_US.utf8 0 0
```

if you don't want to edit your fstab file,
```
mount -t vfat -o remount,rw /dev/hd<xX> /mnt/usb
```

---

### Post by staticvoid on 2007-11-28
ok, thanks. those are helpful commands :)

sv

---

