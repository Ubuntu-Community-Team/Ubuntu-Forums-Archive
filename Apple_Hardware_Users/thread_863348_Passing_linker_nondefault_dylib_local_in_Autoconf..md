---
title: "Passing linker nondefault dylib local in Autoconf.in"
date: 2008-07-18
forum: Apple Hardware Users
---

### Post by Kaniknas on 2008-07-18
I am attempting to install GXSM, an open source scanning microscope controller, on a mac mini running Leopard. However, the compilation fails due to a known error with the gcc linker seen here: Technical Q&A QA1567: Compiling X11 / OpenGL applications on Mac OS X v.10.5 Leopard. Basically, when gcc calls -L/usr/X11R6/lib, the linker sees two copies of libGl.dylib in the default path and compilation fails. The apple devs offer a workaround by telling it to look explicitly to one particular path, i.e. use

-L/usr/X11R6/lib -lGL -lX11 -dylib_file \
/System/Library/Frameworks/OpenGL.framework/Versions/A/Libraries/libGL.dylib:\
/System/Library/Frameworks/OpenGL.framework/Versions/A/Libraries/libGL.dylib

My question is how do I pass this along to the linker in configure.in? I have searched through a lot of the autotools manuals, but I haven't found a good way of doing this-I would prefer not to just hack the makefile as that isn't a good long term solution since I'll have to deal with the same problem whenever I update the system.

Thanks-

---

