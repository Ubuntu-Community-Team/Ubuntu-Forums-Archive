---
title: "Can't log in"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by cyberbuff on 2007-10-23
I don't know what's wrong. I was changed the monitor resolution to 1024X768. Then, without rebooting I tried to install a gdm theme. But the system was stuck. I did a manual restart. now, the login screen appears but after entering the username and password (and hitting enter), everything's gone and the same screen appears again. there's no problem with the correctness of the u-name or password since it doesn't throw any error about them. Help much appreciated...
regards...

---

### Post by reza81 on 2007-10-23
Ctrl+Alt+F1 & reset your password, maybe that will help!

with Ctrl+Alt+F7 you go back to X

---

### Post by Vadi on 2007-10-23
Tried pressing random buttons like ctrl+alt+f1 and then ctrl+alt+f7, alt+tab and such?

---

### Post by cyberbuff on 2007-10-23
I tried this: i went to recovery mode. then
```

su <username>
sudo startx

```
now i am in ubuntu. but whenever i do the normal login, the same story again... :(
Please help

---

### Post by cyberbuff on 2007-10-23
omg! i just replaces the xorg.conf file with the unchanged one. And it's working now. seems like changeing the resolution was the problem. now, the problem is what can i do to change the resolution?

---

### Post by ddrichardson on 2007-10-23
> **cyberbuff said:**
> I tried this: i went to recovery mode. then
```

su <username>
sudo startx

```now i am in ubuntu. but whenever i do the normal login, the same story again... :(
Please helpwhy startx as sudo? What happens if you startx?

---

### Post by cyberbuff on 2007-10-23
> **ddrichardson said:**
> why startx as sudo? What happens if you startx?
I got the idea from the forum. If I "startx" I can get into the desktop without the login screen. and that too in 1024X768 resolution. It seems that changing the resolution was the problem. How can i fix the issue with the resolution?

---

