---
title: "Mounted partitions on desktop"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by boyprodigy on 2007-04-21
I have two partitions on my desktop and I'd rather not have them the. Is there a way to get them off the desktop but still have them mounted?

---

### Post by diatribe on 2007-04-21
are you running gnome kde or xfce?

---

### Post by markl187ld on 2007-04-21
```
gconf-editor
```
Apps - Nautlus - volumes_visible

---

### Post by boyprodigy on 2007-04-21
What if I still want my CD drive to show up?

---

### Post by markl187ld on 2007-04-21
> **boyprodigy said:**
> What if I still want my CD drive to show up?

Then you'll need to edit /etc/fstab to mount your hard disks some place other than /media.

---

### Post by Nythain on 2007-04-21
damn, to slow... yeah, edit your fstab to mount them in like /mount instead of /media... in kubuntu i havent found a way yet to keep /media mounts from appearing on my desktop

---

