---
title: "ZIPing along"
date: 2005-05-17
forum: Apple PPC Users
---

### Post by ktindle on 2005-05-17
Because Iomega ZIP disks are formatted to place all data in an extended FAT partition, to work around the limit of 256 files in the root of a primary partition, you must set up fstab with, in my case, hdd4 instead of simply hdd.

The dynamic device subsystem makes /dev/hdd for you after you add ide-floppy to /etc/modules.  It does not make /dev/hdd4.  And it will disappear after every boot.

These commands must run as root at system startup:

mknod /dev/hdd4 b 22 68
chgrp floppy /dev/hdd4
chmod 0660 /dev/hdd4

This is wonderful- where to place these commands in the startup of Ubuntu 5.04?
Or is one forced (or highly advised) to make your own "init script" from scratch?

---

### Post by mortensn on 2005-05-17
perhaps you could use
[FONT=Courier New]
post-install ide-floppy mknod /dev/hdd4 b 22 68 ;\
chgrp floppy /dev/hdd4 ;\
chmod 0660 /dev/hdd4
[/FONT]

in /etc/modules

Morten

---

### Post by ktindle on 2005-05-18
Well, I didn't think to try that, so I did try it...

No soap.  It is creative, and I thank you, but... nope.

So I created a new /etc/init.d/zipfix file with the commands, marked it as executable, and put a soft link in /etc/rc2.d/S90zipfix.

That did work.  Had to.  Brute force.  But it works.

I do get "not a valid device file" on the first access to the zip drive.  Just try it again, and it works, and works until a reboot.  I can live with that.

---

