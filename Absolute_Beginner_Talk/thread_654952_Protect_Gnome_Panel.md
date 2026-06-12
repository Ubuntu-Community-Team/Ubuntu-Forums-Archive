---
title: "Protect Gnome Panel"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by Atreus12 on 2007-12-31
My parents somehow managed to delete the top panel on gnome, causing them some problems as they couldn't use the program shortcuts they were used to.

Is there a way to prevent (normal) users from deleting or modifying the top panel?

Andrew

---

### Post by spiderbatdad on 2007-12-31
you can lock the panel down with gconf-editor. Alt-F2```
gconf-editor
```
navigate to apps>>panel>>global...select locked_down.

---

