---
title: "avant window navigator install problem"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by kelinu on 2008-04-01
Ok, so i've installed all the dependencies for awn, but now when I type in ./configure this is what comes:

> checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
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
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 98304
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for python... /usr/bin/python
checking for a version of Python >= 2.1.0... yes
checking for a version of Python >= 2.3.5... yes
checking for the distutils Python package... yes
checking for Python include path... -I/usr/include/python2.5
checking for Python library path... -L/usr/lib/python2.5 -lpython2.5
checking for Python site-packages path... ${exec_prefix}/lib/python2.5/site-packages
checking python extra libraries...  -lpthread -ldl  -lutil
checking python extra linking flags... -Xlinker -export-dynamic
checking consistency of all components of python development environment... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for PYGTK... yes
checking for pygtk-codegen-2.0... /usr/bin/pygtk-codegen-2.0
checking for pygtk defs... /usr/share/pygtk/2.0/defs
checking for PYCAIRO... yes
checking for valac... no
checking valac is at least version 0.1.6... ./configure: line 21334: : command not found
yes
checking for vapigen... vapigen
checking for python module xdg... yes
checking for intltool >= 0.34... 0.36.2 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for catalogs to be installed...  af ar bn bg ca cs da de de_DE el en_AU en_CA en_GB es et eu fa fi fi_FI fr fr_FR ga gl gu he hi hr hu id it it_IT ja ka ko lt mr ms nb nl nn no_NO pl pt_BR pt ro ru ru_RU sk sl sq sr sv ta te th tr uk vi zh_CN zh_HK zh_TW
checking for pkg-config... (cached) /usr/bin/pkg-config
checking pkg-config is at least version 0.7... yes
checking for GLIB - version >= 2.8.0... yes (version 2.14.1)
checking for glib-genmarshal... /usr/bin/glib-genmarshal
checking for specific desktop support... Gnome
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for config backend support... checking for gconftool-2... /usr/bin/gconftool-2
GConf
checking for AWN... yes
checking for DOCK... yes
checking for sin in -lm... yes
Using config source xml:merged:/etc/gconf/gconf.xml.defaults for schema installation
Using $(sysconfdir)/gconf/schemas as install directory for schema files
configure: creating ./config.status
config.status: creating Makefile
config.status: creating awn-manager/Makefile
config.status: creating awn-manager/awn-launcher-editor
config.status: creating awn-manager/awn-manager.desktop.in
config.status: creating awn-manager/awnDefs.py
config.status: creating awn-manager/awnManager.py
config.status: creating bindings/Makefile
config.status: creating bindings/python/Makefile
config.status: creating bindings/vala/Makefile
config.status: creating doc/Makefile
config.status: creating doc/reference/Makefile
config.status: creating libawn/Makefile
config.status: creating libawn/egg/Makefile
config.status: creating src/Makefile
config.status: creating awn-applet-activation/Makefile
config.status: creating applets/Makefile
config.status: creating data/Makefile
config.status: creating data/active/Makefile
config.status: creating data/avant-window-navigator.desktop.in
config.status: creating po/Makefile.in
config.status: creating awn.pc
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing intltool commands
config.status: executing default-1 commands
config.status: executing po/stamp-it commands

             Avant Window Navigator 0.2.6
             ============================

                   prefix:   /usr/local

                  Desktop:   gnome
    Configuration Backend:   GConf
              VFS Backend:   gnome-vfs-module-2.0

             Vala Support:   yes

            Documentation:   no



And then make:

> make  all-recursive
make[1]: Entering directory `/home/michael/Desktop/avant-window-navigator-0.2.6'
Making all in libawn
make[2]: Entering directory `/home/michael/Desktop/avant-window-navigator-0.2.6/libawn'
make[2]: Circular stamp-awn-enum-types.h <- awn-enum-types.h dependency dropped.
( cd . && \
          `pkg-config --variable=glib_mkenums glib-2.0` \
                --template ./awn-enum-types.h.in \
          awn-defines.h awn-applet.h awn-applet-dialog.h awn-applet-simple.h awn-cairo-utils.h awn-config-client.h awn-desktop-item.h awn-effects.h awn-enum-types.h awn-plug.h awn-settings.h awn-title.h awn-vfs.h  ) >> xgen-ceth && \
        (cmp xgen-ceth awn-enum-types.h || cp xgen-ceth awn-enum-types.h) && \
        rm -f xgen-ceth && \
        echo timestamp > stamp-awn-enum-types.h
make  all-recursive
make[3]: Entering directory `/home/michael/Desktop/avant-window-navigator-0.2.6/libawn'
Making all in egg
make[4]: Entering directory `/home/michael/Desktop/avant-window-navigator-0.2.6/libawn/egg'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/michael/Desktop/avant-window-navigator-0.2.6/libawn/egg'
make[4]: Entering directory `/home/michael/Desktop/avant-window-navigator-0.2.6/libawn'
make[4]: Circular stamp-awn-enum-types.h <- awn-enum-types.h dependency dropped.
make[4]: Leaving directory `/home/michael/Desktop/avant-window-navigator-0.2.6/libawn'
make[3]: Leaving directory `/home/michael/Desktop/avant-window-navigator-0.2.6/libawn'
make[2]: Leaving directory `/home/michael/Desktop/avant-window-navigator-0.2.6/libawn'
Making all in src
make[2]: Entering directory `/home/michael/Desktop/avant-window-navigator-0.2.6/src'
/bin/bash ../libtool --mode=execute /usr/bin/dbus-binding-tool --prefix=awn_task_manager --mode=glib-server --output=awn-dbus-glue.h awn-dbus.xml
/bin/bash ../libtool --mode=execute /usr/bin/dbus-binding-tool --prefix=awn_applet_manager --mode=glib-server --output=awn-applet-manager-glue.h awn-applet-manager-dbus.xml
make  all-am
make[3]: Entering directory `/home/michael/Desktop/avant-window-navigator-0.2.6/src'
gcc -DHAVE_CONFIG_H -I. -I.. -pthread -DORBIT2=1 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/include/gnome-desktop-2.0 -I/usr/include/libgnomeui-2.0 -I/usr/include/startup-notification-1.0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-keyring-1 -I/usr/include/libgnome-2.0 -I/usr/include/libbonoboui-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/orbit-2.0 -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/libxml2 -I/usr/include/gail-1.0 -I/usr/include/gnome-vfs-module-2.0   -I/usr/include/libwnck-1.0 -I/usr/include/gtk-2.0 -I/usr/include/startup-notification-1.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -DLIBDIR=\""/usr/local/lib"\" -I../libawn   -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -D_GNU_SOURCE   -g -O2 -Wall -fno-strict-aliasing -fmessage-length=0 -D_FORTIFY_SOURCE=2 -MT awn-applet-manager.o -MD -MP -MF .deps/awn-applet-manager.Tpo -c -o awn-applet-manager.o awn-applet-manager.c
mv -f .deps/awn-applet-manager.Tpo .deps/awn-applet-manager.Po
gcc -DHAVE_CONFIG_H -I. -I.. -pthread -DORBIT2=1 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/include/gnome-desktop-2.0 -I/usr/include/libgnomeui-2.0 -I/usr/include/startup-notification-1.0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-keyring-1 -I/usr/include/libgnome-2.0 -I/usr/include/libbonoboui-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/orbit-2.0 -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/libxml2 -I/usr/include/gail-1.0 -I/usr/include/gnome-vfs-module-2.0   -I/usr/include/libwnck-1.0 -I/usr/include/gtk-2.0 -I/usr/include/startup-notification-1.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -DLIBDIR=\""/usr/local/lib"\" -I../libawn   -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -D_GNU_SOURCE   -g -O2 -Wall -fno-strict-aliasing -fmessage-length=0 -D_FORTIFY_SOURCE=2 -MT awn-task-manager.o -MD -MP -MF .deps/awn-task-manager.Tpo -c -o awn-task-manager.o awn-task-manager.c
mv -f .deps/awn-task-manager.Tpo .deps/awn-task-manager.Po
/bin/bash ../libtool --tag=CC   --mode=link gcc  -g -O2 -Wall -fno-strict-aliasing -fmessage-length=0 -D_FORTIFY_SOURCE=2   -o avant-window-navigator main.o awn-applet-manager.o awn-applet-proxy.o awn-bar.o awn-hotspot.o awn-marshallers.o awn-task.o awn-task-manager.o awn-window.o awn-x.o awn-utils.o xutils.o  -lwnck-1 -lgtk-x11-2.0 -lstartup-notification-1 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXinerama -lXi -lXrandr -lXcursor -lXdamage -lpango-1.0 -lcairo -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0 -lXcomposite -lXfixes -lXrender -lX11   ../libawn/libawn.la  -lm 
gcc -g -O2 -Wall -fno-strict-aliasing -fmessage-length=0 -D_FORTIFY_SOURCE=2 -o .libs/avant-window-navigator main.o awn-applet-manager.o awn-applet-proxy.o awn-bar.o awn-hotspot.o awn-marshallers.o awn-task.o awn-task-manager.o awn-window.o awn-x.o awn-utils.o xutils.o  -lwnck-1 /usr/lib/libgtk-x11-2.0.so -lstartup-notification-1 /usr/lib/libgdk-x11-2.0.so /usr/lib/libatk-1.0.so /usr/lib/libgdk_pixbuf-2.0.so /usr/lib/libpangocairo-1.0.so -lfontconfig -lXext -lXinerama -lXi -lXrandr -lXcursor -lXdamage /usr/lib/libpango-1.0.so /usr/lib/libcairo.so /usr/lib/libgobject-2.0.so /usr/lib/libgmodule-2.0.so -ldl /usr/lib/libglib-2.0.so -lXcomposite -lXfixes -lXrender -lX11 ../libawn/.libs/libawn.so -lm 
creating avant-window-navigator
make[3]: Leaving directory `/home/michael/Desktop/avant-window-navigator-0.2.6/src'
make[2]: Leaving directory `/home/michael/Desktop/avant-window-navigator-0.2.6/src'
Making all in awn-applet-activation
make[2]: Entering directory `/home/michael/Desktop/avant-window-navigator-0.2.6/awn-applet-activation'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/michael/Desktop/avant-window-navigator-0.2.6/awn-applet-activation'
Making all in data
make[2]: Entering directory `/home/michael/Desktop/avant-window-navigator-0.2.6/data'
Making all in active
make[3]: Entering directory `/home/michael/Desktop/avant-window-navigator-0.2.6/data/active'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/michael/Desktop/avant-window-navigator-0.2.6/data/active'
make[3]: Entering directory `/home/michael/Desktop/avant-window-navigator-0.2.6/data'
LC_ALL=C ../intltool-merge -d -u -c ../po/.intltool-merge-cache ../po avant-window-navigator.desktop.in avant-window-navigator.desktop
Found cached translation database
Merging translations into avant-window-navigator.desktop.
make[3]: Leaving directory `/home/michael/Desktop/avant-window-navigator-0.2.6/data'
make[2]: Leaving directory `/home/michael/Desktop/avant-window-navigator-0.2.6/data'
Making all in applets
make[2]: Entering directory `/home/michael/Desktop/avant-window-navigator-0.2.6/applets'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/michael/Desktop/avant-window-navigator-0.2.6/applets'
Making all in po
make[2]: Entering directory `/home/michael/Desktop/avant-window-navigator-0.2.6/po'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/michael/Desktop/avant-window-navigator-0.2.6/po'
Making all in bindings
make[2]: Entering directory `/home/michael/Desktop/avant-window-navigator-0.2.6/bindings'
Making all in python
make[3]: Entering directory `/home/michael/Desktop/avant-window-navigator-0.2.6/bindings/python'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/michael/Desktop/avant-window-navigator-0.2.6/bindings/python'
make[3]: Entering directory `/home/michael/Desktop/avant-window-navigator-0.2.6/bindings'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/michael/Desktop/avant-window-navigator-0.2.6/bindings'
make[2]: Leaving directory `/home/michael/Desktop/avant-window-navigator-0.2.6/bindings'
Making all in awn-manager
make[2]: Entering directory `/home/michael/Desktop/avant-window-navigator-0.2.6/awn-manager'
LC_ALL=C ../intltool-merge -d -u -c ../po/.intltool-merge-cache ../po awn-manager.desktop.in awn-manager.desktop
Found cached translation database
Merging translations into awn-manager.desktop.
make[2]: Leaving directory `/home/michael/Desktop/avant-window-navigator-0.2.6/awn-manager'
Making all in doc
make[2]: Entering directory `/home/michael/Desktop/avant-window-navigator-0.2.6/doc'
Making all in reference
make[3]: Entering directory `/home/michael/Desktop/avant-window-navigator-0.2.6/doc/reference'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/michael/Desktop/avant-window-navigator-0.2.6/doc/reference'
make[3]: Entering directory `/home/michael/Desktop/avant-window-navigator-0.2.6/doc'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/michael/Desktop/avant-window-navigator-0.2.6/doc'
make[2]: Leaving directory `/home/michael/Desktop/avant-window-navigator-0.2.6/doc'
make[2]: Entering directory `/home/michael/Desktop/avant-window-navigator-0.2.6'
make[2]: Leaving directory `/home/michael/Desktop/avant-window-navigator-0.2.6'
make[1]: Leaving directory `/home/michael/Desktop/avant-window-navigator-0.2.6'


And then make install:

> Making install in libawn
make[1]: Entering directory `/home/michael/Desktop/avant-window-navigator-0.2.6/libawn'
make[1]: Circular stamp-awn-enum-types.h <- awn-enum-types.h dependency dropped.
make  install-recursive
make[2]: Entering directory `/home/michael/Desktop/avant-window-navigator-0.2.6/libawn'
Making install in egg
make[3]: Entering directory `/home/michael/Desktop/avant-window-navigator-0.2.6/libawn/egg'
make[4]: Entering directory `/home/michael/Desktop/avant-window-navigator-0.2.6/libawn/egg'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/home/michael/Desktop/avant-window-navigator-0.2.6/libawn/egg'
make[3]: Leaving directory `/home/michael/Desktop/avant-window-navigator-0.2.6/libawn/egg'
make[3]: Entering directory `/home/michael/Desktop/avant-window-navigator-0.2.6/libawn'
make[3]: Circular stamp-awn-enum-types.h <- awn-enum-types.h dependency dropped.
make[4]: Entering directory `/home/michael/Desktop/avant-window-navigator-0.2.6/libawn'
make[4]: Circular stamp-awn-enum-types.h <- awn-enum-types.h dependency dropped.
test -z "/usr/local/lib" || /bin/mkdir -p "/usr/local/lib"
 /bin/bash ../libtool --mode=install /usr/bin/install -c  'libawn.la' '/usr/local/lib/libawn.la'
/usr/bin/install -c .libs/libawn.so.0.0.1 /usr/local/lib/libawn.so.0.0.1
/usr/bin/install: cannot create regular file `/usr/local/lib/libawn.so.0.0.1': Permission denied
make[4]: *** [install-libLTLIBRARIES] Error 1
make[4]: Leaving directory `/home/michael/Desktop/avant-window-navigator-0.2.6/libawn'
make[3]: *** [install-am] Error 2
make[3]: Leaving directory `/home/michael/Desktop/avant-window-navigator-0.2.6/libawn'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/home/michael/Desktop/avant-window-navigator-0.2.6/libawn'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/michael/Desktop/avant-window-navigator-0.2.6/libawn'
make: *** [install-recursive] Error 1


And guess what?  It's not installed!  So what is the problem and how do I fix it?

Much appreciated,

Mike

---

### Post by kolisikepu on 2008-04-01
This was the best thread for me to get my AWN going.

[http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981)

Have you installed Compiz?  Have you enabled Visual Effects?

---

### Post by abhiroopb on 2008-04-01
I suggest using the repository version:

#avant window navigator
deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator

to add to the repository:

Open a terminal (Applications>Accessories>Terminal):

```

$ sudo gedit /etc/apt/sources.list

```

In the text box that enters add:

#avant window navigator
deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator

save, exit.

Again on the terminal:
```

$ sudo apt-get update
sudo apt-get upgrade
sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr

```
Thats it, and it should be located in: Applications->Accessories->Avant Window Navigator

---

### Post by kelinu on 2008-04-01
nope still didn't work...i think i did  sumtin wrong in the sources stuff...

---

### Post by kelinu on 2008-04-01
Oh yea, ok i installed avant but guess what...now its not even starting up when i click avant-windows-navigator under accessories

---

### Post by abhiroopb on 2008-04-02
are u using ompiz or metacity?

---

### Post by LowSky on 2008-04-02
you need to use compiz

---

### Post by moonbeam on 2008-04-02
> **LowSky said:**
> you need to use compiz

Compiz is not necessary:   A compositing manager is needed.  [http://wiki.awn-project.org/Installation#Installing_Avant_Window_Navigator](http://wiki.awn-project.org/Installation#Installing_Avant_Window_Navigator)   #3

Thanks,

---

### Post by abhiroopb on 2008-04-02
compiz is basically the most convinenient one as metacity does not have a stable one as yet

---

### Post by moonbeam on 2008-04-02
As an awn/awn-extras developer I would just like to take a moment to comment.

As a development team we strongly endorse the use of one of the following methods to install awn if you're on a Gnome oriented Ubuntu installation.

1)  Official Hardy repository.  If you only want the bar without the applets this tends to be a good choice.  It is also hoped that newer versions of awn may become available in backports upon the release of Hardy.

2)  The "official" awn-testing PPA:  [https://launchpad.net/~awn-testing/+archive](https://launchpad.net/~awn-testing/+archive).  This repo tends to "bleed" and tends to have the most complete applet inclusion (including vala applets).   Note the word "testing" :-)

3)  Reacocard's repository and guide:  [http://ubuntuforums.org/showthread.php?t=385981&highlight=avant+window+navigator](http://ubuntuforums.org/showthread.php?t=385981&highlight=avant+window+navigator)  Excellent guide, excellent support though not quite as many applets as (2).   That being said... the extra value added in terms of hands on/quality support has something to be said for it.  Reacocard and many other posters in this thread are Ubuntu users...  while that is less likely if you choose a random awn dev :-)

Some notes on binary packages in general can be found at:  [http://wiki.awn-project.org/DistributionGuides](http://wiki.awn-project.org/DistributionGuides)

In all honesty there is no need to build your own awn packages for Ubuntu (at least Hardy/Gutsy) unless you have a specific need/desire for either an agnostic or xfce4 specific installation - unless you know that's what you need then chances are you don't need it.

Just my suggestions to help ease the pain...

Thanks,

---

