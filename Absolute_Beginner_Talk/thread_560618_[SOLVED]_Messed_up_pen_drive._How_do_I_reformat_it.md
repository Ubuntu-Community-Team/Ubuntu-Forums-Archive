---
title: "[SOLVED] Messed up pen drive. How do I reformat it to ext3 -I'm on live cd cos system"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by philinux on 2007-09-26
Once I've reformatted it to ext3, was fat32,I can backup my /home folder and reinstall

Live cd system says it cant mount it now

---

### Post by philinux on 2007-09-26
ok pen drive reformatted with bloody windoze but at least its back fat32. 
Problem is with live cd its mounted as read only. Arrgggh

Thes live cd are damn good but making stuff read only is a real pain.

---

### Post by bodhi.zazen on 2007-09-26
You could make a tar archive of /home as root. An archive will preserve permissions.

Save the archive to your flash drive as root, gksudo nautilus, or remount the flash drive with rw.

What option do you want help with ?

---

### Post by philinux on 2007-09-26
Ubuntu live cd not too good.

Reformatted usb drive using Knoppix live cd  and a bit of google, worked a treat. Permissions are a doddle on Knoppix live cd.

so now I've got my home drive backed up on usb drive with full access and symlimks. woohhooo.

Now to reinstall linux

---

