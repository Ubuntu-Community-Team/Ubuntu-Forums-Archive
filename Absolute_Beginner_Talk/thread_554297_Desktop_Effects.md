---
title: "Desktop Effects"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by H_91 on 2007-09-18
For some reason, the **Desktop Effects** in the system>preferences menu has somehow disappeared after I reinstalled compiz. I managed to get it back the first time, but I can't find where I got the code from now. 

Anyone know how?


Thank you. =]

---

### Post by eljoeb on 2007-09-18
If you have compiz fusion, you won't need the desktop effects tool.  Try the CompizConfig Setting manager.

If you're trying to turn it on, try:

```
compiz --replace --use-copy
```

This might be necessary if you are not getting window borders (You will need Emerald installed)

```
emerald --replace
```

---

### Post by H_91 on 2007-09-18
This message appeared while trying to turn on compiz fusion..
+I already have emerald installed.. 

```
vaio@vaio-laptop:~$ compiz --replace --use-copy
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: /usr/share/compiz/default-cubecap.png
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
/usr/bin/compiz.real (core) - Error: no 'text' plugin with ABI version '20070902' loaded

/usr/bin/compiz.real (thumbnail) - Warn: No compatible text plugin found.

(gtk-window-decorator:25146): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:25146): Wnck-WARNING **: Unhandled action type (nil)
inotify_add_watch: No such file or directory

(gtk-window-decorator:25146): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:25146): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:25146): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:25146): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:25146): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:25146): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:25146): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:25146): Wnck-WARNING **: Unhandled action type (nil)
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'mswitch'
/usr/bin/compiz.real (core) - Error: no 'text' plugin with ABI version '20070902' loaded

/usr/bin/compiz.real (shift) - Warn: No compatible text plugin loaded.
/usr/bin/compiz: line 777: 25144 Segmentation fault      (core dumped) $*
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"


```

---

