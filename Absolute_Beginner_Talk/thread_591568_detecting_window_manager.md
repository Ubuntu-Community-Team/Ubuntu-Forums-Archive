---
title: "detecting window manager"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by dr.silly on 2007-10-25
how do i detect the active window manager in shell

---

### Post by ghantoos on 2007-10-26
The only thing I could think of (help a little help from my friends), was "ps"

To detect if gnome is running:

```
 ps fax | grep metacity | wc -l
```If this returns a value bigger than 1, it means metacity is running.
Just do a simple shell script with the rest of the window managers you need to detect.

Hope this is helpful,

cheers,

Ghantoos

---

