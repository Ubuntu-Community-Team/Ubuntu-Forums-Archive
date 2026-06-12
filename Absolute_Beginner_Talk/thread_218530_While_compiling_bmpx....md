---
title: "While compiling bmpx..."
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by dwele on 2006-07-18
I have such problem while compiling BMPx:```
configure: WARNING: The --disable-gui switch was not passed to configure, but
building without the GUI since the X11 headers/libraries were not found
checking for GST... configure: error: Package requirements (gstreamer-0.10 >= 0.10.6) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the GST_CFLAGS and GST_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.
```

What to do?

Thx...

---

### Post by Klemik on 2006-07-18
Hmm maybe try do update/re-install gstreamer package.

---

### Post by dwele on 2006-07-18
OK, but now i have another problem while compiling BMPx: ```
configure: error: conditional "HAVE_LIBNOTIFY" was never defined.
Usually this means the macro was only invoked conditionally.
```

What to do with that?

---

