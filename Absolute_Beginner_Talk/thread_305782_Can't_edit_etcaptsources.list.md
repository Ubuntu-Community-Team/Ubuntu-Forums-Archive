---
title: "Can't edit /etc/apt/sources.list"
date: 2006-11-23
forum: Absolute Beginner Talk
---

### Post by donang on 2006-11-23
tried to add a couple of things to /etc/apt/sources.list but it tells me that i don't have permission to do this.  I am the only user on the system.  all my administration stuff asks for my password which i give with no problems.  Also, i am doing this in graphical mode,not terminal.  I cant even pull up my files in terminal, even as su  or sudo

suggestions?

---

### Post by NetworkGuy on 2006-11-23
type ```
 gksudo gedit /etc/apt/sources.list
```

that should allow you to edit the file.

---

### Post by donang on 2006-11-23
i got a GTK-Warning ** cannot open display

---

### Post by NetworkGuy on 2006-11-23
Restart X and try again  Ctrl-Alt-Backspace to restart X

---

### Post by donang on 2006-11-23
worked great..thanks for help

---

