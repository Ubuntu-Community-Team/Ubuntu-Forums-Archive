---
title: "configuration problem"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by n16_vishnoi on 2007-05-22
i m installing a package , it is showing the following error...

checking for pkg-config... /usr/bin/pkg-config
checking for GTK_CFLAGS...
checking for GTK_LIBS...
configure: error: Package requirements (gtk+-2.0 >= 2.0.0 pango >= 1.0 atk >= 1.0) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the GTK_CFLAGS and GTK_LIBS environment variables
to avoid the need to call pkg-config. See the pkg-config man page for
more details.

what is solution for this error...............................

---

### Post by tkjacobsen on 2007-05-22
Looks like you need to install

libgtk2.0-dev
libpango1.0-dev
libatk1.0-dev

Can all be found using synaptic. System->administration->synaptic package manager

Assuming you're using Ubuntu Feisty (7.04)

---

