---
title: "[SOLVED] Compile error for wxWidgets-2.8.7 please help?"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by hopelessone on 2008-01-03
hi,

Trying to install wxWidgets-2.8.7..

error:
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

What do i do?

Thanks

---

### Post by Perfect Storm on 2008-01-03
What's the reason to compile wxwidgets?
You can get it via synaptic.

to answer your question, you need to install; libgtk2.0-dev

---

### Post by hopelessone on 2008-01-03
Thanks !!

i'm trying to fix this:
[http://forum.amule.org/index.php?topic=14081.0](http://forum.amule.org/index.php?topic=14081.0)

---

### Post by hopelessone on 2008-01-03
Sorry 

1 more error:

checking for GL/gl.h... no
configure: error: OpenGL libraries not available

 OpenGL libraries ??

what do i do

thanks..

---

### Post by Perfect Storm on 2008-01-03
sudo aptitude install libgl1-mesa-dev libglu1-mesa-dev

should do it. When it's done and before you run make command let me see the whole ./configure output to be on the safe side.

---

### Post by hopelessone on 2008-01-03
Thank Q x 10...

---

