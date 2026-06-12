---
title: "new things added to grub boot screen"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by fenderjaguar on 2007-02-22
originally, it had a generic xubuntu, a recovery mode, a memory check, and an option to boot windows xp. now i find there have been 4 more generic xubuntu's added to the list. what the hell? they all say 'generic kernel' or something. but i think the top one now says 6.11 instead of the 3 other which say 6.10.

anyone know why this has happened?

---

### Post by Resurrection on 2007-02-22
The Ubuntu team provides pre-compiled kernels as part of the updates every so often.  These pre-compiled kernels are released base on new generic linux kernel releases.

It is good practice to keep at least two of these kernels, the newest one, and one you know to work solid.  Then you typically use the newest kernel in your list (the one with the highest number).  And save an older kernel as a fall back option in case you ever run into problems.

You can edit your menu.lst file which dictates what grub shows if you don't like all those entries.  To see this file type in a terminal:

```
sudo nano /boot/grub/menu.lst
```

You can always either delete entries you don't want or comment them out with a #.

You can also get rid of the some of the extra kernels from your system, but not sure how to do that in Xubuntu.  In Ubuntu (Gnome) you would use Synaptic to remove those packages.  Not sure what your equivalent is.

---

### Post by fenderjaguar on 2007-02-22
ah so this is just normal? thanks

---

