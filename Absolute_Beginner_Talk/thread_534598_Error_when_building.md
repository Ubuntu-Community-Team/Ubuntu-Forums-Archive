---
title: "Error when building"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by ladida on 2007-08-25
Hello guys, I'm trying to install kiba-dock, and I got this error:


checking for SVG... configure: error: Package requirements (librsvg-2.0 >= 2.13.91) were not met:

No package 'librsvg-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables SVG_CFLAGS
and SVG_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


What do I do?

Thanks

---

### Post by PurposeOfReason on 2007-08-25
Try "sudo apt-get install librsvg-2.0" and do it again.

---

### Post by Frak on 2007-08-25
Try
```
sudo aptitude install librsvg2-dev
```

---

