---
title: "[SOLVED] DVD drive is shown twice"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by zoopzoop on 2008-03-23
After a restart my DVD drive was shown twice (see screenshot).
It was not a big problem since both linked to the same location /media/cdrom0.
But then I inserted a different DVD and only one of the names was updated... the other one still said G4_25433 but also linked to the new DVD.
It's just annoying and I am hesitant to delete any of the links.
Anyone know how I can fix this?
Is there any command that can make Ubuntu re-check which drives are present and update the links on the desktop and in Nautilus?

---

### Post by mikeyphi on 2008-03-23
Looks like you have two instances of your DVD player - Could you post the contents of /etc/fstab

---

### Post by zoopzoop on 2008-03-23
/etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=97f59032-5fca-42dc-9ef2-88a853c66b50 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda4
UUID=b43dd830-d752-47e8-ba1e-3b314b467e19 /home           ext3    defaults        0       2
# /dev/hda1
UUID=0E1477F71477DFDF /media/hda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda1
UUID=A608354208351333 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=0d3622bd-2e49-4047-a21b-bff1db2ee1a4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

### Post by mikeyphi on 2008-03-23
Well - fstab looks OK, so the problem's not there!
If the two icons reappear after a reboot - only thing I can suggest is to go ahead and delete one copy of the icon.

---

### Post by jan quark on 2008-03-23
```
gksudo gconf-editor
```

navigate to apps > nautilus > desktop

check or uncheck the box to make the icon visible or hidden

perhaps this will work...

---

### Post by zoopzoop on 2008-03-23
Thanks, guys, I remove one of the icons and now everything seems to work fine!

---

