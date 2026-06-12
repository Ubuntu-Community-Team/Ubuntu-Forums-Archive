---
title: "Home Folder on Desktop?"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by Leonaken on 2007-01-18
How do you put a shortcut to the Home folder on the desktop in Ubuntu/Gnome? :confused:

---

### Post by ComplexNumber on 2007-01-18
> **Leonaken said:**
> How do you put a shortcut to the Home folder on the desktop in Ubuntu/Gnome? :confused:
fire up gconf-editor. go to 'Edit' -> 'Find' in the menu, then type in "nautilus"(don't tick the 2 tickboxes). highlight apps/nautilus/desktop. tick where it says "home_icon_visible"

---

### Post by irish_flu on 2007-01-18
Easiest way I know is to:

Go to the "Places" menu, locate the icon there for the home folder, then click, hold, and drag the icon onto your desktop.  It won't mess with what's already in the "Places menu, it'll make a copy.

---

### Post by JamieC on 2007-01-18
Or make a symlink by typing the following in terminal:
```

ln -s ~/ ~/Desktop/Home

```

Or, you could just drag it from the "Places" menu to the desktop, ComplexNumber's method is probably best, though.

---

### Post by Leonaken on 2007-01-18
Thanks guys!

---

