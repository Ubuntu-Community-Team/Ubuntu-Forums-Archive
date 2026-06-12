---
title: "Geyes"
date: 2005-12-19
forum: Absolute Beginner Talk
---

### Post by maatghandi on 2005-12-19
Does anyone know if there is a source for additional eyes for the geyes thingy that you can put on the desktop panel? Or, can I make my own? Don't know much about programming, but I can fool around with photoshop and the such.

Peace,
Shroomie

---

### Post by morganth on 2005-12-19
```
**isilando@esper:~$** sudo apt-cache search xeyes
Password:
tuxeyes - a fancy version of xeyes
xfce4-toys - Eyes plugin for Xfce4 panel and xfce4-tips
xeyes - X client - xeyes
**isilando@esper:~$** apt-cache show tuxeyes
_Package: tuxeyes_
Priority: optional
Section: universe/x11
Installed-Size: 1272
Maintainer: Laszlo Boszormenyi (GCS) <gcs@debian.hu>
Architecture: i386
Version: 0.0.3-7build1
Depends: libc6 (>= 2.3.4-1), libgcc1 (>= 1:4.0.0-7), libice6,
libqt3-mt (>= 3:3.3.4), libsm6, libstdc++6 (>= 4.0.0-7),
libx11-6 | xlibs (>> 4.1.0), libxext6 | xlibs (>> 4.1.0)
Suggests: menu
Filename: pool/universe/t/tuxeyes/tuxeyes_0.0.3-7build1_i386.deb
Size: 174206
MD5sum: 8fad6032bfb916d1f6fd17a25d58cdd4
[U]Description: a fancy version of xeyes
 This package displays Tux, Chuck (the BSD daemon), Luxus, or Dust Puppy
 following your mouse cursor in X with their eyes.[/U]
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
```

The same results appear in Synaptc of course ;-) So if synaptic is handier for you, it's  under System>Administration.

Peace :-({|=

---

