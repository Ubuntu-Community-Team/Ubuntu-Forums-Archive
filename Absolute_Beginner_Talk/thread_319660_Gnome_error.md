---
title: "Gnome error"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by stupidkid on 2006-12-16
Hello, whenever I log into Gnome, it takes several minutes. Then it shows an error on not loading gnome-settings-daemon.

```
There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work 
correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application 
did not send a reply, the message bus security policy blocked the reply, 
the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log 
in.
```

Here's my .xsession-errors

```

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "tyler"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/linster:/tmp/.ICE-unix/4428
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
evolution-alarm-notify-Message: Setting timeout for 65096 1166313600 1166248504
evolution-alarm-notify-Message:  Sat Dec 16 19:00:00 2006

evolution-alarm-notify-Message:  Sat Dec 16 00:55:04 2006


(gnome-panel:4512): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -5 and height 25

(gnome-theme-manager:4602): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-theme-manager:4602): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-theme-manager:4602): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-theme-manager:4602): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-theme-manager:4602): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-theme-manager:4602): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-theme-manager:4602): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-theme-manager:4602): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-theme-manager:4602): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-theme-manager:4602): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-theme-manager:4602): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-theme-manager:4602): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-theme-manager:4602): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-theme-manager:4602): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-theme-manager:4602): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-theme-manager:4602): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-theme-manager:4602): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-theme-manager:4602): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-theme-manager:4602): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-theme-manager:4602): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-theme-manager:4602): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-theme-manager:4602): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-theme-manager:4602): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-theme-manager:4602): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-theme-manager:4602): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

```

How can I fix this?

Thanks.

---

### Post by aysiu on 2006-12-16
Maybe [this](http://72.14.253.104/search?q=cache:uGtokR-j8XsJ:forum.xfce.org/index.php%3Ftopic%3D2396.msg10346+Gtk-WARNING+**:+Unable+to+locate+theme+engine+in+module_path:+%22pixmap%22&hl=en&gl=us&ct=clnk&cd=1) might help?

---

### Post by Ominide on 2007-01-04
this is the same error that i get but the link doesn't work.

---

### Post by scifan2 on 2007-01-21
Try installing "gtk-engines-pixmap" ... you may need to install gtk-engines-pixbuf as well...

---

