---
title: "installing gtk+ but glib needs to be upgraded"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by elpico on 2006-10-18
Hi all,

I've trawled through the forum's looking for answers, but I've been going around circles with this. I need to get gtk+ installed (version 2.10.6), but it comes back with an error 

checking for pkg-config... /usr/bin/pkg-config
checking for GLIB - version >= 2.12.0...
*** 'pkg-config --modversion glib-2.0' returned 2.12.4, but GLIB (2.10.3)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error:


Now, I've tried to uninstall the old version of glib, but am having problems doing this - Any idea how I can do this? I've tried aptitude, but failed to find it as an installed package? Any help much appreciated!

Thanks,
elpico.#:-|

---

