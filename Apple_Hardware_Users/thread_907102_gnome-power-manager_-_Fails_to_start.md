---
title: "gnome-power-manager - Fails to start"
date: 2008-09-01
forum: Apple Hardware Users
---

### Post by jackiemcghee on 2008-09-01
Hoping someone here will be able to help me out on this one.

I've got a 1st gen Macbook Pro running Hardy (single boot) and recently my gnome-power-manager has been failing at login, and now, more worryingly it won't even start when I invoke it from the terminal or Gnome Do.

Running 'gnome-power-manager --no-daemon' gives the following:
```
(gnome-power-manager:9016): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.16.4/gobject/gsignal.c:1669: signal `brightness-changed' is invalid for instance `0x81b75b0'
Segmentation fault
```

What I can't understand is why this worked just fine for a while and now barfs every time I try to use it. Since this has begun I've installed pommed to let me use the function keys to control brightness and volume but I can't switch off that annoying keyboard backlight and the machine feels like it's running a little hot.

If there's anything I can do to generate more information on the fault, just let me know. I'm at the limits of my knowledge here.

---

