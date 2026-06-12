---
title: "removable media on desktop"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by galezshade on 2007-06-13
HI. i got a question concerning all those hdd icons on my desktop. i have messed with my pc a lot so i have like 8 different partitions. all of them are shown on my desktop. could anyone tell me how to get rid of them except unmounting. thanks.

---

### Post by happy-and-lost on 2007-06-13
If you don't want them to mount in the first place, comment them out (#)  in /etc/fstab

---

### Post by nightheart on 2007-06-13
I think he means, how do you get rid of the icons and keep the drives mounted.  I'm wondering that myself, as I hate having icons on my desktop.  Just a weird pet peeve.

---

### Post by mcduck on 2007-06-13
There are 2 ways. One is to disable drive icons on desktop with Configuration Editor and the other is to mount those drives to some other place than /media. I use /mnt myself for all internal partitions.

To disable drive icons, run 'gconf-editor', then browse to apps/nautilus/desktop and disable 'volumes_visible'. (This will also disable icons of removable drives and disks.)

---

### Post by happy-and-lost on 2007-06-13
OK, press <Alt><F2> to bring up the run dialog, type *gconf-editor* and click run.

Now navigate to apps>nautilus>desktop and uncheck "volumes_visible"

---

### Post by nightheart on 2007-06-14
Cool.  Thank you.

---

### Post by vanadium on 2007-06-14
Better follow mcduck's advice on mounting on a different place. you probably want icons to appear for removable media like USB sticks such that you can remove them easily.

You change the mount locations by editing /etc/fstab. Next to editing /etc/fstab, you obviously must also create your mount points.

My guess is that you also can change the mount points graphically from within "Places - Computer", right-click properties, Drive tab, but I have no experience with this, and I am not sure whether you really are able to mount them outside of /media this way.

---

### Post by ozzyprv on 2007-08-29
> **happy-and-lost said:**
> OK, press <Alt><F2> to bring up the run dialog, type *gconf-editor* and click run.

Now navigate to apps>nautilus>desktop and uncheck "volumes_visible"

Thank you!

---

