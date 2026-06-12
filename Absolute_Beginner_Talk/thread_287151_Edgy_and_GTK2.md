---
title: "Edgy and GTK2"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by curtisf14 on 2006-10-28
Has anyone experienced any problems with GTK2 themes in Edgy?  I upgraded yesterday and am using the LiNsta2 GTK2 theme, but the theme is pretty different from what it looked like using Dapper (and the buttons/menus within applications have become very square, plain, and boring, as if it can't find the theme or something).  I have tried other GTK2 themes as well, but the same thing seems to happen.  So far, only the themes that come with Ubuntu work as expected.  

As for error messages, if I open something like gedit using the command line, I get a bunch of errors that look like the following before the program opens:

```
(gedit:32573): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
```

Any advice?

---

### Post by progprog on 2006-11-04
> Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap"

I had the same problem, and solved it with "sudo apt-get install gtk2-engines-pixbuf"

---

