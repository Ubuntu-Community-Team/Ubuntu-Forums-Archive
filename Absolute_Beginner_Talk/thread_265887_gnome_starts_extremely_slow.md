---
title: "gnome starts extremely slow"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by DSn0wMan on 2006-09-26
Gnome starts extremely slow (3 -  5 min) on my new install (dapper) after configuring wpa_supplicant. It comes up fine until I login, then just seems to hang for 3 to 5 min with a brown screen before finally loading my gnome desktop.

I am not sure if this helps, but here is my .xsession-errors file:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "josh"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/l33t-mobile:/tmp/.ICE-unix/4795
Gnome-Message: gnome_execute_async_with_env_fds: returning -1

(gnome-panel:4901): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed

(gnome-panel:4901): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -9 and height 24

---

### Post by DSn0wMan on 2006-09-26
Never mind. I fixed it. I had accidently removed the local loopback interface from /etc/network/interfaces.

---

