---
title: "programs to load on boot"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by S15_88 on 2007-07-26
I was wondering if there is a file where i can specify a program to run at startup, and where that file would be located.  what i would like to accomplish is have my GDesklets profile load on startup instead of every time i log on i have to go menu>accessories>GDesklets  then close it.  that was my other concern is it possible to load the profile instead of actually starting GDesklets cause then i'd have to close it right after.

Thanks, Alain

---

### Post by asmoore82 on 2007-07-26
System>Preferences>Sessions

---

### Post by S15_88 on 2007-07-26
sweet deal, do u know the name of the file it writes to and the location?

---

### Post by doomster on 2007-07-26
ignore me:P

---

### Post by asmoore82 on 2007-07-26
> 
       gnome-session uses the contents  of  the   ~/.gnome2/session  file  for
       starting   up   as   specified  by  the  "CurrentSession"  key  in  the
       ~/.gnome2/session-options file.  Various default values are provided in
       case the file entry does not exist.

       If the session file does not exist, gnome-session will use the contents
       of the /usr/share/gnome/default.session file.

```
~ $ man gnome-session
```
:KS

---

