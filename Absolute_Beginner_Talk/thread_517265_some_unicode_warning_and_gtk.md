---
title: "some unicode warning and gtk"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by kinngg on 2007-08-04
checking for zlib.h >= 1.1.4... no
checking for zlib.h... (cached) no
configure: WARNING: zlib library not found or too old, will use built-in instead
checking for png.h > 0.90... no
checking for png.h... (cached) no
configure: WARNING: system png library not found or too old, will use built-in instead
checking for jpeglib.h... no
configure: WARNING: system jpeg library not found, will use built-in instead
checking tiffio.h usability... no
checking tiffio.h presence... no
checking for tiffio.h... no
configure: WARNING: system tiff library not found, will use built-in instead
checking expat.h usability... no
checking expat.h presence... no
checking for expat.h... no
configure: WARNING: system expat library not found, will use built-in instead
checking mspack.h usability... no
checking mspack.h presence... no
checking for mspack.h... no
checking for GTK+ version... 
checking for pkg-config... /usr/bin/pkg-config
checking for GTK+ - version >= 2.0.0... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.
configure: error:
The development files for GTK+ were not found. For GTK+ 2, please
ensure that pkg-config is in the path and that gtk+-2.0.pc is
installed. For GTK+ 1.2 please check that gtk-config is in the path,
and that the version is 1.2.3 or above. Also check that the
libraries returned by 'pkg-config gtk+-2.0 --libs' or 'gtk-config
--libs' are in the LD_LIBRARY_PATH or equivalent.

---

### Post by kinngg on 2007-08-04
i forgot to say.. wats da problem? i cant seem to figure it out

---

