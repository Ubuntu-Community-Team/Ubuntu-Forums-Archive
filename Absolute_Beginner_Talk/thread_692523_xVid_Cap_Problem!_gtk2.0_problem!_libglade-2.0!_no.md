---
title: "xVid Cap Problem! gtk2.0 problem! libglade-2.0! not found!"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by karlo on 2008-02-09
Here is the complete message of the terminal...

```
karlo@karlo-laptop:~/Downloads$ cd xvidcap-1.1.6
karlo@karlo-laptop:~/Downloads/xvidcap-1.1.6$ ls
aclocal.m4    depcomp              net.jarre_de_the.Xvidcap.service.in
AUTHORS       doc                  NEWS
autogen.sh    ffmpeg               po
ChangeLog     INSTALL              ppm2mpeg.sh
config.guess  install-sh           reacocard.asc
config.h.in   intltool-extract.in  README
config.log    intltool-merge.in    src
config.sub    intltool-update.in   TODO.tasks
configure     Makefile.am          xvidcap.desktop
configure.in  Makefile.in          xvidcap.png
COPYING       missing
debian        mkinstalldirs
karlo@karlo-laptop:~/Downloads/xvidcap-1.1.6$ gedit INSTALL
karlo@karlo-laptop:~/Downloads/xvidcap-1.1.6$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
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
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking whether make sets $(MAKE)... (cached) yes
checking for ranlib... ranlib
checking for gawk... (cached) mawk
checking for a sed that does not truncate output... /bin/sed
checking for bc... /usr/bin/bc
checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for scrollkeeper-config... /usr/bin/scrollkeeper-config
checking for docbook2x-man... no
configure: Couldn't find docbook2x-man to generate current man pages. Will try db2x_docbook2man.
checking for db2x_docbook2man... no
configure: Couldn't find neither docbook2x-man nor db2x_docbook2man to generate current man pages. Will install pre-generated ones if present.
checking for xml2po... /usr/bin/xml2po
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
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
checking for msgfmt... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for PACKAGE... configure: error: Package requirements (gtk+-2.0 >= 2.4.0 libglade-2.0 glib-2.0 gthread-2.0) were not met:

No package 'libglade-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PACKAGE_CFLAGS
and PACKAGE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

karlo@karlo-laptop:~/Downloads/xvidcap-1.1.6$ apt-get install libglade-2.0
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
karlo@karlo-laptop:~/Downloads/xvidcap-1.1.6$ sudo apt-get install libglade-2.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libglade-2.0
karlo@karlo-laptop:~/Downloads/xvidcap-1.1.6$ cd ..
karlo@karlo-laptop:~/Downloads$ cd libglade-2.0.1
karlo@karlo-laptop:~/Downloads/libglade-2.0.1$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets ${MAKE}... yes
checking if debuging support was requested... yes
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for strerror in -lcposix... no
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependant libraries... pass_all
checking command to parse /usr/bin/nm -B output... ok
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
checking whether to build static libraries... yes
checking whether -lc should be explicitly linked in... no
creating libtool
checking for pkg-config... /usr/bin/pkg-config
checking for GTK+ - version >= 2.0.0... yes (version 2.12.0)
checking for gtk_plug_get_type... yes
checking for pkg-config... (cached) /usr/bin/pkg-config
checking for libxml-2.0 >= 2.4.10 atk >= 1.0.0 gtk+-2.0 >= 2.0.0... Package libxml-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `libxml-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'libxml-2.0' found
configure: error: Library requirements (libxml-2.0 >= 2.4.10 atk >= 1.0.0 gtk+-2.0 >= 2.0.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
```

what to do? I didn't know installing a package is this difficult!:mad:

**UPDATE** --- searched for some solutions on google, and applied it, here is it, but still no luck!

```
karlo@karlo-laptop:~/Downloads/libglade-2.0.1$ sudo apt-get install libxml-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  ndiswrapper-common libgtk1.2 libglib1.2 libboost-thread1.34.1
  libboost-date-time1.34.1 libmikmod2 libgtk1.2-common ndiswrapper-utils-1.9
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libxml1
The following NEW packages will be installed:
  libxml-dev libxml1
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 578kB of archives.
After unpacking 2327kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ph.archive.ubuntu.com gutsy/universe libxml1 1:1.8.17-14build1 [216kB]
Get:2 http://ph.archive.ubuntu.com gutsy/universe libxml-dev 1:1.8.17-14build1 [362kB]
Fetched 578kB in 17s (33.0kB/s)                                                
Selecting previously deselected package libxml1.
(Reading database ... 127738 files and directories currently installed.)
Unpacking libxml1 (from .../libxml1_1%3a1.8.17-14build1_i386.deb) ...
Selecting previously deselected package libxml-dev.
Unpacking libxml-dev (from .../libxml-dev_1%3a1.8.17-14build1_i386.deb) ...
Setting up libxml1 (1:1.8.17-14build1) ...

Setting up libxml-dev (1:1.8.17-14build1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
karlo@karlo-laptop:~/Downloads/libglade-2.0.1$ sudo apt-get install gtk2.0-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gtk2.0-dev
karlo@karlo-laptop:~/Downloads/libglade-2.0.1$ sudo apt-get install libgtk2.0-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgtk2.0-dev is already the newest version.
The following packages were automatically installed and are no longer required:
  ndiswrapper-common libgtk1.2 libglib1.2 libboost-thread1.34.1
  libboost-date-time1.34.1 libmikmod2 libgtk1.2-common ndiswrapper-utils-1.9
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
karlo@karlo-laptop:~/Downloads/libglade-2.0.1$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets ${MAKE}... yes
checking if debuging support was requested... yes
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for strerror in -lcposix... no
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependant libraries... pass_all
checking command to parse /usr/bin/nm -B output... ok
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
checking whether to build static libraries... yes
checking whether -lc should be explicitly linked in... no
creating libtool
checking for pkg-config... /usr/bin/pkg-config
checking for GTK+ - version >= 2.0.0... yes (version 2.12.0)
checking for gtk_plug_get_type... yes
checking for pkg-config... (cached) /usr/bin/pkg-config
checking for libxml-2.0 >= 2.4.10 atk >= 1.0.0 gtk+-2.0 >= 2.0.0... Package libxml-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `libxml-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'libxml-2.0' found
configure: error: Library requirements (libxml-2.0 >= 2.4.10 atk >= 1.0.0 gtk+-2.0 >= 2.0.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
karlo@karlo-laptop:~/Downloads/libglade-2.0.1$ sudo apt-get install libxml-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libxml-dev is already the newest version.
The following packages were automatically installed and are no longer required:
  ndiswrapper-common libgtk1.2 libglib1.2 libboost-thread1.34.1
  libboost-date-time1.34.1 libmikmod2 libgtk1.2-common ndiswrapper-utils-1.9
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
karlo@karlo-laptop:~/Downloads/libglade-2.0.1$ 
```

---

### Post by mevets on 2008-02-09
You are installing that program from source. I assume you are doing this because it is not in the repos. But if it is, why not install the binaries?

To solve your configure error you need to run
> 
sudo apt-get install libglade2-0 libglade2-dev

You may need one of those packages or both, i dont know, but having both wont hurt. After you install those two, try to run configure again. Be aware it might say you dont have something else.

---

### Post by asmoore82 on 2008-02-09
a debian package which can be installed on Ubuntu for xvidcap
is available on their sourceforge project download page:

[http://sourceforge.net/project/showfiles.php?group_id=81535&package_id=83441&release_id=567877](http://sourceforge.net/project/showfiles.php?group_id=81535&package_id=83441&release_id=567877)
filename: xvidcap_1.1.7rc1_i386.deb

EDIT: just tested it out for the fun of it; it Works!

---

### Post by karlo on 2008-02-11
> **asmoore82 said:**
> a debian package which can be installed on Ubuntu for xvidcap
is available on their sourceforge project download page:

[http://sourceforge.net/project/showfiles.php?group_id=81535&package_id=83441&release_id=567877](http://sourceforge.net/project/showfiles.php?group_id=81535&package_id=83441&release_id=567877)
filename: xvidcap_1.1.7rc1_i386.deb

EDIT: just testid it out for the fun of it; it Works!

**I wanted to compile it my self so that it will be optimized on my i686 pentium M laptop...**

---

