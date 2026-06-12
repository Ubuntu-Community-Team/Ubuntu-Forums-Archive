---
title: "Remove drives from desktop"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by teHIngo on 2007-04-28
On my desktop, all my partitions are shown as drives, for instance hda1, or Volume (my external hard drive).
However, I find this rather ugly. Is there a way to disable this? :confused: 

Thanks in advance! Cheers! :)

---

### Post by blackened on 2007-04-28
ALT+F2  -> gconf-editor

/apps/nautilus/desktop -> uncheck "volumes_visible" in the right pane.

The drawback to this is that any removable media you plug in will not be shown on the desktop either, but such are the things we do for beauty.

---

### Post by teHIngo on 2007-04-28
Awesome, thanks!

---

