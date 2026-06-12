---
title: "[SOLVED] Menu Items not removed"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by Inxsible on 2007-06-08
I un-installed Evolution along with ubuntu-desktop, but the menu entries still remained in the Applications menu. 
The same thing happened with Sound-juicer and serpentine. Why doesn't the un-install remove the menu entries ?

---

### Post by 67GTA on 2007-06-08
I have never removed the desktop package, so I'm just guessing, but sometimes I still have to manually delete menu entries with the menu editor. You might also try "update-menu" in a terminal.

---

### Post by Inxsible on 2007-06-09
When i run update-menu, it gives me an error
```
bash: update-menu: command not found
```

---

### Post by 67GTA on 2007-06-09
Install "menu" from the repositories and try it again.

---

### Post by orbital on 2007-09-19
I have menu installed, but when I run menu-update I also get:

```
bash: update-menu: command not found
```

How to get rid of Evolution shortcut in Applications?

---

### Post by orbital on 2007-09-20
Fixed using SYSTEM-PREFERENCES-MAIN MENU

---

