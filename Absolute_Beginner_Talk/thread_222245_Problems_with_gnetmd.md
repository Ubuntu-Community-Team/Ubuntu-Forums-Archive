---
title: "Problems with gnetmd"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by ignorance on 2006-07-24
i can't get it to do a make or make install
bash: make: command not found

the excecuted code
```
christophe@winkill:~/Desktop/gnetmd-0.6.1$ ./configure
checking whether to enable maintainer-specific portions of Makefiles... no
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... none
checking dependency style of gcc... none
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking for a sed that does not truncate output... /bin/sed
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking command to parse /usr/bin/nm -B output... ok
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for ranlib... ranlib
checking for strip... strip
checking for objdir... .libs
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.lo... yes
checking if gcc supports -fno-rtti -fno-exceptions... yes
checking whether the linker (/usr/bin/ld) supports shared libraries... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking whether -lc should be explicitly linked in... no
creating libtool
checking for ANSI C header files... (cached) yes
checking for a BSD-compatible install... /usr/bin/install -c
checking for gob2... gob2
checking usb.h usability... yes
checking usb.h presence... yes
checking for usb.h... yes
checking for usb_control_msg in -lusb... yes
checking for libusb-config... libusb-config
checking for pkg-config... /usr/bin/pkg-config
checking for "glib-2.0"... yes
checking GLIB_CFLAGS... -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include
checking GLIB_LIBS... -lglib-2.0
checking for "libgnomeui-2.0"... yes
checking GNOMEUI_CFLAGS... -DORBIT2=1 -pthread -I/usr/include/libgnomeui-2.0 -I/usr/include/libgnome-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/gtk-2.0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/libbonoboui-2.0 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/gnome-keyring-1 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/orbit-2.0 -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/libxml2
checking GNOMEUI_LIBS... -pthread -lgnomeui-2 -lSM -lICE -lbonoboui-2 -lgnome-keyring -lxml2 -lz -lgnomecanvas-2 -lgnome-2 -lpopt -lart_lgpl_2 -lpangoft2-1.0 -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgnomevfs-2 -lbonobo-2 -lgconf-2 -lgobject-2.0 -lbonobo-activation -lORBit-2 -lm -lgmodule-2.0 -ldl -lgthread-2.0 -lglib-2.0
checking for "gnome-vfs-module-2.0 libnautilus"... checking for xmms-config... no
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for catalogs to be installed...  en_AU
checking for perl... /usr/bin/perl
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating po/Makefile.in
config.status: creating po/Makefile
config.status: creating src/gui/Makefile
config.status: creating src/xmms/Makefile
config.status: creating src/vfs/Makefile
config.status: creating src/nv/Makefile
config.status: creating src/config.h
config.status: src/config.h is unchanged
config.status: executing depfiles commands
config.status: executing default-1 commands
config.status: executing default-2 commands

  +--------------------------------------------------------------------------+
  | Summary                                                                  |
  +--------------------------------------------------------------------------+
  |                                                                          |
  | libglib:      Yes.                                                       |
  |                                                                          |
  | libusb:       Yes.                                                       |
  |                                                                          |
  | libgnomeui:   Yes.                                                       |
  |                                                                          |
  | libnautilus:  No.  This library is only required if you want to use      |
  |                    the nautilus view and/or the gnome-vfs module.        |
  |                    To compile programs with libnautilus, you will        |
  |                    need the headers too.  These will likely be in a      |
  |                    -dev or -devel package in your distro.                |
  |                                                                          |
  | gob2:         Yes.                                                       |
  |                                                                          |
  | libxmms:      No.  This is only required by the xmms plugin.  To compile |
  |                    programs with libxmms, you will need the headers too. |
  |                    These will likely be in a -dev or -devel package in   |
  |                    your distro.                                          |
  |                                                                          |
  +--------------------------------------------------------------------------+
  |                                                                          |
  | libgnetmd0:                         Will be compiled.                    |
  |                                                                          |
  | nautilus view & vfs module:         Will NOT be compiled.                |
  |                                                                          |
  | xmms plugin:                        Will NOT be compiled.                |
  |                                                                          |
  | standalone gui:                     Will be compiled.                    |
  |                                                                          |
  | command-line tools:                 Don't exist (yet).                   |
  |                                                                          |
  +--------------------------------------------------------------------------+ 
```
anyone got a solution?

---

### Post by ignorance on 2006-07-27
still not figured it out

---

### Post by hilde on 2006-11-20
Do you have 'make' installed?

---

