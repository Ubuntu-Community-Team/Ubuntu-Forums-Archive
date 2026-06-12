---
title: "[SOLVED] Terminate beryl 3d desktop"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by Shadow ZERO on 2007-07-30
Whats the best way to go back to the original desktop UI after you load the beryl-manager?  Quitting the manager from the tray icon doesn't do it.

---

### Post by bren on 2007-07-30
can't you just select 
      - window manager = metacity (this is the ubuntu default)
from the beryl manager

or sudo apt-get remove beryl beryl-manager for more permanent change.

---

### Post by 3rdalbum on 2007-07-30
If that doesn't work (that surprises me), you should press Alt-F2 and put this command into the text field:

```
metacity --replace
```

Make sure that "Metacity" is selected as the window manager in the Beryl applet, then quit the applet, and don't put the command into a terminal window.

This might not work - it went back to Metacity and then immediately started up Beryl again on my computer... but you might get some luck.

---

