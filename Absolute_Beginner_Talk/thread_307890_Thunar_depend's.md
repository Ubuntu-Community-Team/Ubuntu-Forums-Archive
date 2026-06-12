---
title: "Thunar depend's"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by Ben Sprinkle on 2006-11-27
Hello everyone, does anyone know all the dependancies for Thunar?
I know synaptic will install them but this is for another distro.

[http://archive.ubuntu.com/ubuntu/pool/main/t](http://archive.ubuntu.com/ubuntu/pool/main/t)

The 3 thunar folders there, that all I need?

---

### Post by konst88 on 2006-11-27
```
aptitude show <package name>
```
It will show you all the information, with dependencies.

---

### Post by Ben Sprinkle on 2006-11-27
Can you do it for me? Not at Linux right now and I need to know.

---

### Post by konst88 on 2006-11-27
```
libatk1.0-0 (>= 1.12.1), libc6 (>= 2.4-1), libcairo2 (>= 1.2.4),
         libdbus-1-3, libdbus-glib-1-2 (>= 0.71), libexo-0.3-0 (>= 0.3.1.10),
         libfreetype6 (>= 2.2), libglib2.0-0 (>= 2.12.0), libgtk2.0-0 (>=
         2.10.3), libice6, libpango1.0-0 (>= 1.14.3), libsm6, libthunar-vfs-1-2,
         libxfce4util4, xfce4-panel, desktop-file-utils, shared-mime-info,
         pmount

```

---

### Post by Ben Sprinkle on 2006-11-27
Ah, thanks. :)

---

### Post by CatKiller on 2006-11-27
For future reference: [Package: thunar (0.4.0svn+r23151-0ubuntu1)]("http://packages.ubuntu.com/edgy/x11/thunar")

Don't forget that the dependencies (those with the red circle) may also have unmet dependencies of their own.

---

