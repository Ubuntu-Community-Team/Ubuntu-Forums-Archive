---
title: "[SOLVED] error ./configure"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by olddoser on 2007-08-04
When doing ./ configure to install gsambad received the following error.  Cannot find anything in Synaptic for this item.   What to do next?

checking for PACKAGE... configure: error: Package requirements (gtk+-2.0 >= 1.3. 13) were not met:

No package 'gtk+-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PACKAGE_CFLAGS
and PACKAGE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

Thanks

Edit: Sorry running Dapper

---

### Post by taurus on 2007-08-04
Looks like you don't have package gtk+2.0 on your machine.  Use synaptic and search for that package (and the -dev package as well).  Then, install it before you try to build something from source again.

---

### Post by olddoser on 2007-08-04
Can I assume that those starting with "libgtk2.0....." would be correct ones.  I see three out of six installed if this is true then just install all of the uninstalled ones?

Thanks taurus

---

### Post by olddoser on 2007-08-04
Solved needed the dev package.

Thanks

---

