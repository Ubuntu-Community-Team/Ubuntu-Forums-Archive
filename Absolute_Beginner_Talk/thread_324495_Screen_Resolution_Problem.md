---
title: "Screen Resolution Problem"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by Straft on 2006-12-23
Ok, well I'm new to Ubuntu. And the screen resolution is at 1024x768 as default, My LCD monitor does not work with that kind of resolution, I mean it does but it comes out making things look fuzzy. How can I make my resolution higher? The limit is 1024x768 :???:

---

### Post by taurus on 2006-12-23
You probably need to install a driver for your graphic card.  Otherwise, try to edit /etc/X11/xorg.conf and add whatever resolution you want to use in there (near the end).

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/X11/xorg.conf
```

---

