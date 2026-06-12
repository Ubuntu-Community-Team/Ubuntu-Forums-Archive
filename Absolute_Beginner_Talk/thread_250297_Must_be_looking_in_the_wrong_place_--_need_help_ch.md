---
title: "Must be looking in the wrong place -- need help changing a setting..."
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by baylorbear on 2006-09-03
Now I KNOW there has to be a thread for this-- but I can't find it.

I'm trying to change the icon in GNOME next to the "Applications" menu in the top left-hand corner...

Any suggestions or thread-urls?

---

### Post by aysiu on 2006-09-03
To replace them, you'll need to do Alt-F2 ```
gksudo nautilus
```

Look in /usr/share/icons/Human/*size*x*size*/places

To refresh, Alt-F2 ```
killall gnome-panel
```

---

