---
title: "How are .so files created for usplash images on boot"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by moebob24 on 2008-01-31
On the boot screen (ubuntu logo with orange bar loading) I need a .so file to customize this.
I can do this via the GUI utility so all I need now is a .so file to go with the image I want displayed on boot.

---

### Post by PeterJS on 2008-01-31
.so is the extension for Share Object libraries. The .so files used to create usplash themes are actually small C programs that just display the splash image and manage the loading bar, and where the boot messages appear (and what font) if enabled. As for making you're own, couldn't tell you, try google? If you search on gnome-look for usplash a few turn up. Good luck, if you find any really cool tools for creating the .c files from existing images let us know.

---

