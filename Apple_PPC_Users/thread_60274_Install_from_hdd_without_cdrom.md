---
title: "Install from hdd without cdrom"
date: 2005-08-27
forum: Apple PPC Users
---

### Post by vodka60 on 2005-08-27
I copied the cdrom content to os9 partition (hd:9) because my cdrom in pismo is dead. I modified yaboot and get it boot to the installation process. After setting up language, keyboard mapping, the installer proceed to detect cdrom and prompt me to configure driver to load the cdrom. Since I do not have a working cdrom, how can I tell hoary to load from the hd:9 partition? Where do I modify? I try to mount -t hfs /dev/hda9 /cdrom but doesn't work too.

---

