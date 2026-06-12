---
title: "Hard eject for cd"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by pzs on 2007-10-06
I seem to be having trouble ejecting troublesome CDs. I think this one has some kind of DRM on it to stop it being read properly - that's fine, I'll do without ripping it. However, now I can't eject it. I've tried pressing the button, doing right-click/eject on the desktop and doing eject and sudo eject at the command line with no luck. I get this error message:

dm_task_set_name: Device /dev/mapper/Ubuntu-root not found
dm_task_set_name: Device /dev/mapper/hdb5 not found

I'm about to reboot the machine, which seems like a rather hard-core way to eject a CD.

Peter

---

### Post by Kosimo on 2007-10-06
try :

sudo eject /dev/cdrom

or:

sudo umount /dev/cdrom

---

