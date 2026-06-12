---
title: "Buoh....comic reader install"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by MrKlean on 2007-01-19
Ok.. I read the install file and did what it says,,or tried to...here's the end of what I got.. it says files are missing, but they're not ; (  Any thots ??
Thanks

checking for BUOH... configure: error: Package requirements (glib-2.0       >= 2.6.0
                  gtk+-2.0       >= 2.6.0
                  libsoup-2.2    >= 2.2.0
                  gconf-2.0      >= 2.2.0) were not met:

No package 'glib-2.0' found
No package 'gtk+-2.0' found
No package 'libsoup-2.2' found
No package 'gconf-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BUOH_CFLAGS
and BUOH_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

---

### Post by hod139 on 2007-01-19
You need to install the development packages: libglib2.0-dev libgtk2.0-dev libsoup2.2-dev libgconf2-dev.

Those 4 packages will install the missing headers and libraries.  In general any *-dev package installs the files needed for building from source.

---

### Post by MrKlean on 2007-01-19
I thot they were ; (  I'll check again...thanks ; )

---

### Post by MrKlean on 2007-01-19
Thanks Hod...that did it ; )  Now all I have to do is add it to the menus ; )
thanks again ; )

---

