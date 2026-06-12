---
title: "making shortcut for &quot;my computer&quot;"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by Rubruquis on 2008-01-07
I was able to make shortcuts for Firefox etc by right clicking to them and then clicking "add this launcher to desktop".
But when I right click to my computer, it just opens the computer folder and doesn't ask if I want to make a shortcut or not.
Is there a way to make a shortcut for "computer"?
Thank you

---

### Post by Ub1476 on 2008-01-07
Open gconfe-editor in alt+f2:

```
gconf-editor
```

apps>nautilus>desktop>check computer_icon_visible.

---

### Post by philinux on 2008-01-07
Right click on the desktop. Select create launcher.

Under Type use Location.

In command use

computer:///

Fill in other bits as you like.

[edit] always more than one way to do these things.

---

### Post by Rubruquis on 2008-01-07
Thank you very much =)

---

### Post by CatKiller on 2008-01-07
And a third, for luck, you can drag-and-drop from the Places menu. Or the Applications menu, for that matter.

---

