---
title: "Add/Remove closes"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by Joka999 on 2007-02-27
WHen i open Add/Remove it loads up then closes for no reason any1 gt any ideas? im A n00b

---

### Post by lhtown on 2007-02-27
Actually, I don't.

What version of Ubuntu are you running?

---

### Post by picpak on 2007-02-27
Open up a terminal. What does it say when you run

```
gnome-app-install
```

?

---

### Post by Joka999 on 2007-03-01
```
Introspect error: The name org.freedesktop.AppInstall was not provided by any .service files
no listening object (The name org.freedesktop.AppInstall was not provided by any .service files) 

** (gnome-app-install:5217): WARNING **: return value of custom widget handler was not a GtkWidget
/usr/lib/python2.4/site-packages/AppInstall/AppInstall.py:1270: GtkWarning: gtk_tree_model_sort_sort: assertion `tree_model_sort->default_sort_func != NULL' failed
  item.applications.set_default_sort_func(None)
Traceback (most recent call last):
  File "/usr/bin/gnome-app-install", line 141, in ?
    sys.argv, mime_search=msi)
  File "/usr/lib/python2.4/site-packages/AppInstall/AppInstall.py", line 265, in __init__
    time_source = os.stat("/etc/apt/sources.list")[stat.ST_MTIME]
OSError: [Errno 2] No such file or directory: '/etc/apt/sources.list'

```
 It says that, open add/remove loads it then it closes.

---

### Post by picpak on 2007-03-02
!!! How can you not have a sources.list???

Anyway, follow the instructions [here](http://www.psychocats.net/ubuntu/sources), and then rerun Add/Remove.

---

### Post by Joka999 on 2007-03-03
DIdn't work

---

