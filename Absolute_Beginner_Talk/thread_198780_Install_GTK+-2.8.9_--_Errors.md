---
title: "Install GTK+-2.8.9 -- Errors"
date: 2006-06-17
forum: Absolute Beginner Talk
---

### Post by pkroks on 2006-06-17
I'm trying to install a new version of GTK+. I downloaded the source package from  [ftp://ftp.gtk.org/pub/gtk/v2.8/](ftp://ftp.gtk.org/pub/gtk/v2.8/)

When trying to install the package I keep getting errors. Some of the errors include:

When trying to install Cairo
/tmp/cc4qpSPc.s: Assembler messages:
/tmp/cc4qpSPc.s:8064: Error: symbol `_cairo_pixman_composite' is already defined
make[3]: *** [fbpict.lo] Error 1
make[3]: Leaving directory `/home/mpk/Stuff/new stuff/cairo-1.0.2/pixman/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/mpk/Stuff/new stuff/cairo-1.0.2/pixman'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/mpk/Stuff/new stuff/cairo-1.0.2'
make: *** [all] Error 2


When trying to install tiff
make: *** [install-recursive] Error 1

And some others, which I haven't copied yet. 

Does anyone have the command for installing the new version via the repositories and apt-get? 

Or just advice on how to install it would be good. Thanks

I am on Dapper Drake as well.

---

### Post by pkroks on 2006-06-18
Anyone?

---

### Post by pkroks on 2006-06-18
Another friendly bump.

---

