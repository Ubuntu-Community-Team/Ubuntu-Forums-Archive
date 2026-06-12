---
title: "applications menu"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by quinlo on 2008-04-16
so i uninstalled the wine windows emulator but I still have wine in my applications drop-down menu and dont know how to get rid of the sucker...

---

### Post by Inxsible on 2008-04-16
Right click on Applications and then select Edit Menus. Remove the entry for Wine from under the proper heading

---

### Post by quinlo on 2008-04-16
Nice... so easy... thanks a bunch

---

### Post by MrFSL on 2008-04-16
And now if you want to reinstall wine you will have issues because it won't show up right in the menu.

I suggest looking at the contents of this folder:
```
~/.config/menus/applications-merged
```
...and perhaps deleting these files. ;)

---

