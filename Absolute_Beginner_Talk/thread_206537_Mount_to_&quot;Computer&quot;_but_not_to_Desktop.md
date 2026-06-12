---
title: "Mount to &quot;Computer&quot; but not to Desktop?"
date: 2006-06-30
forum: Absolute Beginner Talk
---

### Post by krs1ars on 2006-06-30
So this might be a pretty basic question, but I haven't found any way around it yet.

Currently, I use fstab to mount to other (ntfs) partitions. 

If I mount them to /mtn/something, the work fine, but don't appear in the computer panel.
If I mount them to /media/something, again, they work, and appear in the computer panel, but also appear on the desktop (and I can't seem to get rid of them)
If I don't mount them with fstab, they show up in the computer panel, not on the desktop, but they don't work!

Any help would be great.

---

### Post by gommle on 2006-06-30
Im wondering the same thing. When mounting FTP's they show up on the desktop and i cant get rid of them without unmounting.

---

### Post by snaga on 2006-06-30
I'm not sure I understand what you are trying to accomplish. You have described the various ways to mount things. What are you trying to do?

---

### Post by Jagot on 2006-06-30
If you mean you don't want them to appear on the desktop then hit alt+f2 and type 'gconf-editor'.  Now navigate to apps, nautilus, desktop, then untick 'volumes_visible'

---

