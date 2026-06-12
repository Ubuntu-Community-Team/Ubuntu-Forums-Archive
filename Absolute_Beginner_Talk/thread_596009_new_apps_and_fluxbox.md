---
title: "new apps and fluxbox"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by anchor1te on 2007-10-29
Just installed fluxbuntu and added Wine after the installation.  Ran the fix to update menus.  After installing Wine, ran it again.  Wine is not showing up under Apps.  How do I make newly installed apps show up?


Thanks!

---

### Post by nest on 2007-10-29
open a terminal

```
gedit ~/.fluxbox/menu
```

[Begin] (Fluxbox)
[submenu] (Apps)
[exec] (Program) {command}
[end]

that would be it. hope you could solved it.

---

### Post by kerry_s on 2007-10-29
**sudo update-menus**

---

### Post by linuxlizard on 2007-10-29
If that doesn't do it there is normally a menu.1st file in your /home/{your username}/.fluxbox directory that you edit by hand.

---

