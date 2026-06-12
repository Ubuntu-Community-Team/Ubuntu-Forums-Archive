---
title: "Where is the fstab info in Gutsy?"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by treehouse on 2008-04-15
Curiosity:

My slave, /dev/hdb, mounts automatically on startup, but there's no entry for it in my fstab file. How is this possible?

---

### Post by tzulberti on 2008-04-15
The fstab file is at: /etc. So the file you want to edit is: /etc/fstab.
If it isnot at you fstab then it should be gnome or KDE which mount them. You should check the removable media.

---

### Post by treehouse on 2008-04-15
Sorry, I worded badly in the title. /etc/fstab has no entry for the second hard drive, yet it's mounted. Where's this removable thingamajig?

---

### Post by Inxsible on 2008-04-15
it should be under /media. All drives and partitions that are not listed in fstab and those that do not have a specific mount point are always mounted under /media.

If you know its mounted, then you can access it..and when you do, it will show you the path anyway.

---

### Post by K.Mandla on 2008-04-15
I believe hal and similar daemons catch that drive when it's found and mount it automatically without needing an entry in fstab. /etc/mtab should show where it's mounted, and the device name. Or did I misunderstand your question?

---

### Post by treehouse on 2008-04-15
> **K.Mandla said:**
> I believe hal and similar daemons catch that drive when it's found and mount it automatically without needing an entry in fstab. /etc/mtab should show where it's mounted, and the device name. Or did I misunderstand your question?


Sweet, that's exactly what I was asking.

In a twist of irony, somehow it just stopped automatically loading. I re-added it to fstab and its mounting the old school way, but it's not as cool as when Gnome was doing it on its own :(

Oh well.

---

