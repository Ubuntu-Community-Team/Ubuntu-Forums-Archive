---
title: "[Mint] Can not make install Mangler"
date: 2011-07-09
forum: Any Other OS
---

### Post by Candlehawk on 2011-07-09
I am using Mint 11, and am attempting to compile Mangler version 1.2.2 from source. I downloaded and extracted the file, ./configure (and after downloading half a dozen packages it worked) I make it, and that works, then I try to (sudo) make install, I get this:
```
Making install in libventrilo3
make[1]: Entering directory `/home/alex/mangler-1.2.2/libventrilo3'
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..      -g -O2 -pthread -MT libventrilo3.lo -MD -MP -MF .deps/libventrilo3.Tpo -c -o libventrilo3.lo libventrilo3.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I.. -g -O2 -pthread -MT libventrilo3.lo -MD -MP -MF .deps/libventrilo3.Tpo -c libventrilo3.c  -fPIC -DPIC -o .libs/libventrilo3.o
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I.. -g -O2 -pthread -MT libventrilo3.lo -MD -MP -MF .deps/libventrilo3.Tpo -c libventrilo3.c -o libventrilo3.o >/dev/null 2>&1
mv -f .deps/libventrilo3.Tpo .deps/libventrilo3.Plo
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..      -g -O2 -pthread -MT libventrilo3_message.lo -MD -MP -MF .deps/libventrilo3_message.Tpo -c -o libventrilo3_message.lo libventrilo3_message.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I.. -g -O2 -pthread -MT libventrilo3_message.lo -MD -MP -MF .deps/libventrilo3_message.Tpo -c libventrilo3_message.c  -fPIC -DPIC -o .libs/libventrilo3_message.o
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I.. -g -O2 -pthread -MT libventrilo3_message.lo -MD -MP -MF .deps/libventrilo3_message.Tpo -c libventrilo3_message.c -o libventrilo3_message.o >/dev/null 2>&1
mv -f .deps/libventrilo3_message.Tpo .deps/libventrilo3_message.Plo
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..      -g -O2 -pthread -MT ventrilo3_handshake.lo -MD -MP -MF .deps/ventrilo3_handshake.Tpo -c -o ventrilo3_handshake.lo ventrilo3_handshake.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I.. -g -O2 -pthread -MT ventrilo3_handshake.lo -MD -MP -MF .deps/ventrilo3_handshake.Tpo -c ventrilo3_handshake.c  -fPIC -DPIC -o .libs/ventrilo3_handshake.o
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I.. -g -O2 -pthread -MT ventrilo3_handshake.lo -MD -MP -MF .deps/ventrilo3_handshake.Tpo -c ventrilo3_handshake.c -o ventrilo3_handshake.o >/dev/null 2>&1
mv -f .deps/ventrilo3_handshake.Tpo .deps/ventrilo3_handshake.Plo
/bin/bash ../libtool --tag=CC   --mode=link gcc  -g -O2 -pthread -version 0:0:0  -o libventrilo3.la -rpath /usr/local/lib libventrilo3.lo libventrilo3_message.lo ventrilo3_handshake.lo -lspeex    -lgsm   -lm -lgsm  
libtool: link: gcc -shared  .libs/libventrilo3.o .libs/libventrilo3_message.o .libs/ventrilo3_handshake.o   -lspeex -lm -lgsm  -pthread   -pthread -Wl,-soname -Wl,libventrilo3.so.0 -o .libs/libventrilo3.so.0.0.0
libtool: link: (cd ".libs" && rm -f "libventrilo3.so.0" && ln -s "libventrilo3.so.0.0.0" "libventrilo3.so.0")
libtool: link: (cd ".libs" && rm -f "libventrilo3.so" && ln -s "libventrilo3.so.0.0.0" "libventrilo3.so")
libtool: link: ar cru .libs/libventrilo3.a  libventrilo3.o libventrilo3_message.o ventrilo3_handshake.o
libtool: link: ranlib .libs/libventrilo3.a
libtool: link: ( cd ".libs" && rm -f "libventrilo3.la" && ln -s "../libventrilo3.la" "libventrilo3.la" )
make[2]: Entering directory `/home/alex/mangler-1.2.2/libventrilo3'
test -z "/usr/local/lib" || /bin/mkdir -p "/usr/local/lib"
 /bin/bash ../libtool   --mode=install /usr/bin/install -c   libventrilo3.la '/usr/local/lib'
libtool: install: /usr/bin/install -c .libs/libventrilo3.so.0.0.0 /usr/local/lib/libventrilo3.so.0.0.0
libtool: install: (cd /usr/local/lib && { ln -s -f libventrilo3.so.0.0.0 libventrilo3.so.0 || { rm -f libventrilo3.so.0 && ln -s libventrilo3.so.0.0.0 libventrilo3.so.0; }; })
libtool: install: (cd /usr/local/lib && { ln -s -f libventrilo3.so.0.0.0 libventrilo3.so || { rm -f libventrilo3.so && ln -s libventrilo3.so.0.0.0 libventrilo3.so; }; })
libtool: install: /usr/bin/install -c .libs/libventrilo3.lai /usr/local/lib/libventrilo3.la
libtool: install: /usr/bin/install -c .libs/libventrilo3.a /usr/local/lib/libventrilo3.a
libtool: install: chmod 644 /usr/local/lib/libventrilo3.a
libtool: install: ranlib /usr/local/lib/libventrilo3.a
libtool: finish: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin:/sbin" ldconfig -n /usr/local/lib
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
test -z "/usr/local/include" || /bin/mkdir -p "/usr/local/include"
 /usr/bin/install -c -m 644 ventrilo3.h '/usr/local/include'
make[2]: Leaving directory `/home/alex/mangler-1.2.2/libventrilo3'
make[1]: Leaving directory `/home/alex/mangler-1.2.2/libventrilo3'
Making install in icons
make[1]: Entering directory `/home/alex/mangler-1.2.2/icons'
list=""
for f in *.svg ; do \
		id=`echo $f | perl -pe 's/^(.*)\..*$/$1/'`;  \
		list="$list $id $f";  \
	done ; \
	gdk-pixbuf-csource --raw --build-list $list > mangler-icons.h
make[1]: Leaving directory `/home/alex/mangler-1.2.2/icons'
Making install in sounds
make[1]: Entering directory `/home/alex/mangler-1.2.2/sounds'
./bin2h channelenter.raw channelenter.h sound_channelenter
./bin2h: conversion done
./bin2h channelleave.raw channelleave.h sound_channelleave
./bin2h: conversion done
./bin2h login.raw login.h sound_login
./bin2h: conversion done
./bin2h logout.raw logout.h sound_logout
./bin2h: conversion done
./bin2h talkend.raw talkend.h sound_talkend
./bin2h: conversion done
./bin2h talkstart.raw talkstart.h sound_talkstart
./bin2h: conversion done
cat channelenter.h channelleave.h login.h logout.h talkend.h talkstart.h > mangler-sounds.h
make[1]: Leaving directory `/home/alex/mangler-1.2.2/sounds'
Making install in src
make[1]: Entering directory `/home/alex/mangler-1.2.2/src'
g++ -DHAVE_CONFIG_H -I. -I.. -I../libventrilo3/ -I../icons/ -I../sounds/ -pthread -I/usr/include/atk-1.0 -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/gio-unix-2.0/ -I/usr/include/gtkmm-2.4 -I/usr/lib/gtkmm-2.4/include -I/usr/include/atkmm-1.6 -I/usr/include/giomm-2.4 -I/usr/lib/giomm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/lib/pangomm-1.4/include -I/usr/include/gtk-2.0 -I/usr/include/gtk-unix-print-2.0 -I/usr/include/gdkmm-2.4 -I/usr/lib/gdkmm-2.4/include -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/cairomm-1.0 -I/usr/lib/cairomm-1.0/include -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/lib/gtk-2.0/include -I/usr/include/gdk-pixbuf-2.0   -pthread -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include            -g -O2 -MT mangler.o -MD -MP -MF .deps/mangler.Tpo -c -o mangler.o mangler.cpp
mv -f .deps/mangler.Tpo .deps/mangler.Po
g++ -DHAVE_CONFIG_H -I. -I.. -I../libventrilo3/ -I../icons/ -I../sounds/ -pthread -I/usr/include/atk-1.0 -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/gio-unix-2.0/ -I/usr/include/gtkmm-2.4 -I/usr/lib/gtkmm-2.4/include -I/usr/include/atkmm-1.6 -I/usr/include/giomm-2.4 -I/usr/lib/giomm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/lib/pangomm-1.4/include -I/usr/include/gtk-2.0 -I/usr/include/gtk-unix-print-2.0 -I/usr/include/gdkmm-2.4 -I/usr/lib/gdkmm-2.4/include -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/cairomm-1.0 -I/usr/lib/cairomm-1.0/include -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/lib/gtk-2.0/include -I/usr/include/gdk-pixbuf-2.0   -pthread -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include            -g -O2 -MT channeltree.o -MD -MP -MF .deps/channeltree.Tpo -c -o channeltree.o channeltree.cpp
mv -f .deps/channeltree.Tpo .deps/channeltree.Po
g++ -DHAVE_CONFIG_H -I. -I.. -I../libventrilo3/ -I../icons/ -I../sounds/ -pthread -I/usr/include/atk-1.0 -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/gio-unix-2.0/ -I/usr/include/gtkmm-2.4 -I/usr/lib/gtkmm-2.4/include -I/usr/include/atkmm-1.6 -I/usr/include/giomm-2.4 -I/usr/lib/giomm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/lib/pangomm-1.4/include -I/usr/include/gtk-2.0 -I/usr/include/gtk-unix-print-2.0 -I/usr/include/gdkmm-2.4 -I/usr/lib/gdkmm-2.4/include -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/cairomm-1.0 -I/usr/lib/cairomm-1.0/include -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/lib/gtk-2.0/include -I/usr/include/gdk-pixbuf-2.0   -pthread -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include            -g -O2 -MT mangleraudio.o -MD -MP -MF .deps/mangleraudio.Tpo -c -o mangleraudio.o mangleraudio.cpp
mv -f .deps/mangleraudio.Tpo .deps/mangleraudio.Po
g++ -DHAVE_CONFIG_H -I. -I.. -I../libventrilo3/ -I../icons/ -I../sounds/ -pthread -I/usr/include/atk-1.0 -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/gio-unix-2.0/ -I/usr/include/gtkmm-2.4 -I/usr/lib/gtkmm-2.4/include -I/usr/include/atkmm-1.6 -I/usr/include/giomm-2.4 -I/usr/lib/giomm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/lib/pangomm-1.4/include -I/usr/include/gtk-2.0 -I/usr/include/gtk-unix-print-2.0 -I/usr/include/gdkmm-2.4 -I/usr/lib/gdkmm-2.4/include -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/cairomm-1.0 -I/usr/lib/cairomm-1.0/include -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/lib/gtk-2.0/include -I/usr/include/gdk-pixbuf-2.0   -pthread -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include            -g -O2 -MT manglerbackend.o -MD -MP -MF .deps/manglerbackend.Tpo -c -o manglerbackend.o manglerbackend.cpp
mv -f .deps/manglerbackend.Tpo .deps/manglerbackend.Po
g++ -DHAVE_CONFIG_H -I. -I.. -I../libventrilo3/ -I../icons/ -I../sounds/ -pthread -I/usr/include/atk-1.0 -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/gio-unix-2.0/ -I/usr/include/gtkmm-2.4 -I/usr/lib/gtkmm-2.4/include -I/usr/include/atkmm-1.6 -I/usr/include/giomm-2.4 -I/usr/lib/giomm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/lib/pangomm-1.4/include -I/usr/include/gtk-2.0 -I/usr/include/gtk-unix-print-2.0 -I/usr/include/gdkmm-2.4 -I/usr/lib/gdkmm-2.4/include -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/cairomm-1.0 -I/usr/lib/cairomm-1.0/include -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/lib/gtk-2.0/include -I/usr/include/gdk-pixbuf-2.0   -pthread -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include            -g -O2 -MT manglerpulse.o -MD -MP -MF .deps/manglerpulse.Tpo -c -o manglerpulse.o manglerpulse.cpp
mv -f .deps/manglerpulse.Tpo .deps/manglerpulse.Po
g++ -DHAVE_CONFIG_H -I. -I.. -I../libventrilo3/ -I../icons/ -I../sounds/ -pthread -I/usr/include/atk-1.0 -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/gio-unix-2.0/ -I/usr/include/gtkmm-2.4 -I/usr/lib/gtkmm-2.4/include -I/usr/include/atkmm-1.6 -I/usr/include/giomm-2.4 -I/usr/lib/giomm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/lib/pangomm-1.4/include -I/usr/include/gtk-2.0 -I/usr/include/gtk-unix-print-2.0 -I/usr/include/gdkmm-2.4 -I/usr/lib/gdkmm-2.4/include -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/cairomm-1.0 -I/usr/lib/cairomm-1.0/include -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/lib/gtk-2.0/include -I/usr/include/gdk-pixbuf-2.0   -pthread -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include            -g -O2 -MT mangleralsa.o -MD -MP -MF .deps/mangleralsa.Tpo -c -o mangleralsa.o mangleralsa.cpp
mv -f .deps/mangleralsa.Tpo .deps/mangleralsa.Po
g++ -DHAVE_CONFIG_H -I. -I.. -I../libventrilo3/ -I../icons/ -I../sounds/ -pthread -I/usr/include/atk-1.0 -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/gio-unix-2.0/ -I/usr/include/gtkmm-2.4 -I/usr/lib/gtkmm-2.4/include -I/usr/include/atkmm-1.6 -I/usr/include/giomm-2.4 -I/usr/lib/giomm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/lib/pangomm-1.4/include -I/usr/include/gtk-2.0 -I/usr/include/gtk-unix-print-2.0 -I/usr/include/gdkmm-2.4 -I/usr/lib/gdkmm-2.4/include -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/cairomm-1.0 -I/usr/lib/cairomm-1.0/include -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/lib/gtk-2.0/include -I/usr/include/gdk-pixbuf-2.0   -pthread -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include            -g -O2 -MT mangleross.o -MD -MP -MF .deps/mangleross.Tpo -c -o mangleross.o mangleross.cpp
mv -f .deps/mangleross.Tpo .deps/mangleross.Po
g++ -DHAVE_CONFIG_H -I. -I.. -I../libventrilo3/ -I../icons/ -I../sounds/ -pthread -I/usr/include/atk-1.0 -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/gio-unix-2.0/ -I/usr/include/gtkmm-2.4 -I/usr/lib/gtkmm-2.4/include -I/usr/include/atkmm-1.6 -I/usr/include/giomm-2.4 -I/usr/lib/giomm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/lib/pangomm-1.4/include -I/usr/include/gtk-2.0 -I/usr/include/gtk-unix-print-2.0 -I/usr/include/gdkmm-2.4 -I/usr/lib/gdkmm-2.4/include -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/cairomm-1.0 -I/usr/lib/cairomm-1.0/include -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/lib/gtk-2.0/include -I/usr/include/gdk-pixbuf-2.0   -pthread -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include            -g -O2 -MT manglernetwork.o -MD -MP -MF .deps/manglernetwork.Tpo -c -o manglernetwork.o manglernetwork.cpp
mv -f .deps/manglernetwork.Tpo .deps/manglernetwork.Po
g++ -DHAVE_CONFIG_H -I. -I.. -I../libventrilo3/ -I../icons/ -I../sounds/ -pthread -I/usr/include/atk-1.0 -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/gio-unix-2.0/ -I/usr/include/gtkmm-2.4 -I/usr/lib/gtkmm-2.4/include -I/usr/include/atkmm-1.6 -I/usr/include/giomm-2.4 -I/usr/lib/giomm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/lib/pangomm-1.4/include -I/usr/include/gtk-2.0 -I/usr/include/gtk-unix-print-2.0 -I/usr/include/gdkmm-2.4 -I/usr/lib/gdkmm-2.4/include -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/cairomm-1.0 -I/usr/lib/cairomm-1.0/include -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/lib/gtk-2.0/include -I/usr/include/gdk-pixbuf-2.0   -pthread -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include            -g -O2 -MT manglerserverlist.o -MD -MP -MF .deps/manglerserverlist.Tpo -c -o manglerserverlist.o manglerserverlist.cpp
mv -f .deps/manglerserverlist.Tpo .deps/manglerserverlist.Po
g++ -DHAVE_CONFIG_H -I. -I.. -I../libventrilo3/ -I../icons/ -I../sounds/ -pthread -I/usr/include/atk-1.0 -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/gio-unix-2.0/ -I/usr/include/gtkmm-2.4 -I/usr/lib/gtkmm-2.4/include -I/usr/include/atkmm-1.6 -I/usr/include/giomm-2.4 -I/usr/lib/giomm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/lib/pangomm-1.4/include -I/usr/include/gtk-2.0 -I/usr/include/gtk-unix-print-2.0 -I/usr/include/gdkmm-2.4 -I/usr/lib/gdkmm-2.4/include -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/cairomm-1.0 -I/usr/lib/cairomm-1.0/include -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/lib/gtk-2.0/include -I/usr/include/gdk-pixbuf-2.0   -pthread -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include            -g -O2 -MT manglersettings.o -MD -MP -MF .deps/manglersettings.Tpo -c -o manglersettings.o manglersettings.cpp
mv -f .deps/manglersettings.Tpo .deps/manglersettings.Po
g++ -DHAVE_CONFIG_H -I. -I.. -I../libventrilo3/ -I../icons/ -I../sounds/ -pthread -I/usr/include/atk-1.0 -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/gio-unix-2.0/ -I/usr/include/gtkmm-2.4 -I/usr/lib/gtkmm-2.4/include -I/usr/include/atkmm-1.6 -I/usr/include/giomm-2.4 -I/usr/lib/giomm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/lib/pangomm-1.4/include -I/usr/include/gtk-2.0 -I/usr/include/gtk-unix-print-2.0 -I/usr/include/gdkmm-2.4 -I/usr/lib/gdkmm-2.4/include -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/cairomm-1.0 -I/usr/lib/cairomm-1.0/include -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/lib/gtk-2.0/include -I/usr/include/gdk-pixbuf-2.0   -pthread -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include            -g -O2 -MT manglerconfig.o -MD -MP -MF .deps/manglerconfig.Tpo -c -o manglerconfig.o manglerconfig.cpp
mv -f .deps/manglerconfig.Tpo .deps/manglerconfig.Po
g++ -DHAVE_CONFIG_H -I. -I.. -I../libventrilo3/ -I../icons/ -I../sounds/ -pthread -I/usr/include/atk-1.0 -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/gio-unix-2.0/ -I/usr/include/gtkmm-2.4 -I/usr/lib/gtkmm-2.4/include -I/usr/include/atkmm-1.6 -I/usr/include/giomm-2.4 -I/usr/lib/giomm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/lib/pangomm-1.4/include -I/usr/include/gtk-2.0 -I/usr/include/gtk-unix-print-2.0 -I/usr/include/gdkmm-2.4 -I/usr/lib/gdkmm-2.4/include -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/cairomm-1.0 -I/usr/lib/cairomm-1.0/include -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/lib/gtk-2.0/include -I/usr/include/gdk-pixbuf-2.0   -pthread -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include            -g -O2 -MT manglerchat.o -MD -MP -MF .deps/manglerchat.Tpo -c -o manglerchat.o manglerchat.cpp
mv -f .deps/manglerchat.Tpo .deps/manglerchat.Po
g++ -DHAVE_CONFIG_H -I. -I.. -I../libventrilo3/ -I../icons/ -I../sounds/ -pthread -I/usr/include/atk-1.0 -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/gio-unix-2.0/ -I/usr/include/gtkmm-2.4 -I/usr/lib/gtkmm-2.4/include -I/usr/include/atkmm-1.6 -I/usr/include/giomm-2.4 -I/usr/lib/giomm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/lib/pangomm-1.4/include -I/usr/include/gtk-2.0 -I/usr/include/gtk-unix-print-2.0 -I/usr/include/gdkmm-2.4 -I/usr/lib/gdkmm-2.4/include -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/cairomm-1.0 -I/usr/lib/cairomm-1.0/include -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/lib/gtk-2.0/include -I/usr/include/gdk-pixbuf-2.0   -pthread -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include            -g -O2 -MT manglerprivchat.o -MD -MP -MF .deps/manglerprivchat.Tpo -c -o manglerprivchat.o manglerprivchat.cpp
mv -f .deps/manglerprivchat.Tpo .deps/manglerprivchat.Po
g++ -DHAVE_CONFIG_H -I. -I.. -I../libventrilo3/ -I../icons/ -I../sounds/ -pthread -I/usr/include/atk-1.0 -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/gio-unix-2.0/ -I/usr/include/gtkmm-2.4 -I/usr/lib/gtkmm-2.4/include -I/usr/include/atkmm-1.6 -I/usr/include/giomm-2.4 -I/usr/lib/giomm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/lib/pangomm-1.4/include -I/usr/include/gtk-2.0 -I/usr/include/gtk-unix-print-2.0 -I/usr/include/gdkmm-2.4 -I/usr/lib/gdkmm-2.4/include -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/cairomm-1.0 -I/usr/lib/cairomm-1.0/include -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/lib/gtk-2.0/include -I/usr/include/gdk-pixbuf-2.0   -pthread -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include            -g -O2 -MT manglercharset.o -MD -MP -MF .deps/manglercharset.Tpo -c -o manglercharset.o manglercharset.cpp
mv -f .deps/manglercharset.Tpo .deps/manglercharset.Po
g++ -DHAVE_CONFIG_H -I. -I.. -I../libventrilo3/ -I../icons/ -I../sounds/ -pthread -I/usr/include/atk-1.0 -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/gio-unix-2.0/ -I/usr/include/gtkmm-2.4 -I/usr/lib/gtkmm-2.4/include -I/usr/include/atkmm-1.6 -I/usr/include/giomm-2.4 -I/usr/lib/giomm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/lib/pangomm-1.4/include -I/usr/include/gtk-2.0 -I/usr/include/gtk-unix-print-2.0 -I/usr/include/gdkmm-2.4 -I/usr/lib/gdkmm-2.4/include -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/cairomm-1.0 -I/usr/lib/cairomm-1.0/include -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/lib/gtk-2.0/include -I/usr/include/gdk-pixbuf-2.0   -pthread -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include            -g -O2 -MT manglerintegration.o -MD -MP -MF .deps/manglerintegration.Tpo -c -o manglerintegration.o manglerintegration.cpp
mv -f .deps/manglerintegration.Tpo .deps/manglerintegration.Po
g++ -DHAVE_CONFIG_H -I. -I.. -I../libventrilo3/ -I../icons/ -I../sounds/ -pthread -I/usr/include/atk-1.0 -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/gio-unix-2.0/ -I/usr/include/gtkmm-2.4 -I/usr/lib/gtkmm-2.4/include -I/usr/include/atkmm-1.6 -I/usr/include/giomm-2.4 -I/usr/lib/giomm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/lib/pangomm-1.4/include -I/usr/include/gtk-2.0 -I/usr/include/gtk-unix-print-2.0 -I/usr/include/gdkmm-2.4 -I/usr/lib/gdkmm-2.4/include -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/cairomm-1.0 -I/usr/lib/cairomm-1.0/include -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/lib/gtk-2.0/include -I/usr/include/gdk-pixbuf-2.0   -pthread -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include            -g -O2 -MT mangleradmin.o -MD -MP -MF .deps/mangleradmin.Tpo -c -o mangleradmin.o mangleradmin.cpp
mv -f .deps/mangleradmin.Tpo .deps/mangleradmin.Po
g++ -DHAVE_CONFIG_H -I. -I.. -I../libventrilo3/ -I../icons/ -I../sounds/ -pthread -I/usr/include/atk-1.0 -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/gio-unix-2.0/ -I/usr/include/gtkmm-2.4 -I/usr/lib/gtkmm-2.4/include -I/usr/include/atkmm-1.6 -I/usr/include/giomm-2.4 -I/usr/lib/giomm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/lib/pangomm-1.4/include -I/usr/include/gtk-2.0 -I/usr/include/gtk-unix-print-2.0 -I/usr/include/gdkmm-2.4 -I/usr/lib/gdkmm-2.4/include -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/cairomm-1.0 -I/usr/lib/cairomm-1.0/include -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/lib/gtk-2.0/include -I/usr/include/gdk-pixbuf-2.0   -pthread -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include            -g -O2 -MT manglerrecorder.o -MD -MP -MF .deps/manglerrecorder.Tpo -c -o manglerrecorder.o manglerrecorder.cpp
mv -f .deps/manglerrecorder.Tpo .deps/manglerrecorder.Po
g++ -DHAVE_CONFIG_H -I. -I.. -I../libventrilo3/ -I../icons/ -I../sounds/ -pthread -I/usr/include/atk-1.0 -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/gio-unix-2.0/ -I/usr/include/gtkmm-2.4 -I/usr/lib/gtkmm-2.4/include -I/usr/include/atkmm-1.6 -I/usr/include/giomm-2.4 -I/usr/lib/giomm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/lib/pangomm-1.4/include -I/usr/include/gtk-2.0 -I/usr/include/gtk-unix-print-2.0 -I/usr/include/gdkmm-2.4 -I/usr/lib/gdkmm-2.4/include -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/cairomm-1.0 -I/usr/lib/cairomm-1.0/include -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/lib/gtk-2.0/include -I/usr/include/gdk-pixbuf-2.0   -pthread -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include            -g -O2 -MT manglerosd.o -MD -MP -MF .deps/manglerosd.Tpo -c -o manglerosd.o manglerosd.cpp
mv -f .deps/manglerosd.Tpo .deps/manglerosd.Po
g++ -DHAVE_CONFIG_H -I. -I.. -I../libventrilo3/ -I../icons/ -I../sounds/ -pthread -I/usr/include/atk-1.0 -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/gio-unix-2.0/ -I/usr/include/gtkmm-2.4 -I/usr/lib/gtkmm-2.4/include -I/usr/include/atkmm-1.6 -I/usr/include/giomm-2.4 -I/usr/lib/giomm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/lib/pangomm-1.4/include -I/usr/include/gtk-2.0 -I/usr/include/gtk-unix-print-2.0 -I/usr/include/gdkmm-2.4 -I/usr/lib/gdkmm-2.4/include -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/cairomm-1.0 -I/usr/lib/cairomm-1.0/include -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/lib/gtk-2.0/include -I/usr/include/gdk-pixbuf-2.0   -pthread -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include            -g -O2 -MT manglerg15.o -MD -MP -MF .deps/manglerg15.Tpo -c -o manglerg15.o manglerg15.cpp
mv -f .deps/manglerg15.Tpo .deps/manglerg15.Po
g++ -DHAVE_CONFIG_H -I. -I.. -I../libventrilo3/ -I../icons/ -I../sounds/ -pthread -I/usr/include/atk-1.0 -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/gio-unix-2.0/ -I/usr/include/gtkmm-2.4 -I/usr/lib/gtkmm-2.4/include -I/usr/include/atkmm-1.6 -I/usr/include/giomm-2.4 -I/usr/lib/giomm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/lib/pangomm-1.4/include -I/usr/include/gtk-2.0 -I/usr/include/gtk-unix-print-2.0 -I/usr/include/gdkmm-2.4 -I/usr/lib/gdkmm-2.4/include -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/cairomm-1.0 -I/usr/lib/cairomm-1.0/include -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/lib/gtk-2.0/include -I/usr/include/gdk-pixbuf-2.0   -pthread -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include            -g -O2 -MT inilib.o -MD -MP -MF .deps/inilib.Tpo -c -o inilib.o inilib.cpp
mv -f .deps/inilib.Tpo .deps/inilib.Po
/bin/bash ../libtool --tag=CXX   --mode=link g++  -g -O2   -o mangler mangler.o channeltree.o mangleraudio.o manglerbackend.o manglerpulse.o mangleralsa.o mangleross.o manglernetwork.o manglerserverlist.o manglersettings.o manglerconfig.o manglerchat.o manglerprivchat.o manglercharset.o manglerintegration.o mangleradmin.o manglerrecorder.o manglerosd.o manglerg15.o inilib.o ../libventrilo3/libventrilo3.la -pthread -L/usr/lib/x86_64-linux-gnu -lgtkmm-2.4 -latkmm-1.6 -lgdkmm-2.4 -lgiomm-2.4 -lpangomm-1.4 -lgtk-x11-2.0 -lglibmm-2.4 -lcairomm-1.0 -lsigc-2.0 -lgdk-x11-2.0 -latk-1.0 -lgio-2.0 -lpangoft2-1.0 -lpangocairo-1.0 -lgdk_pixbuf-2.0 -lm -lcairo -lpango-1.0 -lfreetype -lfontconfig -lgobject-2.0 -lgmodule-2.0 -lgthread-2.0 -lrt -lglib-2.0   -pthread -L/usr/lib/x86_64-linux-gnu -lgthread-2.0 -lrt -lglib-2.0      -L/usr/lib/x86_64-linux-gnu -lXi   -L/usr/lib/x86_64-linux-gnu -lX11   -lgsm  
libtool: link: g++ -g -O2 -o .libs/mangler mangler.o channeltree.o mangleraudio.o manglerbackend.o manglerpulse.o mangleralsa.o mangleross.o manglernetwork.o manglerserverlist.o manglersettings.o manglerconfig.o manglerchat.o manglerprivchat.o manglercharset.o manglerintegration.o mangleradmin.o manglerrecorder.o manglerosd.o manglerg15.o inilib.o -pthread -pthread  ../libventrilo3/.libs/libventrilo3.so -L/usr/lib/x86_64-linux-gnu /usr/lib/libgtkmm-2.4.so -latkmm-1.6 /usr/lib/libgdkmm-2.4.so /usr/lib/libgiomm-2.4.so /usr/lib/libpangomm-1.4.so /usr/lib/libgtk-x11-2.0.so /usr/lib/libglibmm-2.4.so /usr/lib/libcairomm-1.0.so /usr/lib/libsigc-2.0.so /usr/lib/libgdk-x11-2.0.so /usr/lib/x86_64-linux-gnu/libatk-1.0.so /usr/lib/x86_64-linux-gnu/libgio-2.0.so /usr/lib/x86_64-linux-gnu/libpangoft2-1.0.so /usr/lib/x86_64-linux-gnu/libpangocairo-1.0.so -lgdk_pixbuf-2.0 -lm /usr/lib/libcairo.so /usr/lib/x86_64-linux-gnu/libpango-1.0.so /usr/lib/x86_64-linux-gnu/libfreetype.so -lfontconfig /usr/lib/x86_64-linux-gnu/libgobject-2.0.so /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so /usr/lib/x86_64-linux-gnu/libgthread-2.0.so -lrt /usr/lib/x86_64-linux-gnu/libglib-2.0.so -lXi -lX11 -lgsm -pthread
make[2]: Entering directory `/home/alex/mangler-1.2.2/src'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /bin/bash ../libtool   --mode=install /usr/bin/install -c mangler '/usr/local/bin'
libtool: install: /usr/bin/install -c .libs/mangler /usr/local/bin/mangler
test -z "/usr/local/share/applications" || /bin/mkdir -p "/usr/local/share/applications"
 /usr/bin/install -c -m 644 ../mangler.desktop '/usr/local/share/applications'
test -z "/usr/local/share/pixmaps" || /bin/mkdir -p "/usr/local/share/pixmaps"
 /usr/bin/install -c -m 644 ../icons/mangler_logo.svg '/usr/local/share/pixmaps'
make[2]: Leaving directory `/home/alex/mangler-1.2.2/src'
make[1]: Leaving directory `/home/alex/mangler-1.2.2/src'
make[1]: Entering directory `/home/alex/mangler-1.2.2'
make[2]: Entering directory `/home/alex/mangler-1.2.2'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/alex/mangler-1.2.2'
make[1]: Leaving directory `/home/alex/mangler-1.2.2'

``` 

The last 8 lines being where the important stuff is. I have checked, and the program does NOT run. I have already checked the allmighty Google, to no avail. Please help!

---

### Post by Candlehawk on 2011-07-09
*cough* bumped from the 9th page *cough*

---

### Post by Perfect Storm on 2011-07-10
Moved to Other OS/Distro Talk.

---

