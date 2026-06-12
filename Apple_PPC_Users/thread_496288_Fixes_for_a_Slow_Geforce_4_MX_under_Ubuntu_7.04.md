---
title: "Fixes for a Slow Geforce 4 MX under Ubuntu 7.04?"
date: 2007-07-09
forum: Apple PPC Users
---

### Post by 0graham0 on 2007-07-09
Anyone have tips on getting the graphics card in my powerbook G4 working better under ubuntu 7.04? (I believe its a nVidia GeForce4 420 Go 32M) Right now any 3d programs crash or run excruciatingly slow.

thanks

---

### Post by stmiller on 2007-07-09
Hey there is no real 3D driver for Nvidia chips in PowerPC Linux. Nvidia has not ever made any, nor released any hardware info for an open source version.  For right now, make sure the 'nv' driver is specified in your xorg config file.

Open a terminal, and
```

$ sudo gedit /etc/X11/xorg.conf

```
and look for the line that says Driver, and make it say nv.
```

Devices
    Driver   "nv"

```
Save and close, then restart X (control+ALT+Backspace[delete key] )

There is a project here: [http://nouveau.freedesktop.org/wiki/](http://nouveau.freedesktop.org/wiki/) which is making open source Nvidia drivers. So that should be coming soon. I think they may already have workable drivers? Anyone know?

---

### Post by 0graham0 on 2007-07-14
it is set up for nv driver, but i'll keep my eye on the nouveau site. Thanks for the info

graham

---

