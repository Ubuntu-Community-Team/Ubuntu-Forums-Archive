---
title: "Error with gtkpod"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by disappearedng on 2008-02-22
when I typed ./configure in terminal under the gtkpod directory,
I get this
"checking for XML::Parser... ok
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for LIBGPOD... configure: error: Package requirements (glib-2.0 >= 2.8.0 gobject-2.0) were not met:

No package 'glib-2.0' found
No package 'gobject-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LIBGPOD_CFLAGS
and LIBGPOD_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
"

what does this mean? how do I fix it?

---

### Post by Crooksey on 2008-02-22
```

$ sudo apt-get update
$ sudo apt-get install gtkpod
```

Or was there a reason for not using apt?

---

