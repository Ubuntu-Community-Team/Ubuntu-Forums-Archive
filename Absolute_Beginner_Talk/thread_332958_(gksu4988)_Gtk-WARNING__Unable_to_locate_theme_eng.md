---
title: "(gksu:4988): Gtk-WARNING **: Unable to locate theme engine in module_path: &quot;pixmap&quot;"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by tchoklat on 2007-01-06
(gksu:4988): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap"

This is the error message when I run a dpkg or gksu command from a terminal.

Any thoughts?

---

### Post by pacificdrums on 2007-02-08
This did the trick for me.
```
sudo aptitude install gtk2-engines-pixbuf
```

---

### Post by grim4593 on 2007-02-10
That worked for me too. Thanks!

---

### Post by olavjunior on 2007-02-24
THANX! This worked great! I see many folks have this problem, this thread is very useful!

---

### Post by yogo on 2007-08-05
> **olavjunior said:**
> THANX! This worked great! I see many folks have this problem, this thread is very useful!



I second that, it is very useful, had the same problem myself, just changed the theme name and viola solved a problem without having to start a new thread.

---

### Post by K.Mandla on 2007-11-08
Thanks for this ... again. Every three months or so I go digging around for the solution to that pixmap error, and find my way back here again. Of course, if the error message said "pixbuf" instead of "pixmap," I could save myself a little apt-cache searching. ... :|

---

