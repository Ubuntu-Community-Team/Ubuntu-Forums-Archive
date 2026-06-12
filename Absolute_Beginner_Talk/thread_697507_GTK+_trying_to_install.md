---
title: "GTK+ trying to install"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by stowaway on 2008-02-15
Hello, 
i havent clock many hours on linux yet.

but my intentions are to get GTK+ installed so i can start coding in ubuntu. ie windows ect.

However GTK+ has alot of dependencies i thought everything install properly. except it still gives this error: (i thought i installed cairo, and pkg-configure and the rest)

I have no idea hwo to change the enviroment variable or where it would be located? most of the stuff i did apt-get if i could. if not i ./configured make and make insalled it. 

----------------------

checking pkg-config is at least version 0.9.0... yes
checking for BASE_DEPENDENCIES... configure: error: Package requirements (glib-2.0 >= 2.13.5    atk >= 1.9.0    pango >= 1.17.3    cairo >= 1.2.0) were not met:

No package 'cairo' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BASE_DEPENDENCIES_CFLAGS
and BASE_DEPENDENCIES_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

---

### Post by the_darkside_986 on 2008-02-15
Did you install the associated packages that have a similar name except they end with "-dev" such as gtk2-dev? That should resolve the error, and automatically select the dev packages of glib, pango, cairo, etc. If not then you might be able to install the "-dev" packages of those failed dependencies.

---

