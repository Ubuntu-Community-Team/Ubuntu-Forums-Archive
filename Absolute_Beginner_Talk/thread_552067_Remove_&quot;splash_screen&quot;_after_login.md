---
title: "Remove &quot;splash screen&quot; after login"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by alecwh on 2007-09-16
After I login to gnome, there is a splash screen that comes up. IT's orange, and really annoying. Can I disable this?

---

### Post by jordanmthomas on 2007-09-16
press Alt + F2 and type
```
gconf-editor /apps/gnome-session/options
```
and hit enter

Then, in the right pane of the newly spawned window is a boolean value called show_splash_screen.  I'm confident you can figure out what to do from here.  :)

---

### Post by alecwh on 2007-09-16
thanks. :)

---

