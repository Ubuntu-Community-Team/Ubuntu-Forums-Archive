---
title: "Install X-Server"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by jayser on 2007-08-23
Hello,

i just install the server and tried to install X-Server by typing in " sudo apt-get install xserver-xorg"

I got this error"not available but is referred to by another package. This may mean that the package is missing, has be obsoleted, or only available from another source
E: Package Xserver-xorg has no installation candidate.

Any clues on this?
Thanks,
Jay

---

### Post by asmoore82 on 2007-08-23
start with

```
~ $ sudo apt-get update
```

and then if you are trying to obtain a Desktop Environment use the metapackages ...

```
~ $ sudo apt-get install ubuntu-desktop
```
-OR-
```
~ $ sudo apt-get install kubuntu-desktop
```
-OR-
```
~ $ sudo apt-get install xubuntu-desktop
```

GNOME/KDE/Xfce, respectively.

---

### Post by RedSquirrel on 2007-08-23
If you don't want to use a full desktop environment, here are two links that will help you install a minimal graphical environment:

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

---

### Post by jayser on 2007-08-27
I noticed that before with version 6 i was able to install xserver.xorg and launch xserver not the desktop. What changed?

Thanks,

---

### Post by RedSquirrel on 2007-08-27
> **jayser said:**
> I noticed that before with version 6 i was able to install xserver.xorg and launch xserver not the desktop. What changed?

Thanks,

I'm not sure what has changed, but with edgy and feisty I have always used the 'xorg' metapackage. Here is its description:

> **X.Org X Window System **
This metapackage provides the components for a standalone
workstation running the X Window System.  It provides the X libraries, [B][COLOR=Blue]an X
server[/COLOR][/B], a set of fonts, and a group of basic X clients and utilities.
'xserver-xorg':

> **the X.Org X server **
This package depends on the full suite of the server and drivers for the
X.Org X server, as well as providing a configuration infrastructure to manage
xorg.conf.  **[COLOR=Red]It does not provide the actual server itself[/COLOR]**[COLOR=Red], [COLOR=black]but removing it
is strongly discouraged.[/COLOR][/COLOR]


---

