---
title: "wipe a disk?"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by buccaneere on 2007-11-15
dd if=/dev/zero of=/dev/hda

Will this clear the external disk, and leave the local drive untouched?

---

### Post by Paulmd on 2007-11-16
> **buccaneere said:**
> dd if=/dev/zero of=/dev/hda

Will this clear the external disk, and leave the local drive untouched?

That's not the way to wipe a drive.

Look here:

dban.sourceforge.net


it's a good idea to physically disconnect any drive you don't want to wipe. It's technically not necessary, but can guard against Operator error.



I can't say for sure what your command will do because I don't know how your system is configured. Anyway, bad idea to run that command.

---

### Post by Inxsible on 2007-11-16
+1 for DBAN

---

