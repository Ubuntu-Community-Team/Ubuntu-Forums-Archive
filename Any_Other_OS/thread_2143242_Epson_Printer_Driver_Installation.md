---
title: "Epson Printer Driver Installation"
date: 2013-05-08
forum: Any Other OS
---

### Post by iandusud on 2013-05-08
Hi folks, I'm new to Linux (Mint 14 nadia) and I'm loving it. However I'm having all sorts of problems trying to install the Linux printer drivers for my Epson DX4400 (I've already installed the printer via Cups using the Gutenprint drivers but the printing is very slow). So far I've managed to get the the 'Configure' command to work, but when I run 'Make' I get an error message. Here's what i get:

ian@ian-Aspire-5738 ~/pips-common-3.0 $ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking for bison... no
checking for byacc... no
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking for a sed that does not truncate output... /bin/sed
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
checking whether to build static libraries... yes
checking whether -lc should be explicitly linked in... no
creating libtool
checking for pkg-config... /usr/bin/pkg-config
checking for gtk+-2.0... yes
checking GTK_CFLAGS... -pthread -I/usr/include/gtk-2.0 -I/usr/lib/i386-linux-gnu/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/i386-linux-gnu/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12  
checking GTK_LIBS... -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgio-2.0 -lpangoft2-1.0 -lpangocairo-1.0 -lgdk_pixbuf-2.0 -lcairo -lpango-1.0 -lfreetype -lfontconfig -lgobject-2.0 -lglib-2.0  
checking for xml2-config... yes
checking for cups-config... yes
checking for pthread_create in -lpthread... yes
checking for working alloca.h... yes
checking for alloca... yes
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking for ANSI C header files... (cached) yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking argz.h usability... yes
checking argz.h presence... yes
checking for argz.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking for inttypes.h... (cached) yes
checking langinfo.h usability... yes
checking langinfo.h presence... yes
checking for langinfo.h... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking for memory.h... (cached) yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking stddef.h usability... yes
checking stddef.h presence... yes
checking for stddef.h... yes
checking for stdint.h... (cached) yes
checking stdio_ext.h usability... yes
checking stdio_ext.h presence... yes
checking for stdio_ext.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for strings.h... (cached) yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for unistd.h... (cached) yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for pid_t... yes
checking for size_t... yes
checking whether time.h and sys/time.h may both be included... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for working volatile... yes
checking whether closedir returns void... no
checking for error_at_line... yes
checking for unistd.h... (cached) yes
checking vfork.h usability... no
checking vfork.h presence... no
checking for vfork.h... no
checking for fork... yes
checking for vfork... yes
checking for working fork... yes
checking for working vfork... (cached) yes
checking whether gcc needs -traditional... no
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking for working memcmp... yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for getpagesize... yes
checking for working mmap... yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible realloc... yes
checking sys/select.h usability... yes
checking sys/select.h presence... yes
checking for sys/select.h... yes
checking for sys/socket.h... (cached) yes
checking types of arguments for select... int,fd_set *,struct timeval *
checking return type of signal handlers... void
checking for working strtod... yes
checking for vprintf... yes
checking for _doprnt... no
checking for __argz_count... yes
checking for __argz_next... yes
checking for __argz_stringify... yes
checking for alarm... yes
checking for floor... no
checking for getcwd... yes
checking for gettimeofday... yes
checking for memmove... yes
checking for mempcpy... yes
checking for memset... yes
checking for mkfifo... yes
checking for munmap... yes
checking for nl_langinfo... yes
checking for select... yes
checking for setlocale... yes
checking for socket... yes
checking for stpcpy... yes
checking for strcasecmp... yes
checking for strchr... yes
checking for strcspn... yes
checking for strdup... yes
checking for strerror... yes
checking for strrchr... yes
checking for strstr... yes
checking for strtol... yes
checking for strtoul... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for ranlib... (cached) ranlib
checking for strerror in -lcposix... no
checking for off_t... yes
checking whether we are using the GNU C Library 2.1 or newer... yes
checking whether integer division by zero raises SIGFPE... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unsigned long long... yes
checking for inttypes.h... yes
checking whether the inttypes.h PRIxNN macros are broken... no
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for argz.h... (cached) yes
checking for limits.h... (cached) yes
checking for locale.h... (cached) yes
checking nl_types.h usability... yes
checking nl_types.h presence... yes
checking for nl_types.h... yes
checking for malloc.h... (cached) yes
checking for stddef.h... (cached) yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking for sys/param.h... (cached) yes
checking for feof_unlocked... yes
checking for fgets_unlocked... yes
checking for getc_unlocked... yes
checking for getcwd... (cached) yes
checking for getegid... yes
checking for geteuid... yes
checking for getgid... yes
checking for getuid... yes
checking for mempcpy... (cached) yes
checking for munmap... (cached) yes
checking for putenv... yes
checking for setenv... yes
checking for setlocale... (cached) yes
checking for stpcpy... (cached) yes
checking for strcasecmp... (cached) yes
checking for strdup... (cached) yes
checking for strtoul... (cached) yes
checking for tsearch... yes
checking for __argz_count... (cached) yes
checking for __argz_stringify... (cached) yes
checking for __argz_next... (cached) yes
checking for iconv... yes
checking for iconv declaration... 
         extern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);
checking for nl_langinfo and CODESET... yes
checking for LC_MESSAGES... yes
checking for bison... no
checking whether NLS is requested... yes
checking whether included gettext is requested... no
checking for GNU gettext in libc... yes
configure: creating ./config.status
config.status: creating m4/Makefile
config.status: creating intl/Makefile
config.status: creating Makefile
config.status: creating Core/Makefile
config.status: creating Core/ekpd/Makefile
config.status: creating Core/libcap/Makefile
config.status: creating Core/libutils/Makefile
config.status: creating Core/pips-filter/Makefile
config.status: creating Core/rsc/Makefile
config.status: creating Core/script/Makefile
config.status: creating Gui/Makefile
config.status: creating Gui/ekpd-tool/Makefile
config.status: creating Gui/ekpnavi/Makefile
config.status: creating Gui/ekpstm/Makefile
config.status: creating Gui/pips-tool/Makefile
config.status: creating Gui/script/Makefile
config.status: creating pixmaps/Makefile
config.status: creating po/Makefile.in
config.status: creating Spooler/Makefile
config.status: creating Spooler/cups/Makefile
config.status: creating Spooler/cups/pips-wrapper/Makefile
config.status: creating Spooler/cups/ekplp/Makefile
config.status: creating Spooler/cups/script/Makefile
config.status: creating Spooler/lpr/Makefile
config.status: creating Spooler/lpr/script/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing default-1 commands
config.status: creating po/POTFILES
config.status: creating po/Makefile
configure: configuring in libltdl
configure: running /bin/bash './configure' --prefix=/usr/local  --enable-ltdl-convenience --cache-file=/dev/null --srcdir=.
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for an ANSI C-conforming const... yes
checking for inline... inline
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
checking how to run the C preprocessor... gcc -E
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
checking whether to build static libraries... yes
checking whether -lc should be explicitly linked in... no
creating libtool
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking whether gcc supports assert without backlinking... 
checking which extension is used for shared libraries... .so
checking which variable specifies run-time library path... LD_LIBRARY_PATH
checking for the default library search path... /lib /usr/lib
checking for objdir... .libs
checking whether libtool supports -dlopen/-dlpreopen... yes
checking for shl_load... no
checking for shl_load in -ldld... no
checking for dlopen in -ldl... yes
checking for dlerror... yes
checking for _ prefix in compiled symbols... no
checking whether deplibs are loaded by dlopen... yes
checking argz.h usability... yes
checking argz.h presence... yes
checking for argz.h... yes
checking for error_t... yes
checking for argz_append... yes
checking for argz_create_sep... yes
checking for argz_insert... yes
checking for argz_next... yes
checking for argz_stringify... yes
checking errno.h usability... yes
checking errno.h presence... yes
checking for errno.h... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking for memory.h... (cached) yes
checking for stdlib.h... (cached) yes
checking stdio.h usability... yes
checking stdio.h presence... yes
checking for stdio.h... yes
checking ctype.h usability... yes
checking ctype.h presence... yes
checking for ctype.h... yes
checking for unistd.h... (cached) yes
checking dl.h usability... no
checking dl.h presence... no
checking for dl.h... no
checking sys/dl.h usability... no
checking sys/dl.h presence... no
checking for sys/dl.h... no
checking dld.h usability... no
checking dld.h presence... no
checking for dld.h... no
checking for string.h... (cached) yes
checking for strchr... yes
checking for strrchr... yes
checking for memcpy... yes
checking for memmove... yes
checking for strcmp... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
ian@ian-Aspire-5738 ~/pips-common-3.0 $ make
cd . && /bin/bash ./config.status config.h
config.status: creating config.h
config.status: config.h is unchanged
make  all-recursive
make[1]: Entering directory `/home/ian/pips-common-3.0'
Making all in m4
make[2]: Entering directory `/home/ian/pips-common-3.0/m4'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/ian/pips-common-3.0/m4'
Making all in intl
make[2]: Entering directory `/home/ian/pips-common-3.0/intl'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/ian/pips-common-3.0/intl'
Making all in libltdl
make[2]: Entering directory `/home/ian/pips-common-3.0/libltdl'
cd . \
      && CONFIG_FILES= CONFIG_HEADERS=config.h:config-h.in \
         /bin/bash ./config.status
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
/bin/bash ./libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -c ltdl.c
rm -f .libs/ltdl.lo
gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -c ltdl.c  -fPIC -DPIC -o .libs/ltdl.lo
gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -c ltdl.c -o ltdl.o >/dev/null 2>&1
mv -f .libs/ltdl.lo ltdl.lo
/bin/bash ./libtool --mode=link gcc  -g -O2  -o libltdlc.la   ltdl.lo -ldl 
rm -fr .libs/libltdlc.la .libs/libltdlc.* .libs/libltdlc.*
ar cru .libs/libltdlc.al ltdl.lo
ranlib .libs/libltdlc.al
creating libltdlc.la
(cd .libs && rm -f libltdlc.la && ln -s ../libltdlc.la libltdlc.la)
make[2]: Leaving directory `/home/ian/pips-common-3.0/libltdl'
Making all in Core
make[2]: Entering directory `/home/ian/pips-common-3.0/Core'
Making all in ekpd
make[3]: Entering directory `/home/ian/pips-common-3.0/Core/ekpd'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/ian/pips-common-3.0/Core/ekpd'
Making all in libcap
make[3]: Entering directory `/home/ian/pips-common-3.0/Core/libcap'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/ian/pips-common-3.0/Core/libcap'
Making all in libutils
make[3]: Entering directory `/home/ian/pips-common-3.0/Core/libutils'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/ian/pips-common-3.0/Core/libutils'
Making all in pips-filter
make[3]: Entering directory `/home/ian/pips-common-3.0/Core/pips-filter'
/bin/bash ../../libtool --mode=link gcc -DLOCALE_PATH=\"/usr/local/share/locale\" -D_LPR_DIRECT -g -O2 -Wall   -o pips-filter  debug.o pfatt.o pfimg.o pfpng.o pips-filter.o pngfilter.o rawfilter.o -lstdc++ ../../libltdl/libltdlc.la -L/usr/lib -lxml2 ../../Core/libutils/libpips-utils.la -lpthread 
gcc -DLOCALE_PATH=\"/usr/local/share/locale\" -D_LPR_DIRECT -g -O2 -Wall -o .libs/pips-filter debug.o pfatt.o pfimg.o pfpng.o pips-filter.o pngfilter.o rawfilter.o  -lstdc++ ../../libltdl/.libs/libltdlc.al -L/usr/lib -lxml2 ../../Core/libutils/.libs/libpips-utils.so -ldl -lpthread -Wl,--rpath -Wl,/usr/local/lib
pfimg.o: In function `set_raster':
/home/ian/pips-common-3.0/Core/pips-filter/pfimg.c:1249: undefined reference to `floor'
pfimg.o: In function `load_image_out':
/home/ian/pips-common-3.0/Core/pips-filter/pfimg.c:177: undefined reference to `floor'
../../Core/libutils/.libs/libpips-utils.so: undefined reference to `xmlFreeDoc'
../../Core/libutils/.libs/libpips-utils.so: undefined reference to `xmlGetProp'
../../Core/libutils/.libs/libpips-utils.so: undefined reference to `xmlStrcmp'
../../Core/libutils/.libs/libpips-utils.so: undefined reference to `xmlNodeListGetString'
../../Core/libutils/.libs/libpips-utils.so: undefined reference to `xmlParseFile'
../../Core/libutils/.libs/libpips-utils.so: undefined reference to `xmlFree'
../../Core/libutils/.libs/libpips-utils.so: undefined reference to `xmlDocGetRootElement'
collect2: error: ld returned 1 exit status
make[3]: *** [pips-filter] Error 1
make[3]: Leaving directory `/home/ian/pips-common-3.0/Core/pips-filter'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/ian/pips-common-3.0/Core'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ian/pips-common-3.0'
make: *** [all] Error 2
ian@ian-Aspire-5738 ~/pips-common-3.0 $ 

Can anyone tell me what I need to do to go on from here please.

Thanks, Ian

---

### Post by Perfect Storm on 2013-05-08
Moved to Other OS/Distro Support.

---

