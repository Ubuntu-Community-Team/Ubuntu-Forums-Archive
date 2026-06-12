---
title: "installing inkscape help"
date: 2006-01-24
forum: Absolute Beginner Talk
---

### Post by mwanafunzi on 2006-01-24
Hi guys,
    I am having some problems intalling inkscape. This is the error that I get  when i apt-get install

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  inkscape: Depends: libgc1 but it is not installable
            Depends: libglibmm-2.4-1 (>= 2.6.1) but it is not installable
            Depends: libgtkmm-2.4-1 but it is not installable
            Depends: libsigc++-2.0-0 (>= 2.0.2) but it is not installable
E: Broken packages



any suggestions?


cheers

---

### Post by AndyCooll on 2006-01-24
It means certain files aren't installed. It doesn't necessarily mean you can't manually install them howwever.

When I come across this type of problem, what I usually do is open up Synaptic and do a search for each of those packages, then I install them individually from there.

:cool:

---

### Post by mwanafunzi on 2006-01-24
I have manually tried reinstalling all those applications that inkscape depends on. It seems that I am still getting the same error. 
I have decided to take a different approach and download the .tar. The problem I am having is that I do not understand most of the output I get when i ./configure..could someone please give some advice..

here is the output i got 
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for intltool >= 0.22... 0.33 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... /usr/bin/msgfmt
checking for msgmerge... /usr/bin/msgmerge
checking for xgettext... /usr/bin/xgettext
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
checking whether gcc and cc understand -c and -o together... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for library containing strerror... none required
checking whether we are using the GNU C++ compiler... (cached) yes
checking whether g++ accepts -g... (cached) yes
checking dependency style of g++... (cached) gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C++ preprocessor... g++ -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking how to run the C preprocessor... gcc -E
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
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
checking whether to build static libraries... yes
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
checking GNU compiler version... 4.0.2
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
checking for catalogs to be installed...  am az be ca cs da de el es es_MX et eu fr ga gl hu it ja mk nb nl nn pa pl pt pt_BR ru sk sl sr sr@Latn sv tr uk zh_CN
checking for pkg-config... /usr/bin/pkg-config
checking for png_read_info in -lpng... yes
checking png.h usability... yes
checking png.h presence... yes
checking for png.h... yes
checking for shl_load in -ldld... no
checking for dlopen... no
checking for dlopen in -ldl... yes
checking gc.h usability... no
checking gc.h presence... no
checking for gc.h... no
checking gc/gc.h usability... yes
checking gc/gc.h presence... yes
checking for gc/gc.h... yes
checking for GC_init in -lgc... yes
checking libgc version 6.4+... 6.4.255 yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking for mallinfo... yes
checking for struct mallinfo.usmblks... yes
checking for struct mallinfo.fsmblks... yes
checking for struct mallinfo.uordblks... yes
checking for struct mallinfo.fordblks... yes
checking for struct mallinfo.hblkhd... yes
checking for freetype-config... /usr/bin/freetype-config
checking for Win32 platform... no
checking pkg-config is at least version 0.9.0... yes
checking for XFT... yes
checking for PANGOFT2... yes
checking for GNOME_VFS... no
checking whether byte ordering is bigendian... no
checking zlib.h usability... yes
checking zlib.h presence... yes
checking for zlib.h... yes
checking for Perl development environment... skipped
checking for Python development environment... skipped
checking for loudmouth-1.0+... no
checking for INKSCAPE... yes
checking popt.h usability... no
checking popt.h presence... no
checking for popt.h... no
configure: error: libpopt is required


the other question pertaining to line 5 or six, is do i need gawk if I have mawk? 
cheers

---

### Post by Nordoelum on 2006-03-31
[QUOTE=mwanafunzi]Hi guys,
    I am having some problems intalling inkscape. This is the error that I get  when i apt-get install

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  inkscape: Depends: libgc1 but it is not installable
            Depends: libglibmm-2.4-1 (>= 2.6.1) but it is not installable
            Depends: libgtkmm-2.4-1 but it is not installable
            Depends: libsigc++-2.0-0 (>= 2.0.2) but it is not installable
E: Broken packages



any suggestions?


cheers[/QUOTE]
Is InkScape on Synaptic?

---

### Post by Nordoelum on 2006-04-02
[quote=mwanafunzi]Hi guys,
    I am having some problems intalling inkscape. This is the error that I get  when i apt-get install

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  inkscape: Depends: libgc1 but it is not installable
            Depends: libglibmm-2.4-1 (>= 2.6.1) but it is not installable
            Depends: libgtkmm-2.4-1 but it is not installable
            Depends: libsigc++-2.0-0 (>= 2.0.2) but it is not installable
E: Broken packages



any suggestions?


cheers[/quote]
I recoomen downloaded the .package

That seams to work :D

Link: [http://prdownloads.sourceforge.net/inkscape/inkscape-0.43.x86.package?download](http://prdownloads.sourceforge.net/inkscape/inkscape-0.43.x86.package?download)

---

