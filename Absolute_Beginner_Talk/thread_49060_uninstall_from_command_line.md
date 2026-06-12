---
title: "uninstall from command line"
date: 2005-07-14
forum: Absolute Beginner Talk
---

### Post by beamo on 2005-07-14
How do I uninstall azureus from the command line? My add/remove applications program is not working.

---

### Post by az on 2005-07-14
[QUOTE=beamo]How do I uninstall azureus from the command line? My add/remove applications program is not working.[/QUOTE]
If you installed it by means of a debian package, the add/remove thinggie is a Gnome thing and limited.

Use synaptic and remove the package with that tool.  The add/remove package is only a small portion of Synaptic.

If you installed it from source, by unpacking a tarball and running the install script (or compiling it)  you will have to run the uninstall script (ort make uninstall, if you compiled it and it has a proper makefile)

---

### Post by beamo on 2005-07-14
Thanks, I used synaptic to install it and didn't realize it would remove it too.

---

