---
title: "GUI file managers mount as read only"
date: 2013-12-28
forum: Any Other OS
---

### Post by micahpage on 2013-12-28
I switched to arch linux a bit ago. GUI file managers like nautilus or thunar sometimes go wacko and mount my sd card or usb's as read only. I have to mount it manually through the terminal via:
```
sudo mount /dev/sd<letter><number> /mnt/USB
```
this fixes it and mounts it as read/write.

This does not happen as far as i know in ubuntu. I am assuming there is some library that ubuntu has by default  that is not yet on my arch. I just dont know what that library is.

---

### Post by sotiris2 on 2013-12-28
If you can get it to write to the partition then it's not lacking some library (ntfs-3g for ntfs partitions comes to mind as a relevant situation.)  My guess is that it probably mounts it as Root owned without write permissions for others. Unfortunately without familiarity with Arch I can't give you much help other than pointing you to [ArchWirki](https://wiki.archlinux.org/index.php/Udisks#Udisks)'s section on what I thing is relevant to your (udisks2 or udisk) problem.

---

### Post by Irihapeti on 2013-12-28
*Thread moved to **Other OS/Distro Support**.*

---

