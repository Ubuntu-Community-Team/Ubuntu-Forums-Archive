---
title: "Move NTFS Volums off Desktop?"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by jusmurph on 2007-06-07
I dual boot... having come from Windows i have quiet a few ntfs partitions. Though they show up on my desktop and i want to know how to move them off so i have a clean desktop!

Thanks!

---

### Post by floke on 2007-06-07
Either unmount them in your /etc/fstab file (sudo nano /etc/fstab) - put a '#' in front of their entries - you could then mount them in media instead by using ntfs-3g and ntfs-config (see [http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html))

Or - use gconf-editor - go to apps/nautilus/desktop - and uncheck 'show mounted volumes' - though this will no longer show you mounted usb's or cd's etc. on the desktop.

---

### Post by Ek0nomik on 2007-06-07
> **Steve.K said:**
> Either unmount them in your /etc/fstab file (sudo nano /etc/fstab) - put a '#' in front of their entries - you could then mount them in media instead by using ntfs-3g and ntfs-config (see [http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html))

**Or - use gconf-editor - go to apps/nautilus/desktop - and uncheck 'show mounted volumes'** - though this will no longer show you mounted usb's or cd's etc. on the desktop.

This is the best option if you want a clean desktop.  :)

---

### Post by jusmurph on 2007-06-07
Cheers,

Thanks!

---

