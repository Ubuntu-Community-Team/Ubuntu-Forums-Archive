---
title: "Gnome - an icon, where is it?"
date: 2006-04-13
forum: Absolute Beginner Talk
---

### Post by zerhacke on 2006-04-13
In Gnome, next to the applications menu is a small Ubuntu circle.  I want to find the location on the computer of this icon so I can change it.  I found an icon of Tux holding the Ubuntu circle.

Where is this icon located on the filesystem so that I may make the appropriate changes?

---

### Post by Perfect Storm on 2006-04-13
Rename your custom icon to distributor-logo.png

```

cd /where/your/icon/is
sudo cp distributor-logo.png /usr/share/icons/hicolor/48x48/apps
killall gnome-panel
```

---

### Post by zerhacke on 2006-04-13
Thank you very much for the speedy reply, AI.  Worked like a charm.

---

