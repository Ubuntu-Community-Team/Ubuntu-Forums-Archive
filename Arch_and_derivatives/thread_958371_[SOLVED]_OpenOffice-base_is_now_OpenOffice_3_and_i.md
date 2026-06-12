---
title: "[SOLVED] OpenOffice-base is now OpenOffice 3 and it won't work"
date: 2008-10-25
forum: Arch and derivatives
---

### Post by Darkade on 2008-10-25
Hello! I've been using arch for a while now and Yesterday I ran into a problem. I had updated my openoffice about a week ago but havent used it and now when I try to use it I get the following erros
```

[ivan@icarus ~]$ soffice

(process:3508): GLib-GObject-CRITICAL **: gtype.c:2458: initialization assertion failed, use IA__g_type_init() prior to this function

(process:3508): GLib-GObject-CRITICAL **: g_type_interface_add_prerequisite: assertion `G_TYPE_IS_INTERFACE (interface_type)' failed

(process:3508): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(process:3508): GLib-GObject-CRITICAL **: gtype.c:2458: initialization assertion failed, use IA__g_type_init() prior to this function

(process:3508): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(process:3508): GLib-GObject-CRITICAL **: gtype.c:2458: initialization assertion failed, use IA__g_type_init() prior to this function

(process:3508): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed


```
and the it hangs, I already reinstalled glib and that didn't helped

Thanks

---

### Post by fwojciec on 2008-10-25
I know that people were getting some sorts of errors with the latest version if they didnt' have the following variable defined in the session:
```
export OOO_FORCE_DESKTOP=gnome
```
And maybe this thread will be helpful as well: [http://bbs.archlinux.org/viewtopic.php?id=57301]("http://bbs.archlinux.org/viewtopic.php?id=57301")

---

### Post by phoochka on 2008-10-25
Yup, I had the same problem and put the code ```
export OOO_FORCE_DESKTOP=gnome
```in my autostart.sh and it worked fine after that.

---

### Post by Darkade on 2008-10-25
Thanks that worked, I dunno why becouse I use openbox :lolflag: but it worked
Anyway we do we need to set that variable? hummmm

Thanks again :D

---

### Post by Barrucadu on 2008-10-26
If you haven't already, just stick it in your /etc/profile.

---

