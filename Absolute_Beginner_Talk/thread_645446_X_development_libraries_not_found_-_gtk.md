---
title: "X development libraries not found - gtk"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by xeb07170 on 2007-12-20
having problems trying to install gtk. I have just recently started using kubuntu/linux.

I need to install gtk to use a program called regviewer. I have installed all the dependencies.

I cant make sense of the error message - had a look around - no one seems to have an answer for it

anyone any idea?

checking for jpeglib.h... yes
checking for jpeg_simple_progression in -ljpeg... yes
checking for libpng12... yes
checking pixbuf loaders to build...
checking for sys/wait.h that is POSIX.1 compatible... yes
checking return type of signal handlers... (cached) void
checking for x86 platform... yes
checking compiler support for MMX... yes
checking for X... no
configure: error: X development libraries not found
root@paul-desktop:~/Desktop/gtk+-2.8.16#  







Thanks


Paul

---

### Post by nowshining on 2007-12-20
ahh ur trying to configure and install from source. :)

have u looked for a .deb file..


if not when u get an error like that even tho it says libs (libraries) u'll need the -dev (development) versions.

also if u have checkinstall u can build a backup .deb file if u'd like

do the following


sudo apt-get install build-essential checkinstall

hit enter

enter ur pw, don't worry ur password will not show as u type, just type it as u normally do and hit the enter key, when asked y/n press y on ur keyboard and the enter key to continue..


from there

and seeing ur in the src folder

./configure

make

sudo checkinstall -D make install

(follow the checkinstall directions and when ur done installing a new .deb file will be created in the same folder as the untared program that's still in source code is, itta be protected by root, but u can still copy it. but not move it as u'll get a permissions error popup..)

after that

issue

sudo make clean

and ur done.. :)


edit: i just noticed ur in root, then on sudo u can just leave them off...

---

### Post by xeb07170 on 2007-12-20
hi,

thanks for reply

may sound simple - but where have i to copy the .deb file?

---

### Post by xeb07170 on 2007-12-20
root@paul-desktop:~/Desktop/gtk+-2.8.16# apt-get install build-essential checkinstall
Reading package lists... Done
Building dependency tree
Reading state information... Done
build-essential is already the newest version.
The following NEW packages will be installed
  checkinstall
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 116kB of archives.
After unpacking 557kB of additional disk space will be used.
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/universe checkinstall 1.6.1-4ubuntu1 [116kB]
Fetched 116kB in 0s (281kB/s)
Selecting previously deselected package checkinstall.
(Reading database ... 95333 files and directories currently installed.)
Unpacking checkinstall (from .../checkinstall_1.6.1-4ubuntu1_i386.deb) ...
Setting up checkinstall (1.6.1-4ubuntu1) ...
root@paul-desktop:~/Desktop/gtk+-2.8.16# ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for native Win32... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
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
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc static flag  works... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
appending configuration tag "F77" to libtool
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for _LARGE_FILES value needed for large files... no
checking for nm... /usr/bin/nm -B
checking whether to enable maintainer-specific portions of Makefiles... no
checking for some Win32 platform... no
checking whether build environment is sane... yes
checking for strerror in -lcposix... no
checking for gcc option to accept ANSI C... none needed
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... (cached) yes
checking for pkg-config... /usr/local/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for BASE_DEPENDENCIES... yes
checking Whether to write dependencies into .pc files... no
checking for perl5... no
checking for perl... /usr/bin/perl
checking for indent... no
checking for lstat... yes
checking for mkstemp... yes
checking for flockfile... yes
checking for _NL_TIME_FIRST_WEEKDAY... yes
checking for sigsetjmp... yes
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
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for catalogs to be installed...  af am ar az az_IR be bg bn br bs ca cs cy da de el en_CA en_GB es et eu fa fi fr ga gl gu he hi hr hu hy ia id is it ja ko ku li lt lv mi mk ml mn mr ms nb ne nl nn no nso pa pl pt pt_BR ro ru rw sk sl sq sr sr@Latn sr@ije sv ta te th tk tr uk uz uz@Latn vi wa xh yi zh_CN zh_HK zh_TW
checking for extra flags to get ANSI library prototypes... none needed
checking for the BeOS... no
checking for HP-UX... no
checking for extra flags for POSIX compliance... none needed
checking for pkg-config... /usr/local/bin/pkg-config
checking for GLIB - version >= 2.8.5... yes (version 2.12.3)
checking for bind_textdomain_codeset... (cached) yes
checking pwd.h usability... yes
checking pwd.h presence... yes
checking for pwd.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for unistd.h... (cached) yes
checking for ANSI C header files... (cached) yes
checking for an ANSI C-conforming const... yes
checking return type of signal handlers... void
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for getpagesize... yes
checking for working mmap... yes
checking for mallinfo... yes
checking for getresuid... yes
checking for uid_t in sys/types.h... yes
checking for fd_set... yes, found in sys/types.h
checking for wchar.h... yes
checking for wctype.h... yes
checking for iswalnum... yes
checking if iswalnum() and friends are properly defined... yes
checking for uxtheme.h... no
checking whether to build gmodulized gdk-pixbuf... yes
checking whether dynamic modules work... yes
checking for TIFFReadScanline in -ltiff... yes
checking tiffio.h usability... yes
checking tiffio.h presence... yes
checking for tiffio.h... yes
checking for jpeg_destroy_decompress in -ljpeg... yes
checking for jpeglib.h... yes
checking for jpeg_simple_progression in -ljpeg... yes
checking for libpng12... yes
checking pixbuf loaders to build...
checking for sys/wait.h that is POSIX.1 compatible... yes
checking return type of signal handlers... (cached) void
checking for x86 platform... yes
checking compiler support for MMX... yes
checking for X... no
configure: error: X development libraries not found
root@paul-desktop:~/Desktop/gtk+-2.8.16# checkinstall -D make install

checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist.
Should I create a default set of package docs?  [y]: y

---

### Post by xeb07170 on 2007-12-20
in case anyone else needs to find the solution - the dev files can be found in the package manager - try doing search for window system - that is how i came across them



thanks for the help mate

---

### Post by nowshining on 2007-12-20
oh no checkinstall when installing logs where the make install puts those files, and then well all done createsa deb file for u :) so u can re-install without having to re-compile from source..

what's the exact program ur trying to install

---

