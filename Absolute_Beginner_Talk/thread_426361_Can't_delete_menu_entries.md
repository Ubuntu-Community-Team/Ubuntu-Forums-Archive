---
title: "Can't delete menu entries?"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by mech7 on 2007-04-28
WINE made some menu entries and i moved them.. but now i can't delete the original ones does anybody know how ?:(

---

### Post by bobplano on 2007-04-28
i don;t know how to delete them, but you can hide them with the alacarte menu editor with GNOME. i don't know about KDE but it should be something similar

---

### Post by nooblot on 2008-06-29
resurrection time ---- running 8.04

How to delete orphan entries ????

---

### Post by david.rahrer on 2008-07-20
Same here, I've tried deactivating, then deleting, reactivating -- they just sit there.  Is there a way to do this from gconf or other config files?

---

### Post by Kevbert on 2008-07-20
To delete menu items so they'll never appear as a menu item:
Right click on Applications so that you can select Edit Menus.  Browse to the menu item you wish to remove, highlight it, and press Delete key.

---

### Post by david.rahrer on 2008-07-20
> **Kevbert said:**
> To delete menu items so they'll never appear as a menu item:
Right click on Applications so that you can select Edit Menus.  Browse to the menu item you wish to remove, highlight it, and press Delete key.

This is the way is should work, but it doesn't.  The items are unaffected by either pressing delete or right-clicking and selecting delete.  This is the problem :(

---

### Post by warp99 on 2008-07-20
The extra wine entries for the desktop files are in some of the hidden directories in your ~/user director. I forget where they are located, but if you open a terminal and issue the following:

```
find ~/ -name '*.desktop'
```

You should be able to figure out the correct files. Then just move to that directory and delete those *.desktop files. The menu items should disappear when you reload Gnome.

---

### Post by david.rahrer on 2008-07-21
Thanks Warp99, that worked.  For me, they all appeared in ~/.local/share and there were a bunch.  I deleted the problem ones and they disappeared from the Applications/Menu immediately.

---

