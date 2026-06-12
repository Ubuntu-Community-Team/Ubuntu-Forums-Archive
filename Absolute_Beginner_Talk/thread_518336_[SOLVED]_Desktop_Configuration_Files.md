---
title: "[SOLVED] Desktop Configuration Files"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by amrclutch1 on 2007-08-05
I would like to know where the desktop configuration files gets it's icons from. In the .desktop file it just says firefox.svg but I don't know what directory it is in.

---

### Post by bodhi.zazen on 2007-08-05
you could try 
```
locate firefox.svg
```

---

### Post by yabbadabbadont on 2007-08-05
It would get it from the current icon theme that the user has set in their theme preferences.  So the actual icon would either be in one of the icon theme directories in /usr/share/icons or in the user's personal ~/.icons directory.  (or a sub-directory of one of them)

---

### Post by amrclutch1 on 2007-08-05
Thanks for the help, i found it! :D

---

