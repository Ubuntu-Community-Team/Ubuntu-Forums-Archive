---
title: "Uninstalling stuff"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by Enter on 2006-07-15
Ok so i was trying to install GimpShop following this: [http://linux.suramya.com/tutorials/Install_GIMPShop/](http://linux.suramya.com/tutorials/Install_GIMPShop/)

After I installed everything it said to install i got on installing gimpshop and when I try run the ./configure it gives me this error

checking for pkg-config... /usr/bin/pkg-config
checking for GLIB - version >= 2.4.5...
*** 'pkg-config --modversion glib-2.0' returned 2.6.3, but GLIB (2.10.3)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error: Test for GLIB failed. See the file 'INSTALL' for help.


Can anyone tell me how to fix this or how to uninstall the glib 2.6.3 which  is installed from source?

---

### Post by jehnx on 2006-08-13
Yeah, you'll definitely want to update your GLIB, as it's out of date considerably and [GIMPshop](http://www.gimpshop.com) has been known to give errors if it's not pretty up-to-date.  2.10 is the current version of it, I believe, available [here](http://www.gtk.org/download/).

To uninstall it, you should be able to "sudo make uninstall" on the source files.

---

