---
title: "pygtk-2.0"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by Namingishard on 2007-10-08
So when trying to install a .tar, After extraction when i type ./configure it goes for awhile then stops and says No package 'pygtk-2.0' found

---

### Post by FuturePilot on 2007-10-08
Run this and then try ./configure again
```
sudo apt-get install python-gtk2-dev
```
You also need the build-essential package if you are compiling something. Install it if you haven't already
```
sudo apt-get install build-essential
```

---

### Post by Namingishard on 2007-10-08
Thanks, Yeah i have build-essentials installed already, but now its saying
No package 'pycairo' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PYCAIRO_CFLAGS
and PYCAIRO_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

---

### Post by FuturePilot on 2007-10-08
```
sudo apt-get install python-cairo-dev
```

---

### Post by Namingishard on 2007-10-08
Thanks again, But now its saying
```

No package 'libwnck-1.0' found
No package 'gnome-desktop-2.0' found
No package 'libgnome-2.0' found
No package 'gnome-vfs-2.0' found
No package 'gconf-2.0' found
No package 'dbus-glib-1' found
No package 'libglade-2.0' found
No package 'xdamage' found
No package 'xcomposite' found

```
Is it normal for it to not find all these files? seems odd.

---

### Post by FuturePilot on 2007-10-08
I think what you need to do is go through Synaptic and install all of the development packages for those. They will end in -dev. Example: libwnck-dev

---

