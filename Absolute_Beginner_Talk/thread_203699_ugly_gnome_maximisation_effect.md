---
title: "ugly gnome maximisation effect"
date: 2006-06-25
forum: Absolute Beginner Talk
---

### Post by bullon on 2006-06-25
hi all!

when i click on an application launcher icon on a gnome panel (or the wastebasket icon) an ugly blue frame "maximises" before the actual window is rendered. Is there any way I can get rid of this? I tried to take a sceenshot but with no success. I know its a minor issue and maybe  shouldn complain about it, but its so annoying](*,) !!!!!!

---

### Post by Maggot on 2006-06-25
My laptop does it too but its so fast hardly noticable. Maybe your Vid card is just slows (old)/not configured so that box appears longer?

---

### Post by aysiu on 2006-06-25
Maybe Alt-F2 ```
gconf-editor
``` Apps > Metacity > General > Reduced Resources?

---

### Post by LKRaider on 2006-06-25
There are two ways to disable that:

1) The terminal way
Just copy&paste these commands to a terminal
```
gconftool-2 --set --type boolean /apps/panel/global/enable_animations "False"
gconftool-2 --set --type boolean /desktop/gnome/interface/enable_animations "False"
```

2) The GUI way
Press Alt+F2 and run **gconf-editor**.
Browse the tree structure and go to _/apps/panel/global_ then disable the **enable_animations** checkbox. Then go to _/desktop/gnome/interface_ and do the same.

---

### Post by bullon on 2006-06-25
done! thanks alot, you people are awesome:D

---

