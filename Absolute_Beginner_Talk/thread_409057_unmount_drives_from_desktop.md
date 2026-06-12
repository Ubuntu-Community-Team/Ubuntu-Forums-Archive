---
title: "unmount drives from desktop"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by AgelessDrifter on 2007-04-14
I'd like to tidy up my new desktop. Dells have a lot of partitions on them by default, and I've got a USB drive with two partitions, so I've got five or six drives mounted on my desktop, and I can't move them. It tells me "only root can unmount (drive)." I guess I don't have permission? How do I correct this?

---

### Post by Dirty Ole on 2007-04-14
open gconf-editor from terminal. browse to apps/nautilus/desktop uncheck volumes visible. This keeps the drives mounted but doesn't show them on the desktop.

If you want to unmount you can try installing pmount( sudo apt-get install pmount ) it allows mounting as normal users. Maybe it will also allow unmounting.

---

### Post by AgelessDrifter on 2007-04-14
Thanks a bunch

---

