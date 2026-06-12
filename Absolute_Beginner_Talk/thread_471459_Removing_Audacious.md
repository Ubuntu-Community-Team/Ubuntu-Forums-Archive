---
title: "Removing Audacious"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by Yggdrasill on 2007-06-12
How can I remove Audacious, audacious-plugins, and audacious-plugins-ugly completely from my system?  I tried some terminal commands but was only successful at removing lib packages.  Also, I installed from source, not Synaptic.

---

### Post by Pragmatist on 2007-06-12
> **Yggdrasill said:**
> How can I remove Audacious, audacious-plugins, and audacious-plugins-ugly completely from my system?  I tried some terminal commands but was only successful at removing lib packages.  Also, I installed from source, not Synaptic.

If you compiled it yourself, without converting to a DEB first, then you either use an uninstall script--if it came with the source package, or you manually track down the files.  This is why it is always a good idea to convert the source to a DEB package, so you can use the package manager to keep track of where you are installing things.

---

