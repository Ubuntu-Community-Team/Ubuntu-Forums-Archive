---
title: "DVD Drive not mounting :S"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by Skyler0 on 2007-02-01
Okay, so when I put a DVD or CD in the drive, I load up the drive from in "Computer", and get this error:

```
mount: block device /dev/hdc is write-protected, mounting read-only

mount: /dev/hdc already mounted or /media/cdrom0 busy

mount: according to mtab, /dev/hdc is already mounted on /media/cdrom0
```

Here's my fstab, in case it helps.

```
# /etc/fstab: static file system information.
#
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
UUID=44a6ad58-5c88-4084-ba5f-987f4b5025bb / ext3 defaults,errors=remount-ro 0 1
UUID=4c386303-b77c-4afd-bdd7-33397af65789 none swap sw 0 0
/dev/hdc      /media/cdrom0               udf,iso9660 user,noauto 0 0
#/dev/         /media/floppy0              auto rw,user,noauto 0 0
/dev/sda1     /media/sda1     ntfs-3g     defaults,locale=en_US.utf8   0    0
/dev/hdb1     /media/hdb1     ntfs-3g     defaults,locale=en_US.utf8   0    0

```

Thanks :S

---

### Post by Skyler0 on 2007-02-03
don't mean to bump, but neone have any idea?

---

### Post by shareMenaPeace on 2007-02-03
Hi, just a thought but maybe it is allready mounted with something else?

Check the Desktop and if you mounted something try rightclick the Desktp Shortcut and unmount.

---

### Post by Skyler0 on 2007-02-03
It's not on the desktop, and if I go to "computer" and right click it there, mount is listed not unmount. And when I try mount it gives me the above error. Also if I right click it, and hit eject, it does open the tray.

---

### Post by Skyler0 on 2007-02-03
EDIT: Okay, I hit eject, then put the cd back in, and its working now :S lol. Idk... oh well its working now.

Thx

---

### Post by shareMenaPeace on 2007-02-03
Nice you got it, sometimes i have some irritating issues too but mostly restarting the x server or in some cases booting fix it.

Cheers

---

