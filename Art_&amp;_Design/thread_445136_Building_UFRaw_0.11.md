---
title: "Building UFRaw 0.11"
date: 2007-05-15
forum: Art &amp; Design
---

### Post by nick_edwards on 2007-05-15
Just bought a new camera - Pentax K10d and unfortunately my installed version of UFRaw does not support it. It seems I need the latest version - 0.11, unfortunately the repositories only have outdated versions. So I downloaded the source and tried to compile it (nervously as I never seem to have any luck with this - I wish I knew what I was doing) and I get an "error 3" in a file called "libgimp_raw.o" (I'll check this when I get home this evening).
Anyway has anyone had any luck installing this, I really need to get this working any help is appreciated.

---

### Post by mahavishnu on 2007-05-26
Unfortunately repositories only have the 0.5 version dated to 2005.
I need the new 0.11 version (march/2007).
When I run ./configure it doen't find GTK:


[B]checking for GTK... configure: error: Package requirements (gtk+-2.0 >= 2.4) were not met:

No package 'gtk+-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GTK_CFLAGS
and GTK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.[/B]

---

### Post by avomartin on 2007-05-28
I got a binary deb file in [http://www.getdeb.net/release.php?id=421]("http://www.getdeb.net/release.php?id=421") and installed ok in feisty

Cheers

---

