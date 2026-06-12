---
title: "desktop effects"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by rkakkar on 2008-01-24
how do i enable desktop effects in kubuntu? looking for translucent window decorations etc.

---

### Post by lluisanunez on 2008-01-24
Install compizconfig-settings-manager
Then go to System > preferences > Advanced desktop settings

---

### Post by Pandemic187 on 2008-01-24
I haven't tried doing so, but [this]("http://ubuntuforums.org/showthread.php?t=601310&highlight=Kubuntu+desktop+effects") thread seems to be a good way of doing it. It's a bit complicated, but I'm guessing that's because Kubuntu isn't as well-developed as Ubuntu is, which the Gusty Gibbon version has installed by default.

---

### Post by CadetD on 2008-01-24
Also after installing Compiz, you will have a new root menu entry: Settings
That is where you turn on the cool new effects (cube and stuff...)
*(banged my head for hours trying to figure that one out.)*

---

### Post by rkakkar on 2008-01-24
> **lluisanunez said:**
> Install compizconfig-settings-manager
Then go to System > preferences > Advanced desktop settings

its blank :P. plus i'm using kubuntu not ubuntu

---

### Post by rkakkar on 2008-01-24
okay fixed it... hadn't install compiz-kde package [:P]... do i have to reboot? because all the options are selected, i don't see any diff

---

### Post by rkakkar on 2008-01-24
rebooted.. but no effects :(

---

### Post by FuturePilot on 2008-01-24
Can you post the output of 
```
compiz
```

---

### Post by rkakkar on 2008-01-24
> **FuturePilot said:**
> Can you post the output of 
```
compiz
```

```
$ compiz
Checking for Xgl: not present.
Detected PCI ID for VGA: 00:02.0 0300: 8086:2562 (rev 03) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present.
Checking for FBConfig: present.
Checking for Xgl: not present.
Starting kde-window-decorator
/usr/bin/compiz.real (dbus) - Error: dbus_bus_get error: Failed to execute dbus-launch to autolaunch D-Bus session
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'dbus'
/usr/bin/compiz.real (blur) - Warn: No stencil buffer. Region based blur disabled

```

it started by my pop up menu window borders are funny..

---

