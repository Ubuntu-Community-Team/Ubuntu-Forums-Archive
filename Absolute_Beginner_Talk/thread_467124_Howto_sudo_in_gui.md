---
title: "Howto sudo in gui?"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by OmnificienT on 2007-06-07
How do I sudo things in the gui?

Thank You.

---

### Post by muguwmp67 on 2007-06-07
You can edit the menu options and add 'gksudo' before calling the command.  Alternatively, you can press alt-f2 and type 'gksudo <command>'.

---

### Post by jfinkels on 2007-06-07
To open the file manager, press Alt+F2 and type ```
gksudo nautilus
```

---

### Post by vanadium on 2007-06-07
DON'T edit the menus! Use sudo rights only when strictly necessary. The Alt+F2 approach is the one to go.

---

### Post by tpg on 2007-06-07
If you're using KDE, then use 'kdesu <command>', for example in the Alt-F2 run dialogue.

---

### Post by warcriminal on 2007-06-07
You just use gksudo.

[http://www.goitexpert.com/entry.cfm?entry=SUDO-and-GKSUDO](http://www.goitexpert.com/entry.cfm?entry=SUDO-and-GKSUDO)

---

