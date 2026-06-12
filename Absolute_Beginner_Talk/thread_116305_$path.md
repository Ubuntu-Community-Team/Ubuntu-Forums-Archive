---
title: "$path ???"
date: 2006-01-12
forum: Absolute Beginner Talk
---

### Post by bkv2k on 2006-01-12
When I open a console window and type ...echo $PATH...I get a display of what's in the path variable.  If I open a virtual terminal...Ctl-Alt-F1..., log in and type...echo $PATH...I get something similar, but not exactly the same.  Why aren't these the same?

Thanks!

---

### Post by earobinson on 2006-01-12
try typing whoami in both see if its any diferent

---

### Post by bkv2k on 2006-01-12
[QUOTE=earobinson]try typing whoami in both see if its any diferent[/QUOTE]

Says I'm the same user in both the console and virtual terminal.

---

### Post by cwaldbieser on 2006-01-12
[QUOTE=bkv2k]Says I'm the same user in both the console and virtual terminal.[/QUOTE]
When you log into the virtual terminal, it is likely to be a login shell, so it sources ~/.bash_profile.

From a terminal in the GUI, it is probably not a login shell, so it sources ~/.bashrc.

---

