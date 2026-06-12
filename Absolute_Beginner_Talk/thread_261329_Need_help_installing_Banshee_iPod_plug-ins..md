---
title: "Need help installing Banshee iPod plug-ins."
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by furste on 2006-09-20
I'm new. Running Dapper 6.06.

When i follow the instructions to install the 'libipoddevice' tarball package (by cd-ing to the folder and then ./configure) that i downloaded from Banshee-project.org (the website of the linux program that supposedly has the best iPod support), everything's fine until  it tells me this:

```
checking for GLIB - version >= 2.0.0... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.
checking pkg-config is at least version 0.9.0... yes
checking for LID... configure: error: Package requirements (gobject-2.0         glib-2.0 >= 2.6.0       dbus-1  dbus-glib-1 hal >= 0.5.2     libgtop-2.0 >= 2.12.0   libxml-2.0) were not met:

No package 'gobject-2.0' found
No package 'glib-2.0' found
No package 'dbus-1' found
No package 'dbus-glib-1' found
No package 'hal' found
No package 'libgtop-2.0' found
No package 'libxml-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LID_CFLAGS
and LID_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

I've been trying to install what it says i'm missing in synaptic, but synaptic says i've got the latest of gobject, glib and the rest.


thanks in advance, i've been irritated to tears for days because of this.

Furste

---

### Post by croak77 on 2006-09-20
You need the xxx-dev packages when compiling. So if its looking for gobject, you will need python-gobject-dev installed. Glib would be libglib2.0-dev. Same with any others you need.

---

