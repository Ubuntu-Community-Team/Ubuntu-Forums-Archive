---
title: "Anjuta install error ...."
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-05-27
I tried to install Anjuta v2.1.3 from download - because Ubuntu package install only installed the v1.2.4a version.

It is complaining that it needs gdl-1.0 but that is not in the repositories nor can I find it via a Google search.

Any ideas?

Thanks

Carl


PS:  here is the error from anjuta ./configure:

checking for GDL... configure: error: Package requirements (gdl-1.0 >= 0.7.3 gdl-gnome-1.0 >= 0.7.3) were not met:

Requested 'gdl-1.0 >= 0.7.3' but version of gdl is 0.6.1
No package 'gdl-gnome-1.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GDL_CFLAGS
and GDL_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

---

