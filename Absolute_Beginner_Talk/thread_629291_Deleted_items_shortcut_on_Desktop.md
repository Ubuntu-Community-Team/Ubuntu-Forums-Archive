---
title: "Deleted items shortcut on Desktop"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by reesy on 2007-12-02
I've been trying to put deleted items on the desktop as a shortcut but it doesn't let me make a link to it. If any one knows how to put it on the desktop I would be grateful.

---

### Post by kevinatkins on 2007-12-02
Hi,

You'll need to use the gconf-editor, which is a bit like the registry editor in Windows. Press <Alt>-<F2> then type in 'gconf-editor' in the 'Run Application' box. When the editor appears, using the tree on the left side, navigate to Apps - > Nautilus -> Desktop and put a check in the 'trash_icon_visible' box.

---

