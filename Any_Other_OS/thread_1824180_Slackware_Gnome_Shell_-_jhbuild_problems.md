---
title: "Slackware Gnome Shell - jhbuild problems"
date: 2011-08-13
forum: Any Other OS
---

### Post by 23dornot23d on 2011-08-13
after a fresh 32 bit install .....

Slackware 13.1 for x86
    

   lynx --source [http://gnomeslackbuild.org/net-install](http://gnomeslackbuild.org/net-install) | bash


Got so far ... with Slackware .... 

Gnome Desktop 2.30 works ok

 [http://gnomeslackbuild.org/support/#FAQs](http://gnomeslackbuild.org/support/#FAQs) 

[IMG]http://img854.imageshack.us/img854/8315/screenshotydo.jpg[/IMG]

  run jhbuild 
   .... [http://live.gnome.org/Jhbuild](http://live.gnome.org/Jhbuild)

Created a normal user 

[http://www.webupd8.org/2010/10/insta...in-ubuntu.html]("http://www.webupd8.org/2010/10/install-gnome-shell-from-git-in-ubuntu.html")

[IMG]http://img685.imageshack.us/img685/9435/jhbuild.jpg[/IMG]

-------------------------

**Problem No1**

No package 'libffi' found

> 
                                                 PKG_CONFIG_PATH=/usr/lib/pkgconfig
export PKG_CONFIG_PATH                                 
That appeared to have worked ....... but now there is another problem

ok libffi is in now but sometimes it says yes its there for jhbuild - sometimes its the wrong format ..... 
other times it just does not see it at all (really is driving me nuts) where does this need to be to
get picked up by slackware ...... 

I think the most annoying thing so far is the not knowing ...... is it  looking in /usr/lib or /usr/lib64 for some of the lib files
and why does it tell me they are in the wrong format ..... then if I  remove .... or rename .... /usr/lib     ..... then it compiles ok ....  bizarre
put /usr/lib ........ back again ..... and it either (cannot find the file or its the wrong format)  


[COLOR=Red]**NOT FULLY SORTED YET - COME BACK TO THIS AND SORT PROPERLY**[/COLOR]

[http://sourceware.org/libffi/](http://sourceware.org/libffi/)

----------------------------

**Problem No2**

1/45 ..... glib is ok

2/45 ..... still needs [gnome-common]("http://pkgs.org/slackware-13.1/slacky-i486/gnome-common-2.28.0-i686-1sl.txz.html")  !!!! surely that should be there ....
       ( again is this a problem with 64 bit ....  )

But we can get it from somewhere else. .... the source that is and compile it ....

  [https://launchpad.net/ubuntu/oneiric...ommon/2.34.0-1]("https://launchpad.net/ubuntu/oneiric/+source/gnome-common/2.34.0-1")
( and I realise this should probablly not be used - but its all I can find )

3/45 ..... pixbuf was ok ....
4/45 ..... cairo  was ok ....
5/45 ..... pango was ok ....
6/45 ..... atk now ok ....
7/45 ..... gdk pixbuf ..... ok
8/45 ..... gtk3 ..... in progress ( only 2 Gig of space left on here ....  )

So done another install on the 1 Terra drive ........

------------------------------------

**Problem 3**

[COLOR=Red]( but stuck at 8/45 gtk3 - Pango problem >>> scroll to the bottom .... )[/COLOR]


     Quote:
                                                   CC     gdkenumtypes.lo
  CC     gdkmarshalers.lo
  CCLD   libgdk-3.la
  GISCAN Gdk-3.0.gir
[COLOR=Red]Couldn't find include 'Pango-1.0.gir' (search path:  ['../gdk', '/home/keith/gnome-shell/install/share/gir-1.0',  '/usr/share/gir-1.0', '/home/keith/gnome-shell/install/share/gir-1.0',  '/usr/share/gir-1.0', '/home/keith/gnome-shell/install/share/gir-1.0'])[/COLOR]
make[4]: *** [Gdk-3.0.gir] Error 1
make[4]: Leaving directory `/home/keith/gnome-shell/source/gtk3/gdk'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/keith/gnome-shell/source/gtk3/gdk'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/keith/gnome-shell/source/gtk3/gdk'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/keith/gnome-shell/source/gtk3'
make: *** [all] Error 2
*** Error during phase build of gtk3: ########## Error running make   *** [8/45]

  [1] Rerun phase build
  [2] Ignore error and continue to install
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration

                                


looking for [COLOR=Red]/share/gir-1.0[/COLOR]

which is in   /home/keith/gnome-shell/install/share/gir-1.0/

because Pango-1.0.gir is not in there .....

> 
[COLOR=Red]Couldn't find include 'Pango-1.0.gir' (search path:   ['../gdk', '/home/keith/gnome-shell/install/share/gir-1.0',   '/usr/share/gir-1.0', '/home/keith/gnome-shell/install/share/gir-1.0',   '/usr/share/gir-1.0', '/home/keith/gnome-shell/install/share/gir-1.0'])[/COLOR]
Its in its own directory ..... so why not here and should it point to the
Pango directory now ..... or should the Pango file be brought across into
the share directory ......


Come back to this later .... when Gnome-Shell 3.2 is out .....
as we seem to be missing a few things ....


For 64 bit ....

[http://pkgs.org/#slackware-13.37](http://pkgs.org/#slackware-13.37)

[http://pkgs.org/slackware-13.37/gnome-slackbuild-3.0-extra-x86_64/](http://pkgs.org/slackware-13.37/gnome-slackbuild-3.0-extra-x86_64/)

______________________________

Not for 64 bit though ,,,,, [COLOR=Red]**( Maybe I should have used the 32 bit version to start with )**[/COLOR]

[http://pkgs.org/slackware-13.37/gnome-slackbuild-3.0-testing-i486/](http://pkgs.org/slackware-13.37/gnome-slackbuild-3.0-testing-i486/)

___________________________________________
for later ....
may need to look here later to tidy up things ....
[http://www.linuxquestions.org/questi...things-647616/]("http://www.linuxquestions.org/questions/slackware-14/cleaning-slackware-deleting-unnecesary-things-647616/")

Side tracked here [http://alien.slackbook.org/dokuwiki/...kware:multilib]("http://alien.slackbook.org/dokuwiki/doku.php?id=slackware:multilib")

[http://slackfind.net/en/packages/sea...i&distversion=]("http://slackfind.net/en/packages/search/?name=libffi&distversion=")

So how do you [_***install a *.txz***_]("http://www.fileinfo.com/extension/txz") file ... ?

                                                                                               __________________

---

### Post by 23dornot23d on 2011-08-14
Lets see if we can bottom one problem at a time then .....


-------------------------

**Problem No1**

No package 'libffi' found

     Quote:
                                                                                                  PKG_CONFIG_PATH=/usr/lib/pkgconfig
export PKG_CONFIG_PATH                                                                  
That appeared to have worked ....... but now there is another problem

ok libffi is in now but sometimes it says yes its there for jhbuild - sometimes its the wrong format ..... 
other times it just does not see it at all (really is driving me nuts) where does this need to be to
get picked up by slackware ...... 

I think the most annoying thing so far is the not knowing ...... is it   looking in /usr/lib or /usr/lib64 for some of the lib files
and why does it tell me they are in the wrong format ..... then if I   remove .... or rename .... /usr/lib     ..... then it compiles ok ....   bizarre
put /usr/lib ........ back again ..... and it either (cannot find the file or its the wrong format)  


[COLOR=Red]**NOT FULLY SORTED YET - COME BACK TO THIS AND SORT PROPERLY**[/COLOR]

[http://sourceware.org/libffi/](http://sourceware.org/libffi/)

----------------------------


```

bash: ./autogen.sh: No such file or directory
bash-4.1$ ls
Desktop                  gnome-shell-build-setup.sh
Source                  installslax
bin                  jhbuild
gnome-common-2.34.0          lib64
gnome-common_2.34.0-1_all.deb      libffi-3.0.8
gnome-common_2.34.0.orig.tar.bz2  libffi-3.0.8-i486-2as.txz
gnome-shell              libffi-3.0.8.tar.gz
bash-4.1$ cd libffi-3.0.8
bash-4.1$ ls
ChangeLog      compile      include         ltmain.sh
ChangeLog.libffi  config.guess      install-sh         man
ChangeLog.libgcj  config.log      libffi.la         mdate-sh
ChangeLog.v1      config.status   libffi.pc         missing
LICENSE          config.sub      libffi.pc.in         mkinstalldirs
Makefile      configure      libffi_convenience.la  src
Makefile.am      configure.ac      libtool         stamp-h1
Makefile.in      configure.host  libtool-version     testsuite
README          depcomp      ltcf-c.sh         texinfo.tex
TODO          doc          ltcf-cxx.sh
acinclude.m4      fficonfig.h      ltcf-gcj.sh
aclocal.m4      fficonfig.h.in  ltconfig
bash-4.1$ PKG_CONFIG_PATH=/usr/lib/pkgconfig
bash-4.1$ export PKG_CONFIG_PATH
bash-4.1$ export PATH=$PATH:/home/keith/bin
bash-4.1$ ./configure
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/ginstall -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /usr/bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking dependency style of gcc... gcc3
checking whether gcc and cc understand -c and -o together... yes
checking for a sed that does not truncate output... /usr/bin/sed
checking for grep that handles long lines and -e... /usr/bin/grep
checking for egrep... /usr/bin/grep -E
checking for ld used by gcc... /usr/x86_64-slackware-linux/bin/ld
checking if the linker (/usr/x86_64-slackware-linux/bin/ld) is GNU ld... yes
checking for /usr/x86_64-slackware-linux/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
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
checking for g77... g77
checking whether we are using the GNU Fortran 77 compiler... yes
checking whether g77 accepts -g... yes
checking the maximum length of command line arguments... 1572864
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
checking whether the gcc linker (/usr/x86_64-slackware-linux/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/x86_64-slackware-linux/bin/ld -m elf_x86_64
checking if the linker (/usr/x86_64-slackware-linux/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/x86_64-slackware-linux/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/x86_64-slackware-linux/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
(cached) (cached) checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for g77 option to produce PIC... -fPIC
checking if g77 PIC flag -fPIC works... yes
checking if g77 static flag -static works... yes
checking if g77 supports -c -o file.o... yes
checking whether the g77 linker (/usr/x86_64-slackware-linux/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
(cached) (cached) checking how to hardcode library paths into programs... immediate
checking whether to enable maintainer-specific portions of Makefiles... no
checking sys/mman.h usability... yes
checking sys/mman.h presence... yes
checking for sys/mman.h... yes
checking for mmap... yes
checking for sys/mman.h... (cached) yes
checking for mmap... (cached) yes
checking whether read-only mmap of a plain file works... yes
checking whether mmap from /dev/zero works... yes
checking for MAP_ANON(YMOUS)... yes
checking whether mmap with MAP_ANON(YMOUS) works... yes
checking for ANSI C header files... (cached) yes
checking for memcpy... yes
checking for working alloca.h... yes
checking for alloca... yes
checking size of double... 8
checking size of long double... 16
checking whether byte ordering is bigendian... no
checking assembler .cfi pseudo-op support... yes
checking assembler supports pc related relocs... yes
checking whether .eh_frame section should be read-only... no
checking for __attribute__((visibility("hidden")))... yes
configure: creating ./config.status
config.status: creating include/Makefile
config.status: creating include/ffi.h
config.status: creating Makefile
config.status: creating testsuite/Makefile
config.status: creating man/Makefile
config.status: creating libffi.pc
config.status: creating fficonfig.h
config.status: fficonfig.h is unchanged
config.status: linking src/x86/ffitarget.h to include/ffitarget.h
config.status: executing depfiles commands
config.status: executing include commands
config.status: executing src commands
bash-4.1$ make
make "AR_FLAGS=" "CC_FOR_BUILD=" "CFLAGS=-g -O2" "CXXFLAGS=-g -O2" "CFLAGS_FOR_BUILD=" "CFLAGS_FOR_TARGET=" "INSTALL=/usr/bin/ginstall -c" "INSTALL_DATA=/usr/bin/ginstall -c -m 644" "INSTALL_PROGRAM=/usr/bin/ginstall -c" "INSTALL_SCRIPT=/usr/bin/ginstall -c" "JC1FLAGS=" "LDFLAGS=" "LIBCFLAGS=" "LIBCFLAGS_FOR_TARGET=" "MAKE=make" "MAKEINFO=/bin/sh /home/keith/libffi-3.0.8/missing --run makeinfo " "PICFLAG=" "PICFLAG_FOR_TARGET=" "RUNTESTFLAGS=" "SHELL=/bin/sh" "exec_prefix=/usr/local" "infodir=/usr/local/share/info" "libdir=/usr/local/lib" "prefix=/usr/local" "AR=ar" "AS=as" "CC=gcc" "CXX=g++" "LD=ld" "NM=" "RANLIB=ranlib" "DESTDIR=" all-recursive
make[1]: Entering directory `/home/keith/libffi-3.0.8'
Making all in include
make[2]: Entering directory `/home/keith/libffi-3.0.8/include'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/keith/libffi-3.0.8/include'
Making all in testsuite
make[2]: Entering directory `/home/keith/libffi-3.0.8/testsuite'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/keith/libffi-3.0.8/testsuite'
Making all in man
make[2]: Entering directory `/home/keith/libffi-3.0.8/man'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/keith/libffi-3.0.8/man'
make[2]: Entering directory `/home/keith/libffi-3.0.8'
depbase=`echo src/debug.lo | sed 's|[^/]*$|.deps/&|;s|\.lo$||'`;\
/bin/sh ./libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I.  -I. -I./include -Iinclude -I./src  -Wall -g -fexceptions -g -O2 -MT src/debug.lo -MD -MP -MF $depbase.Tpo -c -o src/debug.lo src/debug.c &&\
mv -f $depbase.Tpo $depbase.Plo
 gcc -DHAVE_CONFIG_H -I. -I. -I./include -Iinclude -I./src -Wall -g -fexceptions -g -O2 -MT src/debug.lo -MD -MP -MF src/.deps/debug.Tpo -c src/debug.c  -fPIC -DPIC -o src/.libs/debug.o
 gcc -DHAVE_CONFIG_H -I. -I. -I./include -Iinclude -I./src -Wall -g -fexceptions -g -O2 -MT src/debug.lo -MD -MP -MF src/.deps/debug.Tpo -c src/debug.c -o src/debug.o >/dev/null 2>&1
depbase=`echo src/prep_cif.lo | sed 's|[^/]*$|.deps/&|;s|\.lo$||'`;\
/bin/sh ./libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I.  -I. -I./include -Iinclude -I./src  -Wall -g -fexceptions -g -O2 -MT src/prep_cif.lo -MD -MP -MF $depbase.Tpo -c -o src/prep_cif.lo src/prep_cif.c &&\
mv -f $depbase.Tpo $depbase.Plo
 gcc -DHAVE_CONFIG_H -I. -I. -I./include -Iinclude -I./src -Wall -g -fexceptions -g -O2 -MT src/prep_cif.lo -MD -MP -MF src/.deps/prep_cif.Tpo -c src/prep_cif.c  -fPIC -DPIC -o src/.libs/prep_cif.o
 gcc -DHAVE_CONFIG_H -I. -I. -I./include -Iinclude -I./src -Wall -g -fexceptions -g -O2 -MT src/prep_cif.lo -MD -MP -MF src/.deps/prep_cif.Tpo -c src/prep_cif.c -o src/prep_cif.o >/dev/null 2>&1
depbase=`echo src/types.lo | sed 's|[^/]*$|.deps/&|;s|\.lo$||'`;\
/bin/sh ./libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I.  -I. -I./include -Iinclude -I./src  -Wall -g -fexceptions -g -O2 -MT src/types.lo -MD -MP -MF $depbase.Tpo -c -o src/types.lo src/types.c &&\
mv -f $depbase.Tpo $depbase.Plo
 gcc -DHAVE_CONFIG_H -I. -I. -I./include -Iinclude -I./src -Wall -g -fexceptions -g -O2 -MT src/types.lo -MD -MP -MF src/.deps/types.Tpo -c src/types.c  -fPIC -DPIC -o src/.libs/types.o
 gcc -DHAVE_CONFIG_H -I. -I. -I./include -Iinclude -I./src -Wall -g -fexceptions -g -O2 -MT src/types.lo -MD -MP -MF src/.deps/types.Tpo -c src/types.c -o src/types.o >/dev/null 2>&1
depbase=`echo src/raw_api.lo | sed 's|[^/]*$|.deps/&|;s|\.lo$||'`;\
/bin/sh ./libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I.  -I. -I./include -Iinclude -I./src  -Wall -g -fexceptions -g -O2 -MT src/raw_api.lo -MD -MP -MF $depbase.Tpo -c -o src/raw_api.lo src/raw_api.c &&\
mv -f $depbase.Tpo $depbase.Plo
 gcc -DHAVE_CONFIG_H -I. -I. -I./include -Iinclude -I./src -Wall -g -fexceptions -g -O2 -MT src/raw_api.lo -MD -MP -MF src/.deps/raw_api.Tpo -c src/raw_api.c  -fPIC -DPIC -o src/.libs/raw_api.o
 gcc -DHAVE_CONFIG_H -I. -I. -I./include -Iinclude -I./src -Wall -g -fexceptions -g -O2 -MT src/raw_api.lo -MD -MP -MF src/.deps/raw_api.Tpo -c src/raw_api.c -o src/raw_api.o >/dev/null 2>&1
depbase=`echo src/java_raw_api.lo | sed 's|[^/]*$|.deps/&|;s|\.lo$||'`;\
/bin/sh ./libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I.  -I. -I./include -Iinclude -I./src  -Wall -g -fexceptions -g -O2 -MT src/java_raw_api.lo -MD -MP -MF $depbase.Tpo -c -o src/java_raw_api.lo src/java_raw_api.c &&\
mv -f $depbase.Tpo $depbase.Plo
 gcc -DHAVE_CONFIG_H -I. -I. -I./include -Iinclude -I./src -Wall -g -fexceptions -g -O2 -MT src/java_raw_api.lo -MD -MP -MF src/.deps/java_raw_api.Tpo -c src/java_raw_api.c  -fPIC -DPIC -o src/.libs/java_raw_api.o
 gcc -DHAVE_CONFIG_H -I. -I. -I./include -Iinclude -I./src -Wall -g -fexceptions -g -O2 -MT src/java_raw_api.lo -MD -MP -MF src/.deps/java_raw_api.Tpo -c src/java_raw_api.c -o src/java_raw_api.o >/dev/null 2>&1
depbase=`echo src/closures.lo | sed 's|[^/]*$|.deps/&|;s|\.lo$||'`;\
/bin/sh ./libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I.  -I. -I./include -Iinclude -I./src  -Wall -g -fexceptions -g -O2 -MT src/closures.lo -MD -MP -MF $depbase.Tpo -c -o src/closures.lo src/closures.c &&\
mv -f $depbase.Tpo $depbase.Plo
 gcc -DHAVE_CONFIG_H -I. -I. -I./include -Iinclude -I./src -Wall -g -fexceptions -g -O2 -MT src/closures.lo -MD -MP -MF src/.deps/closures.Tpo -c src/closures.c  -fPIC -DPIC -o src/.libs/closures.o
 gcc -DHAVE_CONFIG_H -I. -I. -I./include -Iinclude -I./src -Wall -g -fexceptions -g -O2 -MT src/closures.lo -MD -MP -MF src/.deps/closures.Tpo -c src/closures.c -o src/closures.o >/dev/null 2>&1
depbase=`echo src/x86/ffi64.lo | sed 's|[^/]*$|.deps/&|;s|\.lo$||'`;\
/bin/sh ./libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I.  -I. -I./include -Iinclude -I./src  -Wall -g -fexceptions -g -O2 -MT src/x86/ffi64.lo -MD -MP -MF $depbase.Tpo -c -o src/x86/ffi64.lo src/x86/ffi64.c &&\
mv -f $depbase.Tpo $depbase.Plo
 gcc -DHAVE_CONFIG_H -I. -I. -I./include -Iinclude -I./src -Wall -g -fexceptions -g -O2 -MT src/x86/ffi64.lo -MD -MP -MF src/x86/.deps/ffi64.Tpo -c src/x86/ffi64.c  -fPIC -DPIC -o src/x86/.libs/ffi64.o
 gcc -DHAVE_CONFIG_H -I. -I. -I./include -Iinclude -I./src -Wall -g -fexceptions -g -O2 -MT src/x86/ffi64.lo -MD -MP -MF src/x86/.deps/ffi64.Tpo -c src/x86/ffi64.c -o src/x86/ffi64.o >/dev/null 2>&1
depbase=`echo src/x86/unix64.lo | sed 's|[^/]*$|.deps/&|;s|\.lo$||'`;\
/bin/sh ./libtool   --mode=compile gcc -DHAVE_CONFIG_H -I.  -I. -I./include -Iinclude -I./src  -I. -I./include -Iinclude -I./src -g -O2 -MT src/x86/unix64.lo -MD -MP -MF $depbase.Tpo -c -o src/x86/unix64.lo src/x86/unix64.S &&\
mv -f $depbase.Tpo $depbase.Plo
 gcc -DHAVE_CONFIG_H -I. -I. -I./include -Iinclude -I./src -I. -I./include -Iinclude -I./src -g -O2 -MT src/x86/unix64.lo -MD -MP -MF src/x86/.deps/unix64.Tpo -c src/x86/unix64.S  -fPIC -DPIC -o src/x86/.libs/unix64.o
 gcc -DHAVE_CONFIG_H -I. -I. -I./include -Iinclude -I./src -I. -I./include -Iinclude -I./src -g -O2 -MT src/x86/unix64.lo -MD -MP -MF src/x86/.deps/unix64.Tpo -c src/x86/unix64.S -o src/x86/unix64.o >/dev/null 2>&1
/bin/sh ./libtool --tag=CC   --mode=link gcc -Wall -g -fexceptions -g -O2 -version-info `grep -v '^#' ./libtool-version`  -o libffi.la -rpath /usr/local/lib src/debug.lo src/prep_cif.lo src/types.lo src/raw_api.lo src/java_raw_api.lo src/closures.lo                   src/x86/ffi64.lo src/x86/unix64.lo src/x86/ffi.lo src/x86/sysv.lo      
rm -fr  .libs/libffi.a .libs/libffi.la .libs/libffi.lai .libs/libffi.so .libs/libffi.so.5 .libs/libffi.so.5.0.9
gcc -shared  src/.libs/debug.o src/.libs/prep_cif.o src/.libs/types.o src/.libs/raw_api.o src/.libs/java_raw_api.o src/.libs/closures.o src/x86/.libs/ffi64.o src/x86/.libs/unix64.o src/x86/.libs/ffi.o src/x86/.libs/sysv.o   -Wl,-soname -Wl,libffi.so.5 -o .libs/libffi.so.5.0.9
(cd .libs && rm -f libffi.so.5 && ln -s libffi.so.5.0.9 libffi.so.5)
(cd .libs && rm -f libffi.so && ln -s libffi.so.5.0.9 libffi.so)
ar cru .libs/libffi.a  src/debug.o src/prep_cif.o src/types.o src/raw_api.o src/java_raw_api.o src/closures.o src/x86/ffi64.o src/x86/unix64.o src/x86/ffi.o src/x86/sysv.o
ranlib .libs/libffi.a
creating libffi.la
(cd .libs && rm -f libffi.la && ln -s ../libffi.la libffi.la)
/bin/sh ./libtool --tag=CC   --mode=link gcc -Wall -g -fexceptions -g -O2   -o libffi_convenience.la  src/debug.lo src/prep_cif.lo src/types.lo src/raw_api.lo src/java_raw_api.lo src/closures.lo                   src/x86/ffi64.lo src/x86/unix64.lo src/x86/ffi.lo src/x86/sysv.lo      
rm -fr  .libs/libffi_convenience.a .libs/libffi_convenience.la
ar cru .libs/libffi_convenience.a src/.libs/debug.o src/.libs/prep_cif.o src/.libs/types.o src/.libs/raw_api.o src/.libs/java_raw_api.o src/.libs/closures.o src/x86/.libs/ffi64.o src/x86/.libs/unix64.o src/x86/.libs/ffi.o src/x86/.libs/sysv.o
ranlib .libs/libffi_convenience.a
creating libffi_convenience.la
(cd .libs && rm -f libffi_convenience.la && ln -s ../libffi_convenience.la libffi_convenience.la)
make[2]: Leaving directory `/home/keith/libffi-3.0.8'
make[1]: Leaving directory `/home/keith/libffi-3.0.8'
bash-4.1$ su
Password: 
bash-4.1# make install
Making install in include
make[1]: Entering directory `/home/keith/libffi-3.0.8/include'
make[2]: Entering directory `/home/keith/libffi-3.0.8/include'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/libffi-3.0.8/include" || /usr/bin/mkdir -p "/usr/local/lib/libffi-3.0.8/include"
 /usr/bin/ginstall -c -m 644 'ffi.h' '/usr/local/lib/libffi-3.0.8/include/ffi.h'
 /usr/bin/ginstall -c -m 644 'ffitarget.h' '/usr/local/lib/libffi-3.0.8/include/ffitarget.h'
make[2]: Leaving directory `/home/keith/libffi-3.0.8/include'
make[1]: Leaving directory `/home/keith/libffi-3.0.8/include'
Making install in testsuite
make[1]: Entering directory `/home/keith/libffi-3.0.8/testsuite'
make[2]: Entering directory `/home/keith/libffi-3.0.8/testsuite'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/keith/libffi-3.0.8/testsuite'
make[1]: Leaving directory `/home/keith/libffi-3.0.8/testsuite'
Making install in man
make[1]: Entering directory `/home/keith/libffi-3.0.8/man'
make[2]: Entering directory `/home/keith/libffi-3.0.8/man'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/man/man3" || /usr/bin/mkdir -p "/usr/local/share/man/man3"
 /usr/bin/ginstall -c -m 644 './ffi.3' '/usr/local/share/man/man3/ffi.3'
 /usr/bin/ginstall -c -m 644 './ffi_call.3' '/usr/local/share/man/man3/ffi_call.3'
 /usr/bin/ginstall -c -m 644 './ffi_prep_cif.3' '/usr/local/share/man/man3/ffi_prep_cif.3'
make[2]: Leaving directory `/home/keith/libffi-3.0.8/man'
make[1]: Leaving directory `/home/keith/libffi-3.0.8/man'
make[1]: Entering directory `/home/keith/libffi-3.0.8'
make[2]: Entering directory `/home/keith/libffi-3.0.8'
test -z "/usr/local/lib" || /usr/bin/mkdir -p "/usr/local/lib"
 /bin/sh ./libtool   --mode=install /usr/bin/ginstall -c  'libffi.la' '/usr/local/lib/libffi.la'
/usr/bin/ginstall -c .libs/libffi.so.5.0.9 /usr/local/lib/libffi.so.5.0.9
(cd /usr/local/lib && { ln -s -f libffi.so.5.0.9 libffi.so.5 || { rm -f libffi.so.5 && ln -s libffi.so.5.0.9 libffi.so.5; }; })
(cd /usr/local/lib && { ln -s -f libffi.so.5.0.9 libffi.so || { rm -f libffi.so && ln -s libffi.so.5.0.9 libffi.so; }; })
/usr/bin/ginstall -c .libs/libffi.lai /usr/local/lib/libffi.la
/usr/bin/ginstall -c .libs/libffi.a /usr/local/lib/libffi.a
chmod 644 /usr/local/lib/libffi.a
ranlib /usr/local/lib/libffi.a
PATH="$PATH:/sbin" ldconfig -n /usr/local/lib
----------------------------------------------------------------------
[COLOR=Red][B]Libraries have been installed in:
   /usr/local/lib[/B][/COLOR]

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
test -z "/usr/local/share/info" || /usr/bin/mkdir -p "/usr/local/share/info"
 /usr/bin/ginstall -c -m 644 './doc/libffi.info' '/usr/local/share/info/libffi.info'
 install-info --info-dir='/usr/local/share/info' '/usr/local/share/info/libffi.info'
test -z "/usr/local/lib/pkgconfig" || /usr/bin/mkdir -p "/usr/local/lib/pkgconfig"
 /usr/bin/ginstall -c -m 644 'libffi.pc' '/usr/local/lib/pkgconfig/libffi.pc'
make[2]: Leaving directory `/home/keith/libffi-3.0.8'
make[1]: Leaving directory `/home/keith/libffi-3.0.8'
bash-4.1# 


```[COLOR=Red][B]Libraries have been installed in:    /usr/local/lib

should this have been lib64 ?

[COLOR=Black]completely wipe the directory for glib now and see what it reports back after jhbuild


Feel Free to join in if you see something glareingly obvious that I am doing wrong here.......

I am a designer not a programmer ....

It still is not finding it ..........

```

checking for python version... 2.6
checking for python platform... linux2
checking for python script directory... ${prefix}/lib64/python2.6/site-packages
checking for python extension module directory... ${exec_prefix}/lib64/python2.6/site-packages
checking for iconv_open... yes
checking whether to cache iconv descriptors... no
checking for ZLIB... yes
checking for LIBFFI... no
configure: error: Package requirements (libffi >= 3.0.0) were not met:

No package 'libffi' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LIBFFI_CFLAGS
and LIBFFI_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
*** Error during phase configure of glib: ########## Error running ./autogen.sh --prefix /home/keith/gnome-shell/install --libdir '/home/keith/gnome-shell/install/lib64'  --disable-static --disable-gtk-doc  *** [1/45]

  [1] Rerun phase configure
  [2] Ignore error and continue to configure
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "clean"
  [8] Go to phase "distclean"
choice: invalid choice


```and now it does it ok ,,,,, Bizarre .....

```

checking pkg-config is at least version 0.16... yes
checking for gawk... (cached) gawk
checking for perl5... no
checking for perl... perl
checking for indent... indent
checking for perl... /usr/bin/perl
checking for a Python interpreter with version >= 2.5... python
checking for python... /usr/bin/python
checking for python version... 2.6
checking for python platform... linux2
checking for python script directory... ${prefix}/lib64/python2.6/site-packages
checking for python extension module directory... ${exec_prefix}/lib64/python2.6/site-packages
checking for iconv_open... yes
checking whether to cache iconv descriptors... no
checking for ZLIB... yes

```[/COLOR]```
[COLOR=Black][COLOR=Red]checking for LIBFFI... yes[/COLOR][/COLOR]
```[/B]```
[B][COLOR=Black]
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
checking for catalogs to be installed...  af am ar as ast az be be@latin bg bn bn_IN bs ca ca@valencia cs cy da de dz el en_CA en_GB en@shaw eo es et eu fa fi fr ga gl gu he hi hr hu hy id is it ja ka kk kn ko ku lt lv mai mg mk ml mn mr ms nb nds ne nl nn oc or pa pl ps pt pt_BR ro ru rw si sk sl sq sr sr@latin sr@ije sv ta te th tl tr ug tt uk vi wa xh yi zh_CN zh_HK zh_TW
checking how to print strings... printf
checking for a sed that does not truncate output... /usr/bin/sed
checking for fgrep... /usr/bin/grep -F
checking for ld used by gcc... /usr/x86_64-slackware-linux/bin/ld
checking if the linker (/usr/x86_64-slackware-linux/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking how to convert x86_64-unknown-linux-gnu file names to x86_64-unknown-linux-gnu format... func_convert_file_noop
checking how to convert x86_64-unknown-linux-gnu file names to toolchain format... func_convert_file_noop
checking for /usr/x86_64-slackware-linux/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for dlltool... no
checking how to associate runtime and link libraries... printf %s\n
checking for ar... ar
checking for archiver @FILE support... @
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for sysroot... no
checking for mt... mt
checking if mt is a manifest tool... no
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/x86_64-slackware-linux/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking how to run the C++ preprocessor... c++ -E
checking for ld used by c++... /usr/x86_64-slackware-linux/bin/ld -m elf_x86_64
checking if the linker (/usr/x86_64-slackware-linux/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the c++ linker (/usr/x86_64-slackware-linux/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for c++ option to produce PIC... -fPIC -DPIC
checking if c++ PIC flag -fPIC -DPIC works... yes
checking if c++ static flag -static works... yes
checking if c++ supports -c -o file.o... yes
checking if c++ supports -c -o file.o... (cached) yes
checking whether the c++ linker (/usr/x86_64-slackware-linux/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... (cached) GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
configure: creating ./config.lt
config.lt: creating libtool
checking for extra flags to get ANSI library prototypes... none needed
checking for extra flags for POSIX compliance... none needed
checking for ANSI C header files... yes
checking for vprintf... yes
checking for _doprnt... no
checking for size_t... yes
checking for working alloca.h... yes
checking for alloca... yes
checking for mmap... yes
checking for posix_memalign... yes
checking for memalign... yes
checking for valloc... yes
checking for fsync... yes
checking for pipe2... yes
checking for atexit... yes
checking for on_exit... yes
checking for timegm... yes
checking for gmtime_r... yes
checking for qsort_r... yes
checking if qsort_r uses glibc compatible argument order... yes
checking size of char... 1
checking size of short... 2
checking size of long... 8
checking size of int... 4
checking size of void *... 8
checking size of long long... 8
checking size of __int64... 0
checking for format to printf and scanf a guint64... %llu
checking for an ANSI C-conforming const... yes
checking if malloc() and friends prototypes are gmem.h compatible... yes
checking for growing stack pointer... no
checking for __inline... yes
checking for __inline__... yes
checking for inline... yes
checking if inline functions in headers work... yes
checking for working do while(0) macros... yes
checking for ISO C99 varargs macros in C... yes
checking for ISO C99 varargs macros in C++... yes
checking for GNUC varargs macros... yes
checking for GNUC visibility attribute... yes
checking whether using Sun Studio C compiler... no
checking whether byte ordering is bigendian... no
checking dirent.h usability... yes
checking dirent.h presence... yes
checking for dirent.h... yes
checking float.h usability... yes
checking float.h presence... yes
checking for float.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking pwd.h usability... yes
checking pwd.h presence... yes
checking for pwd.h... yes
checking grp.h usability... yes
checking grp.h presence... yes
checking for grp.h... yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking sys/poll.h usability... yes
checking sys/poll.h presence... yes
checking for sys/poll.h... yes
checking sys/resource.h usability... yes
checking sys/resource.h presence... yes
checking for sys/resource.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking sys/times.h usability... yes
checking sys/times.h presence... yes
checking for sys/times.h... yes
checking sys/wait.h usability... yes
checking sys/wait.h presence... yes
checking for sys/wait.h... yes
checking unistd.h usability... yes
checking unistd.h presence... yes
checking for unistd.h... yes
checking values.h usability... yes
checking values.h presence... yes
checking for values.h... yes
checking sys/select.h usability... yes
checking sys/select.h presence... yes
checking for sys/select.h... yes
checking sys/types.h usability... yes
checking sys/types.h presence... yes
checking for sys/types.h... yes
checking stdint.h usability... yes
checking stdint.h presence... yes
checking for stdint.h... yes
checking inttypes.h usability... yes
checking inttypes.h presence... yes
checking for inttypes.h... yes
checking sched.h usability... yes
checking sched.h presence... yes
checking for sched.h... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking sys/vfs.h usability... yes
checking sys/vfs.h presence... yes
checking for sys/vfs.h... yes
checking sys/mount.h usability... yes
checking sys/mount.h presence... yes
checking for sys/mount.h... yes
checking sys/vmount.h usability... no
checking sys/vmount.h presence... no
checking for sys/vmount.h... no
checking sys/statfs.h usability... yes
checking sys/statfs.h presence... yes
checking for sys/statfs.h... yes
checking sys/statvfs.h usability... yes
checking sys/statvfs.h presence... yes
checking for sys/statvfs.h... yes
checking mntent.h usability... yes
checking mntent.h presence... yes
checking for mntent.h... yes
checking sys/mnttab.h usability... no
checking sys/mnttab.h presence... no
checking for sys/mnttab.h... no
checking sys/vfstab.h usability... no
checking sys/vfstab.h presence... no
checking for sys/vfstab.h... no
checking sys/mntctl.h usability... no
checking sys/mntctl.h presence... no
checking for sys/mntctl.h... no
checking sys/sysctl.h usability... yes
checking sys/sysctl.h presence... yes
checking for sys/sysctl.h... yes
checking fstab.h usability... yes
checking fstab.h presence... yes
checking for fstab.h... yes
checking sys/uio.h usability... yes
checking sys/uio.h presence... yes
checking for sys/uio.h... yes
checking sys/mkdev.h usability... no
checking sys/mkdev.h presence... no
checking for sys/mkdev.h... no
checking linux/magic.h usability... yes
checking linux/magic.h presence... yes
checking for linux/magic.h... yes
checking for struct stat.st_mtimensec... no
checking for struct stat.st_mtim.tv_nsec... no
checking for struct stat.st_atimensec... no
checking for struct stat.st_atim.tv_nsec... no
checking for struct stat.st_ctimensec... no
checking for struct stat.st_ctim.tv_nsec... no
checking for struct stat.st_blksize... yes
checking for struct stat.st_blocks... yes
checking for struct statfs.f_fstypename... no
checking for struct statfs.f_bavail... yes
checking for struct statvfs.f_basetype... no
checking for struct tm.tm_gmtoff... yes
checking for struct tm.__tm_gmtoff... no
checking for nl_langinfo and CODESET... yes
checking stddef.h usability... yes
checking stddef.h presence... yes
checking for stddef.h... yes
checking stdlib.h usability... yes
checking stdlib.h presence... yes
checking for stdlib.h... yes
checking string.h usability... yes
checking string.h presence... yes
checking for string.h... yes
checking for setlocale... yes
checking size of size_t... 8
checking for the appropriate definition for size_t... unsigned long
checking for lstat... yes
checking for strerror... yes
checking for strsignal... yes
checking for memmove... yes
checking for vsnprintf... yes
checking for stpcpy... yes
checking for strcasecmp... yes
checking for strncasecmp... yes
checking for poll... yes
checking for getcwd... yes
checking for vasprintf... yes
checking for setenv... yes
checking for unsetenv... yes
checking for getc_unlocked... yes
checking for readlink... yes
checking for symlink... yes
checking for fdwalk... no
checking for memmem... yes
checking for chown... yes
checking for lchmod... no
checking for lchown... yes
checking for fchmod... yes
checking for fchown... yes
checking for link... yes
checking for utimes... yes
checking for getgrgid... yes
checking for getpwuid... yes
checking for getmntent_r... yes
checking for setmntent... yes
checking for endmntent... yes
checking for hasmntopt... yes
checking for getmntinfo... no
checking for splice... yes
checking for statvfs... yes
checking for statfs... yes
checking whether to use statfs or statvfs... statfs
checking crt_externs.h usability... no
checking crt_externs.h presence... no
checking for crt_externs.h... no
checking for _NSGetEnviron... no
checking for C99 vsnprintf... yes
checking whether printf supports positional parameters... yes
checking value of AF_INET... 2
checking value of AF_INET6... 10
checking value of AF_UNIX... 1
checking value of MSG_PEEK... 2
checking value of MSG_OOB... 1
checking value of MSG_DONTROUTE... 4
checking for getprotobyname_r... yes
checking for endservent... yes
checking netdb.h usability... yes
checking netdb.h presence... yes
checking for netdb.h... yes
checking wspiapi.h usability... no
checking wspiapi.h presence... no
checking for wspiapi.h... no
checking for strndup... yes
checking for setresuid... yes
checking for setreuid... yes
checking sys/prctl.h usability... yes
checking sys/prctl.h presence... yes
checking for sys/prctl.h... yes
checking arpa/nameser_compat.h usability... yes
checking arpa/nameser_compat.h presence... yes
checking for arpa/nameser_compat.h... yes
checking for res_query... in -lresolv
checking number of arguments to statfs()... 2
checking for signed... yes
checking for long long... yes
checking for long double... yes
checking for wchar_t... yes
checking for wint_t... yes
checking for size_t... (cached) yes
checking for ptrdiff_t... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for snprintf... yes
checking for wcslen... yes
checking for C99 snprintf... yes
checking for sys_errlist... yes
checking for sys_siglist... yes
checking for sys_siglist declaration... yes
checking for fd_set... yes, found in sys/types.h
checking whether realloc (NULL,) will work... yes
checking for nl_langinfo (CODESET)... yes
checking for a compliant posix_memalign() implementation... yes
checking for OpenBSD strlcpy/strlcat... no
checking for an implementation of va_copy()... yes
checking for an implementation of __va_copy()... yes
checking whether va_lists can be copied by value... no
checking for dlopen... no
checking for NSLinkModule... no
checking for dlopen in -ldl... yes
checking for dlsym in -ldl... yes
/usr/lib64/gcc/x86_64-slackware-linux/4.5.2/../../../../lib64/crt1.o: In function `_start':
/glibc-tmp-714dc68a4bbd6ca2b142f97bdca9dd8b/glibc-2.13/csu/../sysdeps/x86_64/elf/start.S:109: undefined reference to `main'
collect2: ld returned 1 exit status
checking for RTLD_GLOBAL brokenness... no
checking for preceeding underscore in symbols... no
checking for dlerror... yes
checking for the suffix of module shared libraries... .so
checking for gspawn implementation... gspawn.lo
checking for GIOChannel implementation... giounix.lo
checking for is_selinux_enabled in -lselinux... no
checking sys/inotify.h usability... yes
checking sys/inotify.h presence... yes
checking for sys/inotify.h... yes
checking for inotify_init1... yes
checking for FAMOpen in -lfam... yes
checking fam.h usability... yes
checking fam.h presence... yes
checking for fam.h... yes
checking for FAMNoExists in -lfam... yes
checking for getxattr in -lc... yes
checking sys/xattr.h usability... yes
checking sys/xattr.h presence... yes
checking for sys/xattr.h... yes
checking for XATTR_NOFOLLOW... no
checking for platform-dependent source... 
checking whether to compile timeloop... yes
checking if building for some Win32 platform... no
checking for thread implementation... posix
checking thread related cflags... -pthread
checking for sched_get_priority_min... yes
checking thread related libraries... -pthread 
checking for localtime_r... yes
checking for gmtime_r... (cached) yes
checking for posix getpwuid_r... yes
checking for posix getgrgid_r... yes
checking size of pthread_t... 8
checking for pthread_attr_setstacksize... yes
checking for minimal/maximal thread priority... sched_get_priority_min(SCHED_OTHER)/sched_get_priority_max(SCHED_OTHER)
checking for pthread_setschedparam... yes
checking for posix yield function... sched_yield
checking size of pthread_mutex_t... 40
checking byte contents of PTHREAD_MUTEX_INITIALIZER... 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
checking for clock_gettime... no
checking for clock_gettime in -lrt... yes
checking for monotonic clocks... yes
checking whether to use assembler code for atomic operations... x86_64
checking whether GCC supports built-in atomic intrinsics... yes
checking for Win32 atomic intrinsics... no
checking for futex(2) system call... yes
checking for eventfd(2) system call... yes
checking value of POLLIN... 1
checking value of POLLOUT... 4
checking value of POLLPRI... 2
checking value of POLLERR... 8
checking value of POLLHUP... 16
checking value of POLLNVAL... 32
checking for broken poll... no
checking whether compiler understands -Wno-pointer-sign... yes
checking for EILSEQ... yes
checking for gtkdoc-check... /usr/bin/gtkdoc-check
checking for gtkdoc-rebase... /usr/bin/gtkdoc-rebase
checking for gtkdoc-mkpdf... /usr/bin/gtkdoc-mkpdf
checking whether to build gtk-doc documentation... no
checking whether to include dtrace tracing support... yes
checking for dtrace... no
checking whether to include systemtap tracing support... no
checking for DBUS1... yes
checking for -Bsymbolic-functions linker flag... yes
configure: creating ./config.status
config.status: creating glib-2.0.pc
config.status: creating glib-2.0-uninstalled.pc
config.status: creating gmodule-2.0.pc
config.status: creating gmodule-export-2.0.pc
config.status: creating gmodule-no-export-2.0.pc
config.status: creating gmodule-2.0-uninstalled.pc
config.status: creating gmodule-no-export-2.0-uninstalled.pc
config.status: creating gthread-2.0.pc
config.status: creating gthread-2.0-uninstalled.pc
config.status: creating gobject-2.0.pc
config.status: creating gobject-2.0-uninstalled.pc
config.status: creating gio-2.0.pc
config.status: creating gio-unix-2.0.pc
config.status: creating gio-windows-2.0.pc
config.status: creating gio-2.0-uninstalled.pc
config.status: creating gio-unix-2.0-uninstalled.pc
config.status: creating glib-zip
config.status: creating glib-gettextize
config.status: creating Makefile
config.status: creating build/Makefile
config.status: creating build/win32/Makefile
config.status: creating build/win32/dirent/Makefile
config.status: creating build/win32/vs9/Makefile
config.status: creating build/win32/vs10/Makefile
config.status: creating glib/Makefile
config.status: creating glib/glib.stp
config.status: creating glib/libcharset/Makefile
config.status: creating glib/gnulib/Makefile
config.status: creating glib/pcre/Makefile
config.status: creating glib/update-pcre/Makefile
config.status: creating glib/tests/Makefile
config.status: creating gmodule/Makefile
config.status: creating gmodule/gmoduleconf.h
config.status: creating gobject/Makefile
config.status: creating gobject/gobject.stp
config.status: creating gobject/glib-mkenums
config.status: creating gobject/tests/Makefile
config.status: creating gthread/Makefile
config.status: creating gthread/tests/Makefile
config.status: creating gio/Makefile
config.status: creating gio/gdbus-codegen/Makefile
config.status: creating gio/gdbus-codegen/config.py
config.status: creating gio/xdgmime/Makefile
config.status: creating gio/inotify/Makefile
config.status: creating gio/libasyncns/Makefile
config.status: creating gio/fen/Makefile
config.status: creating gio/fam/Makefile
config.status: creating gio/win32/Makefile
config.status: creating gio/tests/Makefile
config.status: creating gio/tests/gdbus-object-manager-example/Makefile
config.status: creating po/Makefile.in
config.status: creating docs/Makefile
config.status: creating docs/reference/Makefile
config.status: creating docs/reference/glib/Makefile
config.status: creating docs/reference/glib/version.xml
config.status: creating docs/reference/gobject/Makefile
config.status: creating docs/reference/gobject/version.xml
config.status: creating docs/reference/gio/Makefile
config.status: creating docs/reference/gio/gdbus-object-manager-example/Makefile
config.status: creating docs/reference/gio/version.xml
config.status: creating tests/Makefile
config.status: creating tests/gobject/Makefile
config.status: creating tests/refcount/Makefile
config.status: creating m4macros/Makefile
config.status: creating config.h
config.status: executing depfiles commands
config.status: executing default-1 commands
config.status: executing libtool commands
config.status: executing glib/glibconfig.h commands
config.status: executing chmod-scripts commands
bash-4.1$ 

[/COLOR][/B]
```[B][COLOR=Black]sorted this drives me NUTS ,,,, next run .....

```

  CC     libgobject_2_0_la-gvaluetypes.lo
  CCLD   libgobject-2.0.la
/usr/lib/libffi.so: could not read symbols: File in wrong format
collect2: ld returned 1 exit status
make[4]: *** [libgobject-2.0.la] Error 1
make[4]: Leaving directory `/home/keith/gnome-shell/source/glib/gobject'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/keith/gnome-shell/source/glib/gobject'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/keith/gnome-shell/source/glib/gobject'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/keith/gnome-shell/source/glib'
make: *** [all] Error 2
*** Error during phase build of glib: ########## Error running make   *** [1/45]

  [1] Rerun phase build
  [2] Ignore error and continue to install
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "configure"
  [8] Go to phase "clean"
  [9] Go to phase "distclean"
choice: 


```now if I move the /usr/lib to /usr/lib.BAK 
and back again
mv /usr/lib.BAK /usr/lib


.......... It will build again .....

This is CRAZY ...... but we have it built now ..........

I have a feeling this is to do with USER and SYSTEM privileges ,,, just a hunch,

```

make[3]: Leaving directory `/home/keith/gnome-shell/source/glib/docs'
make[2]: Leaving directory `/home/keith/gnome-shell/source/glib/docs'
make[1]: Leaving directory `/home/keith/gnome-shell/source/glib/docs'
*** Error during phase install of glib: Module failed to install into DESTDIR u'/home/keith/gnome-shell/install/_jhbuild/root-glib-broken' *** [1/45]

  [1] Rerun phase install
  [2] Ignore error and continue to next module
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
choice: 


```[http://www.geekazine.com/news/franks-thoughts/installing-slackware-linux-part-6-some-tips-and-tricks](http://www.geekazine.com/news/franks-thoughts/installing-slackware-linux-part-6-some-tips-and-tricks)

[/COLOR][/B][/COLOR]> 
**Using the GUI**
 Start the GUI from the command line with the command, &#8220;startx.&#8221;   Change the window manager from command line with the command,  &#8220;xwmconfig.&#8221;  (Once you are logged in, xwmconfig applies only to the  logged in user.)
 If you must boot directly into a GUI, log in as root, open a text editor, and [change the default runlevel in the file */etc/inittab* from &#8220;3&#8243; to &#8220;4.&#8221;]("http://humanreadable.nfshost.com/sdeg/dual_startup.htm")  

WHY ?

[http://genek.net/LinuxAdventures/sysadmin/slackconfig.html](http://genek.net/LinuxAdventures/sysadmin/slackconfig.html)
[COLOR=Red][B][COLOR=Black] 

SORTED PROBLEM 1 .......
_______________________________________

New Problem .......

```

/home/keith/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_cclosure_marshal_generic'
collect2: ld returned 1 exit status
linking of temporary binary failed: Command '['/bin/sh', '../../libtool', '--mode=link', '--tag=CC', '--silent', 'gcc', '-o', '/home/keith/gnome-shell/source/gobject-introspection/tests/scanner/tmp-introspectiSUzvR/Regress-1.0', '-export-dynamic', '-L.', 'libregress.la', '-pthread', '-L/home/keith/gnome-shell/install/lib64', '-lgio-2.0', '-lgobject-2.0', '-lgmodule-2.0', '-lgthread-2.0', '-lrt', '-lglib-2.0', '/home/keith/gnome-shell/source/gobject-introspection/tests/scanner/tmp-introspectiSUzvR/Regress-1.0.o']' returned non-zero exit status 1
make[4]: *** [Regress-1.0.gir] Error 1
make[4]: Leaving directory `/home/keith/gnome-shell/source/gobject-introspection/tests/scanner'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/keith/gnome-shell/source/gobject-introspection/tests'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/keith/gnome-shell/source/gobject-introspection/tests'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/keith/gnome-shell/source/gobject-introspection'
make: *** [all] Error 2
*** Error during phase build of gobject-introspection: ########## Error running make   *** [2/45]

  [1] Rerun phase build
  [2] Ignore error and continue to install
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "configure"
  [8] Go to phase "clean"
  [9] Go to phase "distclean"
choice: 


```Next stop here ...... 8/45 ...... gtk3

```

*** Configuring gtk3 *** [8/45]
./autogen.sh --prefix /home/keith/gnome-shell/install --libdir '/home/keith/gnome-shell/install/lib64'  --disable-static --disable-gtk-doc 
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal --force -I m4 ${ACLOCAL_FLAGS}
/usr/share/aclocal/imlib.m4:9: warning: underquoted definition of AM_PATH_IMLIB
/usr/share/aclocal/imlib.m4:9:   run info '(automake)Extending aclocal'
/usr/share/aclocal/imlib.m4:9:   or see http://sources.redhat.com/automake/automake.html#Extending-aclocal
autoreconf: configure.ac: tracing
autoreconf: configure.ac: creating directory build-aux
autoreconf: running: libtoolize --copy --force
libtoolize: putting auxiliary files in AC_CONFIG_AUX_DIR, `build-aux'.
libtoolize: copying file `build-aux/ltmain.sh'
libtoolize: putting macros in AC_CONFIG_MACRO_DIR, `m4'.
libtoolize: copying file `m4/libtool.m4'
libtoolize: copying file `m4/ltoptions.m4'
libtoolize: copying file `m4/ltsugar.m4'
libtoolize: copying file `m4/ltversion.m4'
libtoolize: copying file `m4/lt~obsolete.m4'
/usr/share/aclocal/imlib.m4:9: warning: underquoted definition of AM_PATH_IMLIB
/usr/share/aclocal/imlib.m4:9:   run info '(automake)Extending aclocal'
/usr/share/aclocal/imlib.m4:9:   or see http://sources.redhat.com/automake/automake.html#Extending-aclocal
autoreconf: running: /usr/bin/autoconf --force
autoreconf: running: /usr/bin/autoheader --force
autoreconf: running: automake --add-missing --copy --force-missing
configure.ac:137: installing `build-aux/config.guess'
configure.ac:137: installing `build-aux/config.sub'
configure.ac:65: installing `build-aux/install-sh'
configure.ac:65: installing `build-aux/missing'
demos/gtk-demo/Makefile.am: installing `build-aux/depcomp'
gdk/Makefile.am:183: HAVE_INTROSPECTION does not appear in AM_CONDITIONAL
gtk/Makefile.am:1002: HAVE_INTROSPECTION does not appear in AM_CONDITIONAL
autoreconf: automake failed with exit status: 1
*** Error during phase configure of gtk3: ########## Error running ./autogen.sh --prefix /home/keith/gnome-shell/install --libdir '/home/keith/gnome-shell/install/lib64'  --disable-static --disable-gtk-doc  *** [8/45]

  [1] Rerun phase configure
  [2] Ignore error and continue to build
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "clean"
  [8] Go to phase "distclean"
choice: --


``````

checking whether build environment is sane... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for BASE_DEPENDENCIES... no
configure: error: Package requirements (glib-2.0 >= 2.29.14    atk >= 1.30    pango >= 1.29.0    cairo >= 1.10.0    cairo-gobject >= 1.10.0    gdk-pixbuf-2.0 >= 2.23.5) were not met:

Requested 'glib-2.0 >= 2.29.14' but version of GLib is 2.28.6
Requested 'pango >= 1.29.0' but version of Pango is 1.28.4
Requested 'gdk-pixbuf-2.0 >= 2.23.5' but version of GdkPixbuf is 2.23.3

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BASE_DEPENDENCIES_CFLAGS
and BASE_DEPENDENCIES_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
bash-4.1$ 


```Requested 'glib-2.0 >= 2.29.7' but version of GLib is 2.28.6

ok so first .... why is it building an older version ,,,, than the one I need ?

Where do we get the latest from ...... time to go hunt it down ...... >>>

[[COLOR=Red]http://www.google.com/search?client=ubuntu&channel=fs&q=%27glib-2.0+%3E%3D+2.29.7&ie=utf-8&oe=utf-8[/COLOR]]("http://www.google.com/search?client=ubuntu&channel=fs&q=%27glib-2.0+%3E%3D+2.29.7&ie=utf-8&oe=utf-8")

[https://launchpad.net/ubuntu/oneiric/amd64/gir1.2-glib-2.0/1.29.0-0ubuntu1](https://launchpad.net/ubuntu/oneiric/amd64/gir1.2-glib-2.0/1.29.0-0ubuntu1)

[http://pkgs.org/package/gir1.2-glib-2.0](http://pkgs.org/package/gir1.2-glib-2.0)


Interestingthread

[http://www.linuxquestions.org/questions/slackware-14/error-compiling-compiz-plugins-with-alien-bobs-multilib-packages-installed-885793/](http://www.linuxquestions.org/questions/slackware-14/error-compiling-compiz-plugins-with-alien-bobs-multilib-packages-installed-885793/)


__________________________________________________________

So lets reduce the problems ...... lols ..... lets make it 64bit and 32bit ...... then it cannot go wrong .... ;)

Slackware 13.37 Multilib

[http://connie.slackware.com/~alien/multilib/13.37/]("http://connie.slackware.com/%7Ealien/multilib/13.37/")

I am having second thoughts here as these are all older packages ...... 

I want to only install the latest packages needed to get Gnome - Shell working .....

or ? ( Gnome - Shell will work on older packages - just not the latest compiled version )

Ok from what I have read - we cannot use .deb files ....

so need to compile the latest source code for glib ....... which is where exactly .. ?

[http://archive.ubuntu.com/ubuntu/pool/main/g/gobject-introspection/gobject-introspection_1.29.16.orig.tar.bz2](http://archive.ubuntu.com/ubuntu/pool/main/g/gobject-introspection/gobject-introspection_1.29.16.orig.tar.bz2)

[http://archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/glib2.0_2.29.14.orig.tar.bz2](http://archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/glib2.0_2.29.14.orig.tar.bz2)

[[COLOR=Red]_*FULLSIZE Screenshot - Glib 2.29.14 now installed*_[/COLOR]]("http://img809.imageshack.us/img809/3606/screenshot1jt.jpg")
[/COLOR] [/B][/COLOR]

---

### Post by 23dornot23d on 2011-08-15
[COLOR=Blue]**Its a clean run now through all the other modules though ....**[/COLOR]

Ok another day a little further not much - but its another problem solved ....

But another problem gained 

**Problem 4**
(8/45)

```

  CC     gdkdevice.lo
  CC     gdkdevicemanager.lo
  CC     gdkdisplay.lo
  CC     gdkdisplaymanager.lo
  CC     gdkdnd.lo
  CC     gdkevents.lo
  CC     gdkglobals.lo
  CC     gdkkeys.lo
  CC     gdkkeyuni.lo
  CC     gdkoffscreenwindow.lo
  CC     gdkpango.lo
  CC     gdkpixbuf-drawable.lo
  CC     gdkrectangle.lo
  CC     gdkrgba.lo
  CC     gdkscreen.lo
  CC     gdkselection.lo
  CC     gdkvisual.lo
  CC     gdkwindow.lo
  CC     gdkwindowimpl.lo
  CC     gdkenumtypes.lo
  CC     gdkmarshalers.lo
  CCLD   libgdk-3.la
  GISCAN Gdk-3.0.gir
[COLOR=Red]**Couldn't find include 'GdkPixbuf-2.0.gir' (search path: ['../gdk', '/home/keith/gnome-shell/install/share/gir-1.0', '/usr/share/gir-1.0', '/home/keith/gnome-shell/install/share/gir-1.0', '/usr/share/gir-1.0', '/home/keith/gnome-shell/install/share/gir-1.0'])**[/COLOR]
make[4]: *** [Gdk-3.0.gir] Error 1
make[4]: Leaving directory `/home/keith/gnome-shell/source/gtk3/gdk'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/keith/gnome-shell/source/gtk3/gdk'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/keith/gnome-shell/source/gtk3/gdk'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/keith/gnome-shell/source/gtk3'
make: *** [all] Error 2
*** Error during phase build of gtk3: ########## Error running make   *** [8/45]

  [1] Rerun phase build
  [2] Ignore error and continue to install
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "configure"
  [8] Go to phase "clean"
  [9] Go to phase "distclean"
choice: 


```

---

### Post by sffvba[e0rt on 2011-08-15
Just a thought (seeing that there hasn't been that much "assistance" here)...

linuxquestions.org has the official Slackware forum... [http://www.linuxquestions.org/questions/slackware-14/](http://www.linuxquestions.org/questions/slackware-14/)

Have you tried there?


404

---

### Post by 23dornot23d on 2011-08-15
Cheers for that link "not found"

I am looking all over the net for files and similar scenarios ....

I just found this one too but it only goes to 13.1 

[http://www.linuxpackages.net/howto.php](http://www.linuxpackages.net/howto.php)

and the new release is 13.37

If you see anything in the way I am going about this to be odd or wrong

feel free to comment ..... I am not sure about setting up pointers or links to the

libraries I have so far managed to install ..... 

[COLOR=Red]**Will have a look here ,,, next time I am using slackware ... tomorrow night possibly  ...**[/COLOR]
> 
If you ever happen to want to link against installed libraries in a given directory, LIBDIR, you must either use libtool, and specify the full pathname of the library, or use the `-LLIBDIR' flag during linking and do at least one of the following:    - add LIBDIR to the `LD_LIBRARY_PATH' environment variable      during execution    - add LIBDIR to the `LD_RUN_PATH' environment variable      during linking    - use the `-Wl,--rpath -Wl,LIBDIR' linker flag    - have your system administrator add LIBDIR to `/etc/ld.so.conf'  See any operating system documentation about shared libraries for more information, such as the ld(1) and ld.so(8) manual pages.
I am sort of hoping the gnome-shell

script looks after a lot of that ..... 

Ok cheers - will look at that link now ......ty  ;)


I keep going onto linux forums .... on specific things I am searching for .... it has helped me
quite a lot so far ...... maybe if I come to a dead end here , I will post some questions there.

For the time being its just something that intrigues me ..... and I would love to get Gnome-Shell
working in Slackware .... 13.37 ....

ok New problem .... one step backwards today ......

**Problem 5** 
(7/45)

Although I manged to get through this the other day by upgrading a package ..... it now complains
that I have left the old one there .....

So how do I remove it ... properly ..... it was installed by the system the original one ..... ?
I compiled the newer version ......

```

checking for the BeOS... no
checking for HP-UX... no
checking for extra flags for POSIX compliance... none needed
checking for pkg-config... (cached) /usr/bin/pkg-config
checking pkg-config is at least version 0.16... yes
[COLOR=Blue]**checking for GLIB - version >= 2.27.2.**[/COLOR].. 
*** '[COLOR=Red]**pkg-config --modversion glib-2.0' returned 2.28.6, but GLIB (2.29.14)**[/COLOR]
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error: 
*** GLIB 2.27.2 or better is required. The latest version of
*** GLIB is always available from ftp://ftp.gtk.org/pub/gtk/.
bash-4.1$ pkg-config --modversion glib-2.0
2.28.6
bash-4.1$ 


```Why does ldconfig not do anything .... ?
Why is it asking me if PKG_CONFIG_PATH is wrong ... ? ( when it worked on everything else ok )
Why doesn't it just use the latest version ...... ?




So I need to remove [COLOR=Blue][B]GLIB - version >= 2.27.2
so is it easy and will my sytem still work if I do it ?

[/B][COLOR=Black][http://englanders.us/~jason/howtos.php?howto=glib]("http://englanders.us/%7Ejason/howtos.php?howto=glib")

[/COLOR][/COLOR]see the bottom of the link for the answer .....

and lets find a recovery too ... just in case something goes wrong ...
[http://rlworkman.net/howtos/glibc-recovery](http://rlworkman.net/howtos/glibc-recovery)

So even after taking as many precautions as needed. ......

we now have ,,,, no glibc ....
we also cannot mount the cdrom to get us back to where we started  - not that that is where I want to go
so after installing the new version of glibc ..... why is it not seeing it .....

Well the good news is we are able to use 

slapt-get --install clutter
slapt-get --install glib

etc .....

---

### Post by 23dornot23d on 2011-08-17
Another day a little further ...... and its so easy to re-install over the top of the existing one retaining everything the way you had it set up ......
and also adding more to it ......

I am quite liking this now ......

[IMG]http://img26.imageshack.us/img26/8104/screenshotoz.jpg[/IMG]


So now I have 2 users 

[IMG]http://img850.imageshack.us/img850/3650/screenshot2eg.jpg[/IMG]

and all of my disks and cdrom/dvd mounted ....... so now I can make some space by moving the Gnome-Shell source files over to another drive ......


Options we love options ....

[IMG]http://img197.imageshack.us/img197/9071/optionse.jpg[/IMG]

---

### Post by cbowman57 on 2011-08-17
Wow, you've made a lot of progress.

---

### Post by 23dornot23d on 2011-08-17
Lols ..... not really ..... 5 steps forwards and one step backwards most of the time here .....
or is it the other way around ? but it is a challenge ..... and I do like challenges .....
 this may be a bit above my station .....

but already have learned a few new things about the system ....

I suppose it depends how deep we dig ...... but there are more worms deeper down .... 
whatever you do if you use this ......

Do not remove Glibc ...... :lolflag:

I just did ..... and luckily a re-install without formatting brought me back to where I left off
so [COLOR=Red]**first mistake **[/COLOR]....... and I am sure I will make many more ......

I have been through the full build to try to get an idea of the problems I will face .....
this is going to take some time ...... especially the speed  I go ..... old and slow ... :D

---

### Post by cbowman57 on 2011-08-17
:lol:  I bet it is a learning experience.

---

### Post by 23dornot23d on 2011-08-17
One thing I found fascinating tonight was 

slapt-get --dist-upgrade

I am at version 13.37

The packagemanager ...... or whatever slapt-get is ...... looks in a area at 13.1 version of said distro
and starts pulling in files from there ......

So I believe I just downgraded ........ [COLOR=Red]**so mistake 2**[/COLOR] ...... do not think because it says upgrade ;)
that is what you will get ....... 

( each time you mess up with this you seem to loose GUI .... so it is CLI only most of the time now )

So its re-install time yet again ........ ( take 2 ) ...... this Distro could grow on me yet ...... lols .... :D

After a rebuild in User2 ..... I got to 12/45 without any major errors ..... amazingly .....

Have to wait a while while it re-inserts the packages again ..... to see where we are now ...

[URL="http://repository.slacky.eu/slackware-12.2/libraries/libffi/3.0.8/"]
[/URL]

---

### Post by sffvba[e0rt on 2011-08-17
OK... Slack time again... I won't be trying what you are doing... But I will marvel at the prettyness of KDE 4.7 from a Slackware 13.37 install... BBL (Got some installing to do :KS)


404

Curses... will this distro-hopping never cease...

---

### Post by 23dornot23d on 2011-08-17
Not sure whats happening here at the moment 

[IMG]http://img41.imageshack.us/img41/4339/screenshot4ra.jpg[/IMG]

Chances of a working system ..... :confused:

I had KDE 4.7 working earlier tonight on here .... its a little slow on my desktop machine
but has all the nice effects once its going .... the transparency and blue glow around the windows
as well as a lot of other things too ..... 

[IMG]http://img6.imageshack.us/img6/4599/snapshot2v.jpg[/IMG]

I have had Gnome-Shell and KDE working together in the same environment in the past ..... will be interesting to see
if I ever get it working on Slackware ..... but it wont be this week ......

[IMG]http://img263.imageshack.us/img263/6689/gnomep.jpg[/IMG]



Lets see if we can add Gnome Tweak Tool  

[http://ftp.dk.debian.org/gsb/gsb64-3.0_slackware64-13.37/extra/gnome-tweak-tool/](http://ftp.dk.debian.org/gsb/gsb64-3.0_slackware64-13.37/extra/gnome-tweak-tool/)

Where is slapt-get 

[http://pkgs.org/download/slackware-13.1/gnome-slackbuild-2.30-gsb-x86_64/slapt-get-0.10.2e-x86_64-1gsb.txz.html](http://pkgs.org/download/slackware-13.1/gnome-slackbuild-2.30-gsb-x86_64/slapt-get-0.10.2e-x86_64-1gsb.txz.html)

```

bash-4.1# installpkg /root/Desktop/slapt-get-0.10.2e-x86_64-1gsb.txz
Verifying package slapt-get-0.10.2e-x86_64-1gsb.txz.
Installing package slapt-get-0.10.2e-x86_64-1gsb.txz:
PACKAGE DESCRIPTION:
# slapt-get (an Apt-like front-end to Slackware's pkgtools)
#
# slapt-get is an apt-like front-end to Slackware's pkgtools.
# It allows you to install/upgrade/uninstall packages using 
# "repositories" (very similar to the way Debian does it). 
#  
# slapt-get is required by GSB for some of the installer functions.
#
# slapt-get was written by the amazing Jason Woodward:
#   <http://software.jaos.org>
#
Executing install script for slapt-get-0.10.2e-x86_64-1gsb.txz.
Package slapt-get-0.10.2e-x86_64-1gsb.txz installed.


bash-4.1# slapt-get
slapt-get - Jason Woodward <woodwardj at jaos dot org>
An implementation of the Debian APT system to Slackware
Usage:
slapt-get [option(s)] [target]

Targets:
  --update|-u    - retrieves pkg data from MIRROR
  --upgrade      - upgrade installed pkgs
  --dist-upgrade - upgrade to newer release
  --install|-i   [pkg name(s)] - install specified pkg(s)
  --install-set  [disk set(s)] - install specified disk set(s)
  --remove       [pkg name(s)] - remove specified pkg(s)
  --show         [pkg name] - show pkg description
  --filelist     [pkg name] - show pkg installed files
  --search       [expression] - search available pkgs
  --list         - list pkgs
  --available    - list available pkgs
  --installed    - list installed pkgs
  --clean        - purge cached pkgs
  --autoclean    - only purge cache of older, unreacheable pkgs
  --add-keys     - retrieve GPG keys for sources
  --version      - print version and license info

Options:
  --download-only|-d  - only download pkg on install/upgrade
  --simulate|-s       - show pkgs to be installed/upgraded
  --no-prompt|-y      - do not prompt during install/upgrade
  --prompt|-p         - always prompt during install/upgrade
  --reinstall         - re-install the pkg
  --ignore-excludes   - install/upgrade excludes
  --no-md5            - do not perform md5 check sum
  --no-dep            - skip dependency check
  --ignore-dep        - ignore dependency failures
  --print-uris        - print URIs only, do not download
  --show-stats|-S     - show download statistics
  --config|-c []      - specify alternate slapt-getrc location
  --remove-obsolete   - remove obsolete packages
  --retry []          - specify number of download retry attempts
  --no-upgrade        - install package, do not attempt to upgrade
bash-4.1# 


``````

bash-4.1# installpkg /root/Desktop/gnome-tweak-tool-3.0.3-x86_64-1gsb.txz
Verifying package gnome-tweak-tool-3.0.3-x86_64-1gsb.txz.
Installing package gnome-tweak-tool-3.0.3-x86_64-1gsb.txz:
PACKAGE DESCRIPTION:
# gnome-tweak-tool (gnome shell configuration tool)
#
# gnome-tweak-tool is a nifty configuration tool which allows you to 
# easily change themes, fonts, and other aspects of the GNOME shell.
#
Executing install script for gnome-tweak-tool-3.0.3-x86_64-1gsb.txz.
Package gnome-tweak-tool-3.0.3-x86_64-1gsb.txz installed.

bash-4.1# 


``````

bash-4.1# gnome-tweak-tool
Traceback (most recent call last):
  File "/usr/bin/gnome-tweak-tool", line 20, in <module>
    import gi
ImportError: No module named gi
bash-4.1# 


```[http://ftp.dk.debian.org/gsb/gsb64-3.0_slackware64-13.37/](http://ftp.dk.debian.org/gsb/gsb64-3.0_slackware64-13.37/)

[http://ftp.dk.debian.org/gsb/gsb64-3.0_slackware64-13.37/gsb64/a/](http://ftp.dk.debian.org/gsb/gsb64-3.0_slackware64-13.37/gsb64/a/)

```

bash-4.1# installpkg /root/Desktop/gnome-shell-extensions-3.0.0-noarch-1gsb.txzVerifying package gnome-shell-extensions-3.0.0-noarch-1gsb.txz.
Installing package gnome-shell-extensions-3.0.0-noarch-1gsb.txz:
PACKAGE DESCRIPTION:
# gnome-shell-extensions (GNOME shell extensions)
#
# GNOME Shell Extensions is a collection of extensions providing 
# additional and optional functionality to GNOME Shell.
#
Package gnome-shell-extensions-3.0.0-noarch-1gsb.txz installed.

bash-4.1# installpkg /root/Desktop/gnome-shell-3.0.1-x86_64-2gsb.txz
Verifying package gnome-shell-3.0.1-x86_64-2gsb.txz.
Installing package gnome-shell-3.0.1-x86_64-2gsb.txz:
PACKAGE DESCRIPTION:
# gnome-shell (GNOME shell)
#
# gnome-shell provides the core compositing user interface functions 
# for the GNOME 3 desktop, like switching to windows and launching 
# applications. GNOME Shell takes advantage of the capabilities of 
# modern graphics hardware and introduces innovative user interface 
# concepts to provide an attractive and easy-to-use experience.
#
Executing install script for gnome-shell-3.0.1-x86_64-2gsb.txz.
Package gnome-shell-3.0.1-x86_64-2gsb.txz installed.

bash-4.1# gnome-shell --replace
gnome-shell: error while loading shared libraries: libmutter.so.0: cannot open shared object file: No such file or directory
bash-4.1# installpkg /root/Desktop/mutter-3.0.1-x86_64-1gsb.txz
Verifying package mutter-3.0.1-x86_64-1gsb.txz.
Installing package mutter-3.0.1-x86_64-1gsb.txz:
PACKAGE DESCRIPTION:
# mutter (metacity with clutter extensions)
#
# mutter is a fork of the Metacity window manager which supports
# compositing through clutter. 
#
# 
Executing install script for mutter-3.0.1-x86_64-1gsb.txz.
Package mutter-3.0.1-x86_64-1gsb.txz installed.

bash-4.1# gnome-shell --replace
gnome-shell: error while loading shared libraries: libcanberra-gtk3.so.0: cannot open shared object file: No such file or directory
bash-4.1# 


```

```

bash-4.1# gnome-shell --replace
gnome-shell: error while loading shared libraries: libmutter.so.0: cannot open shared object file: No such file or directory
bash-4.1# installpkg /root/Desktop/mutter-3.0.1-x86_64-1gsb.txz
Verifying package mutter-3.0.1-x86_64-1gsb.txz.
Installing package mutter-3.0.1-x86_64-1gsb.txz:
PACKAGE DESCRIPTION:
# mutter (metacity with clutter extensions)
#
# mutter is a fork of the Metacity window manager which supports
# compositing through clutter. 
#
# 
Executing install script for mutter-3.0.1-x86_64-1gsb.txz.
Package mutter-3.0.1-x86_64-1gsb.txz installed.

bash-4.1# gnome-shell --replace
gnome-shell: error while loading shared libraries: libcanberra-gtk3.so.0: cannot open shared object file: No such file or directory
bash-4.1# installpkg /root/Desktop/libcanberra-0.28-x86_64-1gsb.txz
Verifying package libcanberra-0.28-x86_64-1gsb.txz.
Installing package libcanberra-0.28-x86_64-1gsb.txz:
PACKAGE DESCRIPTION:
# libcanberra (Freedesktop.org Sound Theme Specification Library)
#
# libcanberra is an implementation of the XDG Sound Theme and Name 
# Specifications, for generating event sounds on free desktops, such as 
# GNOME. It comes with several backends (ALSA, PulseAudio, null) and is 
# designed to be portable.
#
Executing install script for libcanberra-0.28-x86_64-1gsb.txz.
Package libcanberra-0.28-x86_64-1gsb.txz installed.

bash-4.1# gnome-shell --replace
gnome-shell: error while loading shared libraries: libgjs.so.0: cannot open shared object file: No such file or directory
bash-4.1# 


```

---

### Post by 23dornot23d on 2011-08-19
Ok I have now got a routine for installing packages ....

There may still be a better way ...... but this is what I am doing now ....

Go into Firefox ...... go to the online directory of txz files you need ......

[http://ftp.dk.debian.org/gsb/gsb64-3.0_slackware64-13.37/gsb64/a/](http://ftp.dk.debian.org/gsb/gsb64-3.0_slackware64-13.37/gsb64/a/)

[IMG]http://img88.imageshack.us/img88/4059/screenshot11wd.jpg[/IMG]

select and download each of the  txz files into your home directory

[IMG]http://img64.imageshack.us/img64/1714/screenshot10pkg.jpg[/IMG]


Next in a terminal from your home directory  type in

pkgtool

next just go through them installing from current directory .......

once done move on to the next one ( but first remove or store the already downloaded one somewhere else - or it will go through them again )

so the next directory
[http://ftp.dk.debian.org/gsb/gsb64-3.0_slackware64-13.37/gsb64/ac/](http://ftp.dk.debian.org/gsb/gsb64-3.0_slackware64-13.37/gsb64/ac/)

[IMG]http://img685.imageshack.us/img685/7277/screenshot13gnometweakt.jpg[/IMG]

---

### Post by FormatSeize on 2011-08-19
> **not found said:**
> OK... Slack time again... I won't be trying what you are doing... But I will marvel at the prettyness of KDE 4.7 from a Slackware 13.37 install.

It is quite wonderful, isn't it?
 
As for the building of Gnome Shell in Slackware, I've thought about it, but never got around to trying it. When I do get around to doing it, though, I probably will go the avenue of installing the bare minimum SalixOS, and then going from there.

---

### Post by 23dornot23d on 2011-08-19
> 
As for the building of Gnome Shell in Slackware, I've thought about it,  but never got around to trying it. When I do get around to doing it,  though, I probably will go the avenue of installing the bare minimum  SalixOS, and then going from there.
You should give it a try ..... its good fun ..... and the rewards may not seem a lot ....
but they are .....

I got this today and am feeling quite confident now ..... ( even though it does not look to be much .... the windows and applications are functional ...... just seem to be missing icons and
text now ...... small details ..... ;)

[IMG]http://img856.imageshack.us/img856/7303/gs1s.jpg[/IMG]

I still have XFCE fully functional and KDE too ...... so two fallback desktops .....

Normal Gnome has gone for the time being ..... and I get a warning that I cannot use GTK 2 and GTK 3
together ......

This seems similar to the Glibc problem I had earlier ..... how do you just remove one and leave the other functioning

anybody that knows ...... write the answer on the back of a stamp and mail it to me ...... please ..... ;)

It got similar problems to what I always get to start with the Adwaita theme is missing ...... ( do they remove this on purpose )

can't it be included automatically ...... 

I have a copy but is that the right thing to keep doing ...... unzip it into /home/.themes/


So the steps to re-create what I have done .....

1 .... Install a fresh copy of the 64 bit Slackware 13.37 Full 
2 .... Install [COLOR=Red]_***[Gnome 2.30 ]("http://gnomeslackbuild.org/")***_[/COLOR]using the lynx command
3 .... Install all the Gnome Shell Packages that you can find for Slackware
4 .... Use jhbuild to compile and update everything ......... 

( although this does not work yet fully .....due to libffi - gnome-common and gobject-introspection problems )
while all the above can be downloaded as source files and compiled ...... slackware versions would be better .....

I am sure in 6 weeks time that some of the packages will become available as Gnome-Shell schedule 
closes in for the release of 3.2 ....

So hopefully having this ready and available ..... with all the small little quirks sorted ..... we should be
able to build Gnome-Shell ......

I am still trying at the moment and will post the errors that I now have ....... 

I will do a clean install too in a New User Profile that I will set up ...... to try to get everything as clean as I can
and only using the slackware packages if at all possible .......

[http://www.slackware.com/config/packages.php](http://www.slackware.com/config/packages.php)

```

  CC     librsvg_2_la-rsvg-file-util.lo
  CCLD   librsvg-2.la
  CC     rsvg_convert-rsvg-convert.o
  CCLD   rsvg-convert
/home/keith2/gnome-shell/install/lib64/libgobject-2.0.so: undefined reference to `g_datalist_get_data'
/home/keith2/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_variant_take_ref'
/home/keith2/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_variant_new_objv'
/home/keith2/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_unix_set_fd_nonblocking'
/home/keith2/gnome-shell/install/lib64/libgobject-2.0.so: undefined reference to `g_match_info_unref'
/home/keith2/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_variant_dup_objv'
/home/keith2/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_unix_open_pipe'
/home/keith2/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_time_zone_refresh_local'
/home/keith2/gnome-shell/install/lib64/libgobject-2.0.so: undefined reference to `g_match_info_ref'
collect2: ld returned 1 exit status
make[2]: *** [rsvg-convert] Error 1
make[2]: Leaving directory `/home/keith2/gnome-shell/source/librsvg'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/keith2/gnome-shell/source/librsvg'
make: *** [all] Error 2
*** Error during phase build of librsvg: ########## Error running make   *** [9/45]

  [1] Rerun phase build
  [2] Ignore error and continue to install
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "configure"
  [8] Go to phase "clean"
  [9] Go to phase "distclean"
choice: 


```ok so look for a download of the librsvg

[http://pkgs.org/slackware-13.37/slackware-x86_64/librsvg-2.32.0-x86_64-1.txz.html](http://pkgs.org/slackware-13.37/slackware-x86_64/librsvg-2.32.0-x86_64-1.txz.html)


one more thing just so I remember I disable Gnome online accounts here

```

checking if GNOME Online Accounts support is enabled... yes
checking for GOA... no
configure: error: goa-1.0 not found (or version < 3.1.1),
    If you want to disable GNOME Online Accounts support,
    please append --disable-goa to configure.
*** Error during phase configure of evolution-data-server: ########## Error running ./autogen.sh --prefix /home/keith2/gnome-shell/install --libdir '/home/keith2/gnome-shell/install/lib64'  --disable-static --disable-gtk-doc  *** [22/45]

  [1] Rerun phase configure
  [2] Ignore error and continue to build
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "clean"
  [8] Go to phase "distclean"
choice: 4
exit shell to continue with build
bash-4.1$ ./configure --disable-goa
checking for a BSD-compatible install... /usr/local/bin/ginstall -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /usr/local/bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
checking for style of include used by make... GNU
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for supported compiler flags...  -DPANGO_DISABLE_DEPRECATED -DGDK_PIXBUF_DISABLE_DEPRECATED -DG_DISABLE_SINGLE_INCLUDES -DGTK_DISABLE_SINGLE_INCLUDES -DGSEAL_ENABLE -Wall -Wextra -Wno-missing-field-initializers -Wno-sign-compare -Wno-unused-parameter -Wdeclaration-after-statement -Werror-implicit-function-declaration -Wformat-security -Winit-self -Wmissing-declarations -Wmissing-include-dirs -Wmissing-noreturn -Wnested-externs -Wpointer-arith -Wredundant-decls -Wundef -Wwrite-strings
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for inline... inline
checking whether gcc and cc understand -c and -o together... yes
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking for flex... flex
checking lex output file root... lex.yy
checking lex library... -lfl
checking whether yytext is a pointer... yes
checking for bison... bison -y
checking for jw... /usr/bin/jw
checking whether NLS is requested... yes
checking for intltool >= 0.35.5... 0.41.1 found
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for perl >= 5.8.1... 5.12.3
checking for XML::Parser... ok
checking for msgfmt... (cached) /usr/bin/msgfmt
checking for gmsgfmt... (cached) /usr/bin/msgfmt
checking for xgettext... (cached) /usr/bin/xgettext
checking for msgmerge... (cached) /usr/bin/msgmerge
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for ld used by GCC... /usr/x86_64-slackware-linux/bin/ld
checking if the linker (/usr/x86_64-slackware-linux/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking how to print strings... printf
checking for a sed that does not truncate output... /usr/local/bin/sed
checking for grep that handles long lines and -e... /usr/local/bin/grep
checking for egrep... /usr/local/bin/grep -E
checking for fgrep... /usr/local/bin/grep -F
checking for ld used by gcc... /usr/x86_64-slackware-linux/bin/ld
checking if the linker (/usr/x86_64-slackware-linux/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking how to convert x86_64-unknown-linux-gnu file names to x86_64-unknown-linux-gnu format... func_convert_file_noop
checking how to convert x86_64-unknown-linux-gnu file names to toolchain format... func_convert_file_noop
checking for /usr/x86_64-slackware-linux/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for dlltool... no
checking how to associate runtime and link libraries... printf %s\n
checking for ar... ar
checking for archiver @FILE support... @
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for sysroot... no
checking for mt... mt
checking if mt is a manifest tool... no
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
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/x86_64-slackware-linux/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for gtkdoc-check... /usr/bin/gtkdoc-check
checking for gtkdoc-rebase... /usr/bin/gtkdoc-rebase
checking for gtkdoc-mkpdf... /usr/bin/gtkdoc-mkpdf
checking whether to build gtk-doc documentation... no
checking for Win32... no
checking for sys/wait.h that is POSIX.1 compatible... yes
checking for size_t... yes
checking for working alloca.h... yes
checking for alloca... yes
checking for fsync... yes
checking for strptime... yes
checking for strtok_r... yes
checking for nl_langinfo... yes
checking for GNOME_PLATFORM... yes
checking if GNOME Online Accounts support is enabled... no
checking for GNOME_KEYRING... yes
checking for regexec... yes
checking Berkeley DB... yes
checking for iconv in -liconv... no
checking for iconv... yes
checking for gnu_get_libc_version... yes
checking if iconv() handles UTF-8... yes
checking preferred charset name formats for system iconv... found
checking for nl_langinfo (CODESET)... yes
checking for %l and %k support in strftime... yes
checking Mozilla NSPR pkg-config module name... nspr
checking Mozilla NSS pkg-config module name... nss
checking for sendmail... /usr/sbin/sendmail
checking system mail directory... /var/spool/mail, world writable
checking for tm_gmtoff in struct tm... yes
checking if ctime_r wants three arguments... no
checking for gethostbyname_r... yes
checking if gethostbyname_r wants five arguments... no
checking for gethostbyaddr_r... yes
checking if gethostbyaddr_r wants seven arguments... no
checking for sys/statvfs.h... yes
checking for statvfs... yes
checking for sys/param.h... yes
checking for sys/mount.h... yes
checking for statfs... yes
checking if system supports getaddrinfo and getnameinfo... yes
checking wspiapi.h usability... no
checking wspiapi.h presence... no
checking for wspiapi.h... no
checking if we should build the calendar... yes
checking if we should build the weather calendar backend... yes
checking for LIBGWEATHER... yes
checking for SunOS broken spool format... no
checking for Kerberos 5... no
checking for et/com_err.h... yes
checking for com_err.h... no
checking for purify... impure
checking for OpenLDAP... no
checking for SunLDAP... no
checking for pkg-config... (cached) /usr/bin/pkg-config
checking pkg-config is at least version 0.16... yes
checking for GLIB - version >= 2.0.0... yes (version 2.29.17)
checking for SQLITE3... yes
checking for E_DATA_SERVER... yes
checking for E_DATA_SERVER_UI... yes
checking for E_BACKEND... yes
checking for EVOLUTION_ADDRESSBOOK... yes
checking for EVOLUTION_CALENDAR... yes
checking ical_set_unknown_token_handling_setting function... no
checking for GDATA... yes
checking for SOUP... yes
checking for deflateEnd in -lz... yes
checking zlib.h usability... yes
checking zlib.h presence... yes
checking for zlib.h... yes
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... no
checking for _LARGEFILE64_SOURCE value needed for large files... yes
checking for CAMEL... yes
checking for gconftool-2... /usr/bin/gconftool-2
Using config source xml:merged:/home/keith2/gnome-shell/install/etc/gconf/gconf.xml.defaults for schema installation
Using $(sysconfdir)/gconf/schemas as install directory for schema files
checking for gperf... /usr/bin/gperf
checking for gobject-introspection... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating evolution-data-server-zip
config.status: creating evolution-data-server.pc
config.status: creating addressbook/Makefile
config.status: creating addressbook/libebook/Makefile
config.status: creating addressbook/libebook/libebook.pc
config.status: creating addressbook/libedata-book/Makefile
config.status: creating addressbook/libedata-book/libedata-book.pc
config.status: creating addressbook/libegdbus/Makefile
config.status: creating addressbook/backends/Makefile
config.status: creating addressbook/backends/file/Makefile
config.status: creating addressbook/backends/vcf/Makefile
config.status: creating addressbook/backends/ldap/Makefile
config.status: creating addressbook/backends/google/Makefile
config.status: creating addressbook/backends/webdav/Makefile
config.status: creating art/Makefile
config.status: creating calendar/Makefile
config.status: creating calendar/libecal/Makefile
config.status: creating calendar/libecal/libecal.pc
config.status: creating calendar/libedata-cal/Makefile
config.status: creating calendar/libedata-cal/libedata-cal.pc
config.status: creating calendar/libegdbus/Makefile
config.status: creating calendar/backends/Makefile
config.status: creating calendar/backends/caldav/Makefile
config.status: creating calendar/backends/file/Makefile
config.status: creating calendar/backends/http/Makefile
config.status: creating calendar/backends/contacts/Makefile
config.status: creating calendar/backends/weather/Makefile
config.status: creating camel/Makefile
config.status: creating camel/providers/Makefile
config.status: creating camel/providers/imap/Makefile
config.status: creating camel/providers/imapx/Makefile
config.status: creating camel/providers/local/Makefile
config.status: creating camel/providers/nntp/Makefile
config.status: creating camel/providers/pop3/Makefile
config.status: creating camel/providers/sendmail/Makefile
config.status: creating camel/providers/smtp/Makefile
config.status: creating camel/tests/Makefile
config.status: creating camel/tests/folder/Makefile
config.status: creating camel/tests/lib/Makefile
config.status: creating camel/tests/message/Makefile
config.status: creating camel/tests/mime-filter/Makefile
config.status: creating camel/tests/misc/Makefile
config.status: creating camel/tests/smime/Makefile
config.status: creating camel/camel.pc
config.status: creating camel/camel-provider.pc
config.status: creating libebackend/Makefile
config.status: creating libebackend/libebackend.pc
config.status: creating libedataserver/Makefile
config.status: creating libedataserver/eds-version.h
config.status: creating libedataserver/libedataserver.pc
config.status: creating libedataserverui/Makefile
config.status: creating libedataserverui/libedataserverui.pc
config.status: creating tests/Makefile
config.status: creating tests/libebook/Makefile
config.status: creating tests/libebook/client/Makefile
config.status: creating tests/libebook/vcard/Makefile
config.status: creating tests/libecal/Makefile
config.status: creating tests/libecal/client/Makefile
config.status: creating tests/libedata-cal/Makefile
config.status: creating tests/libedataserver/Makefile
config.status: creating tests/libedataserverui/Makefile
config.status: creating docs/Makefile
config.status: creating docs/reference/Makefile
config.status: creating docs/reference/addressbook/Makefile
config.status: creating docs/reference/addressbook/libebook/Makefile
config.status: creating docs/reference/addressbook/libedata-book/Makefile
config.status: creating docs/reference/calendar/Makefile
config.status: creating docs/reference/calendar/libecal/Makefile
config.status: creating docs/reference/calendar/libedata-cal/Makefile
config.status: creating docs/reference/camel/Makefile
config.status: creating docs/reference/libedataserver/Makefile
config.status: creating docs/reference/libedataserverui/Makefile
config.status: creating docs/reference/libebackend/Makefile
config.status: creating po/Makefile.in
config.status: creating vala/Makefile
config.status: creating config.h
config.status: executing depfiles commands
config.status: executing po-directories commands
config.status: creating po/POTFILES
config.status: creating po/Makefile
config.status: executing libtool commands
config.status: executing po/stamp-it commands

    evolution-data-server has been configured as follows:
    Calendar:        yes
    Weather calendar:    yes
    Mail Directory:        /var/spool/mail, world writable
    LDAP support:        no
    NNTP support:        yes
    Kerberos 5:        no
    SSL support:        yes
    SMIME support:        yes
    IPv6 support:        yes
    Dot Locking:        yes
    File Locking:        fcntl
    Large files:        yes
    Gtk Doc:        no
    Introspection:        auto
    Vala bindings:        no
    GNOME Online Accounts    no

bash-4.1$ 


```

---

### Post by 23dornot23d on 2011-08-20
I just took the easy option ...... :) 

After around 5 days trying to install Gnome-Shell on slackware 13.37  ........ 
I came to the conclusion it is like trying to mate a Donkey with a Elephant ...... not saying which is which of course .....

So El Koraco was right in the term he used .......


and so I completed the challenge by using one that's already done ..... 

and here is one we made earlier lols
( blue peter quote for anyone not getting the joke )

Obviously this version was not done by me ......... but will now look at installing this version .... 
but it runs great from the DVD so far even with 512 Meg memory ....

[http://sourceforge.net/projects/slackex/files/](http://sourceforge.net/projects/slackex/files/)

ok his version works in slackware amd uses the Nvidia graphics card .... only thing I had to do was this .......

**nvidia-xconfig**

after log in

root   
password stocksund

[IMG]http://img534.imageshack.us/img534/4410/screenshotjt.jpg[/IMG]


Downside .... the installation does not pick up the graphics drivers/module after installation to the HDD ........ how strange .....

and slackware hates USB external drives .......[COLOR=Red]_***[ what a pain]("http://img600.imageshack.us/img600/4438/errorto.jpg")***_[/COLOR] ......

unknown block 0,30 ........ where is it trying to put it .......

and why it sees everything on the main drive sda ( [[COLOR=Red]_***1 to 7 listed on the scrreenshot ***_[/COLOR]]("http://img542.imageshack.us/img542/3922/error2s.jpg")above ) - 
but nothing from the one its booting from all upto ... sdb14 amazes me too .....

It install and boots from sdb ..... yet it might as well be a chicken or a turkey ..... to the OS
so it looks for and mounts sda ..... easy work .... main drive I see ya now .....
sdb what is this ..... is it a chicken or a frog ..... lets ignore it and move right along .....
even though we are running from it .... it even identifies everything in the fstab from the DVD live boot
so what does it loose on the transfer ....

The Graphics modules dissappear into thin air as do any references to drives I spent time telling it that this install
had.

SLACKWARE .....

My five days with it ......

It downgrades instead of upgrades ..... ( some great words to cover this is - it picks what works lols .... it does ???.... )
 
Its use of graphics drivers and it ease of installing packages is something I can go back to when I first started using computers.

What does intrigue me is its a NEVER ENDING PUZZLE .......

Why did it use LILO ..... that picked up not one of my 10 installs on the USB drive ..... oh sorry one slackex ..... but it will not boot


I still find it difficult to move away from now ..... as it needs sorting out ......

Its good once its running ..... but do not dare do anything once it is ....... 13.37 ..... oh yes .... want an upgrade

Oh yes please ...... so it starts pulling in packages from 13.1 ............. bizarre ......

Do I continue banging my head against this wall .... or move on ..... ( well two people I know succeeded so its not impossible )

Lets work out what can be done .....

1 .... The latest Gnome Shell link I have found will boot ok from the DVD ..... so ok there then .....
2 .... Install it and you have no Graphics ...... just the terminal ....as the modules for any graphics have gone .....
3 .... We have net and we can download packages ..... so how do I replace the graphics and the kernel ..... 

or even rebuild the kernel with the graphics module for Nvidia ..... 

So we need a Linux kernel - maybe the latest for a slackware build ....
We need the Linux headers ......
We need some way of compiling the kernel and getting the OS to recognize it to boot from

So the kernel ..... where is it the latest one ? ....... search _***[slackware kernel ]("http://www.google.com/search?client=ubuntu&channel=fs&q=slackware+kernel&ie=utf-8&oe=utf-8#sclient=psy&hl=en&client=ubuntu&hs=pcF&channel=fs&biw=1162&bih=511&source=hp&q=slackware+kernel+2011&pbx=1&oq=slackware+kernel+2011&aq=f&aqi=&aql=&gs_sm=e&gs_upl=10329l12183l0l12615l5l5l0l0l0l0l369l1386l2-4.1l5l0&bav=on.2,or.r_gc.r_pw.&fp=a4928e5e8a1fad2e")***_...... 

see what we get 2.6.37.6 or [[COLOR=Red]_***2.6.39.4***_[/COLOR]]("http://www.google.com/search?client=ubuntu&channel=fs&q=slackware+kernel+2.6.39.4&ie=utf-8&oe=utf-8")

lets search on the last one see if its in a directory somewhere ....

Ok the latest may not be the best in this instance from what I am reading on the forums ....

so ..... [[COLOR=Blue]_***2.6.37.6***_[/COLOR]]("http://www.google.com/search?client=ubuntu&channel=fs&q=slackware+kernel+2.6.39.4&ie=utf-8&oe=utf-8#sclient=psy&hl=en&client=ubuntu&channel=fs&source=hp&q=slackware+kernel+2.6.37.6&pbx=1&oq=slackware+kernel+2.6.37.6&aq=f&aqi=&aql=&gs_sm=e&gs_upl=857164l860982l0l861419l9l9l0l0l0l1l340l2212l0.1.2.5l8l0&bav=on.2,or.r_gc.r_pw.&fp=a4928e5e8a1fad2e&biw=1162&bih=511")

so building an [[COLOR=Red]_***Nvidia Kernel***_[/COLOR]]("http://alien.slackbook.org/dokuwiki/doku.php?id=linux:kernelbuilding") for it ..... [[COLOR=Green]_***LINK***_[/COLOR]]("http://www.google.com/search?client=ubuntu&channel=fs&q=slackware+kernel+2.6.39.4&ie=utf-8&oe=utf-8#sclient=psy&hl=en&client=ubuntu&channel=fs&source=hp&q=slackware+kernel+2.6.37.6+nvidia&pbx=1&oq=slackware+kernel+2.6.37.6+nvidia&aq=f&aqi=&aql=&gs_sm=e&gs_upl=31842l35067l0l35345l7l6l0l0l0l0l244l1129l0.5.1l6l0&bav=on.2,or.r_gc.r_pw.&fp=a4928e5e8a1fad2e&biw=1162&bih=511")

I have used Linux since time began ..... but only now am I starting to get a feel for what really happens 
under the hood ...... Slackware is very informative in every way ...... 

( even though today was a bad day for me = no real success with it yet ...... )

I will continue .... until it breaks completely or works ....

---

### Post by cbowman57 on 2011-08-20
That looks interesting.  I looked EVERYWHERE for a pre-built G-S 3 on Slack. :)

Good job.

---

### Post by 23dornot23d on 2011-08-21
Cheers Chuck ....

I have it all installed but cannot as yet get the graphics drivers working for Nvidia ....

[IMG]http://img846.imageshack.us/img846/2127/screenshotfd.jpg[/IMG]

The Installation goes well no real hiccups to be seen .... no errors 

Just when I come to re-boot ..... its a command line prompt only ....

Will spend some more time on it today though .....

Slowly and surely is good .....

Will compile all of the files in the folder you see below ...... as these are missing dependencies
from last time ..... and now I have the 32 bit - am hoping I can find more files too ....

Have just nicely got the 32 bit on here .... plus the Gnome 2.30 setup too ....

[IMG]http://img89.imageshack.us/img89/7585/screenshot1fc.jpg[/IMG]

The Gnome-Shell runs fine from DVD and is installed on the USB too .... 
but for some reason  it will not run from USB grub without a crash. :confused:

---

### Post by cbowman57 on 2011-08-21
Downloading slackex now, will try to experiment with it over the next couple days.

---

### Post by 23dornot23d on 2011-08-21
Ok good to hear

I am going through it again step by step

libffi is needed for jhbuild ....... as its the first error so have installed that first ...

[http://repository.slacky.eu/slackware-12.2/libraries/libffi/3.0.8/](http://repository.slacky.eu/slackware-12.2/libraries/libffi/3.0.8/)

download it into your main home directory

**pkgtool**

then picks up the files from this directory and will install them ....

[IMG]http://img8.imageshack.us/img8/4995/screenshot2tbx.jpg[/IMG]

so libffi 32 bit is in now .....

So now going to go get the Gnome-Shell install script for[_*** jhbuild ***_]("http://live.gnome.org/Jhbuild")from Gnome and install it all again ....

Will go through this slowly ...... and record the errors as they appear again ....... this being the 32 bit may be different
and I hope that all the packages are available this time ...... for easy installation .....

**So problem 1**

same as last time with the 64 bit .....

```

remote: Total 14695 (delta 11560), reused 7788 (delta 6539)
Receiving objects: 100% (14695/14695), 3.65 MiB | 75 KiB/s, done.
Resolving deltas: 100% (11560/11560), done.
git remote set-url origin git://git.gnome.org/gobject-introspection
git pull --rebase
Current branch master is up to date.
*** Configuring gobject-introspection *** [2/45]
./autogen.sh --prefix /home/keith/gnome-shell/install --libdir '/home/keith/gnome-shell/install/lib'  --disable-static --disable-gtk-doc 
You need to install the gnome-common module and make
sure the gnome-autogen.sh script is in your $PATH.
*** Error during phase configure of gobject-introspection: ########## Error running ./autogen.sh --prefix /home/keith/gnome-shell/install --libdir '/home/keith/gnome-shell/install/lib'  --disable-static --disable-gtk-doc  *** [2/45]

  [1] Rerun phase configure
  [2] Ignore error and continue to build
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "clean"
  [8] Go to phase "distclean"
choice: 


```Seems to be the same if not worse than last time ...... added gnome-common for docs
will see if I can get the binaries ..... and load tit straight in here ...... for gobject-introspection 
as it has not managed to make install it .....

```

libtool: link: gcc -o /home/keith/gnome-shell/source/gobject-introspection/tests/tmp-introspectcNfIR8/.libs/GIMarshallingTests-1.0 -pthread /home/keith/gnome-shell/source/gobject-introspection/tests/tmp-introspectcNfIR8/GIMarshallingTests-1.0.o -Wl,--export-dynamic  -L. ./.libs/libgimarshallingtests-1.0.so -L/home/keith/gnome-shell/install/lib -ldl -lgio-2.0 -lgobject-2.0 -lgmodule-2.0 -lgthread-2.0 -lrt -lglib-2.0 -pthread -Wl,-rpath -Wl,/home/keith/gnome-shell/install/unused
make  all-recursive
make[3]: Entering directory `/home/keith/gnome-shell/source/gobject-introspection/tests'
Making all in .
make[4]: Entering directory `/home/keith/gnome-shell/source/gobject-introspection/tests'
make[4]: Leaving directory `/home/keith/gnome-shell/source/gobject-introspection/tests'
Making all in scanner
make[4]: Entering directory `/home/keith/gnome-shell/source/gobject-introspection/tests/scanner'
  GISCAN Regress-1.0.gir
/home/keith/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_variant_dup_objv'
/home/keith/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_variant_take_ref'
/home/keith/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_variant_new_objv'
/home/keith/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_unix_open_pipe'
/home/keith/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_unix_set_fd_nonblocking'
/home/keith/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_time_zone_refresh_local'
/home/keith/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_cclosure_marshal_generic'
collect2: ld returned 1 exit status
linking of temporary binary failed: Command '['/bin/sh', '../../libtool', '--mode=link', '--tag=CC', '--silent', 'gcc', '-o', '/home/keith/gnome-shell/source/gobject-introspection/tests/scanner/tmp-introspectwZEzdW/Regress-1.0', '-export-dynamic', '-L.', 'libregress.la', '-pthread', '-L/home/keith/gnome-shell/install/lib', '-lgio-2.0', '-lgobject-2.0', '-lgmodule-2.0', '-lgthread-2.0', '-lrt', '-lglib-2.0', '/home/keith/gnome-shell/source/gobject-introspection/tests/scanner/tmp-introspectwZEzdW/Regress-1.0.o']' returned non-zero exit status 1
make[4]: *** [Regress-1.0.gir] Error 1
make[4]: Leaving directory `/home/keith/gnome-shell/source/gobject-introspection/tests/scanner'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/keith/gnome-shell/source/gobject-introspection/tests'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/keith/gnome-shell/source/gobject-introspection/tests'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/keith/gnome-shell/source/gobject-introspection'
make: *** [all] Error 2
*** Error during phase build of gobject-introspection: ########## Error running make   *** [2/45]

  [1] Rerun phase build
  [2] Ignore error and continue to install
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "configure"
  [8] Go to phase "clean"
  [9] Go to phase "distclean"
choice: 


```Ok going to start pulling the completed binaries in  from here ...... may be quicker

[http://ftp.dk.debian.org/gsb/gsb-3.0_slackware-13.37/gsb/a/](http://ftp.dk.debian.org/gsb/gsb-3.0_slackware-13.37/gsb/a/)

```

config.lt: creating libtool
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking dependency style of gcc -std=gnu99... gcc3
checking for nm... /usr/bin/nm -B
checking for some Win32 platform... no
checking whether build environment is sane... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for BASE_DEPENDENCIES... no
configure: error: Package requirements (glib-2.0 >= 2.29.14    atk >= 1.30    pango >= 1.29.0    cairo >= 1.10.0    cairo-gobject >= 1.10.0    gdk-pixbuf-2.0 >= 2.23.5) were not met:

Requested 'pango >= 1.29.0' but version of Pango is 1.28.4
Requested 'gdk-pixbuf-2.0 >= 2.23.5' but version of GdkPixbuf is 2.23.3

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BASE_DEPENDENCIES_CFLAGS
and BASE_DEPENDENCIES_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
bash-4.1$ 


``````

checking for GStreamer (needed for recording functionality)... yes
checking for TEST_SHELL_RECORDER... yes
checking for GNOME_SHELL... no
configure: error: Package requirements (gio-2.0 >= 2.29.10
                               gio-unix-2.0 dbus-glib-1 libxml-2.0
                               gtk+-3.0 >= 3.0.0
                               libmutter >= 3.0.0
                               gjs-internals-1.0 >= 1.29.15
                   libgnome-menu-3.0 gstreamer-0.10 gstreamer-base-0.10 x11 gconf-2.0
                               gdk-x11-3.0 libsoup-2.4
                   clutter-x11-1.0 >= 1.7.5
                   clutter-glx-1.0 >= 1.7.5
                               libstartup-notification-1.0 >= 0.11
                               gobject-introspection-1.0 >= 0.10.1
                   libcanberra
                               telepathy-glib >= 0.15.5
                               telepathy-logger-0.2 >= 0.2.4
                               polkit-agent-1 >= 0.100 xfixes) were not met:

Requested 'gjs-internals-1.0 >= 1.29.15' but version of gjs-internals-1.0 is 0.7.14
Requested 'telepathy-glib >= 0.15.5' but version of Telepathy-GLib is 0.14.7
Requested 'polkit-agent-1 >= 0.100' but version of polkit-agent-1 is 0.97

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GNOME_SHELL_CFLAGS
and GNOME_SHELL_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
*** Error during phase configure of gnome-shell: ########## Error running ./autogen.sh --prefix /home/keith/gnome-shell/install --libdir '/home/keith/gnome-shell/install/lib' --enable-jhbuild-wrapper-script --disable-static --disable-gtk-doc  *** [43/45]

  [1] Rerun phase configure
  [2] Ignore error and continue to build
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "clean"
  [8] Go to phase "distclean"
choice: 


```Does anybody think a slapt-get update and upgrade will solve any of these problems ..... ?

Or is there a easy way to do this .......

At the moment my thoughts are search the net for each item ...... put a link below here .....

then pull them into the new slackware release and compile them ......

[COLOR=Blue]_***[gjs-internals]("http://mail.gnome.org/archives/commits-list/2011-March/msg03747.html")***_-1.0 >= 1.29.15

[_***telepathy-glib***_]("http://aur.archlinux.org/packages.php?ID=50140") >= 0.15.5

[_***polkit-agent***_]("http://pkgs.org/package/polkit-agent")-1 >= 0.100  ( ok this one looks like we can get it - but Mandriva rpm .... keep looking )

________________________________________

[COLOR=Black]**OK 3 found .... what next ..... guess we install them somehow ....**[/COLOR]

Ok polkit-agent ..... for Slackware [_*[COLOR=Black]**HERE**[/COLOR]*_]("http://search.slackware.eu/cgi-bin/package.cgi/view/slackware-13.37/slackware/l/polkit-gnome-0.101-i486-1.txz")[COLOR=Black]   OK this installed [/COLOR]

Ttelepathy source files from Telepathy ...... [_***HERE***_]("http://telepathy.freedesktop.org/releases/")

gjs ...... files from Gnome ...... [_***HERE***_]("http://ftp.gnome.org/pub/GNOME/sources/gjs/1.29/")

_________________________________________

[COLOR=Black]I decided to wipe the full gnome-shell directory and start over again ......
but leaving all the latest upgrades of libraries in place ....
seem to be getting a cleaner build now ..... 

( but still not without problems **[[COLOR=DarkOrange]_*gobject-introspection*_[/COLOR]]("https://live.gnome.org/GObjectIntrospection")[COLOR=Red] is a real pain[/COLOR]** )
( wow - sounds to be really useful though ..... so I better get it working ok )

with it being at the start of the build too - I am not sure how many packages it affects ......

well upto **7/45** and all is well ...... so far ... 
 ....................              except for whats in red above ^^^^
.............. [B]8/45 gtk3



The more I do on this .....


I think it leads me to believe - that if you could automate the procedure for finding packages on the

net and pull the ones needed in for the relative project it would be awesome ........[/B] 

Instead I am seeming to have to track each one down ...... and they are all over the shop ......

Obviously this is only relative for latest packages ......

Lets take the 3 files above I have so far tracked down ..... 
( and we know there are loads more to find and it is constantly changing too )
( it needs one database ..... with a quick referencing system to do this efficiently )

Telepathy .... on the Telapathy site
gobject introspection ...... on the Gnome site
polkit-agent ....... on the slackware site



[B]........ 9/45 librsvg ...... FAIL .... undefined reference to "g_datalist_get_data" etc
10/45
11/45
12/45
13/45 all ok ......  after ignoring the above error  ^^^^^^^^^^^^^^^^^^^^^^^^^^^

14/45 ......libsoup ...... FAIL ..... returned non zero exit status

OK I doubt this will build now ....... so try to sort the above problems before moving on .....
[/B] [/COLOR] [/COLOR]

---

### Post by 23dornot23d on 2011-08-22
Ok got the latest Nvidia drivers loaded up now ... :D

**[Full size]("http://img12.imageshack.us/img12/8149/screenshotchk.jpg")**

[IMG]http://img838.imageshack.us/img838/9108/screenshotovb.jpg[/IMG]


cd /usr/src/linux
make prepare


Disabling the novea driver involves creating a file **/etc/modprobe.d/disable-nouveau.conf** with the following lines:     Code:
     
blacklist nouveau 
options nouveau modeset=0 



Download NVIDIA-Linux-x86_64-275.09.07.run OR NVIDIA-Linux-x86-275.09.07.run

I actually used this  link though for my Nvidia 6200

[http://www.nvidia.com/content/DriverDownload-March2009/confirmation.php?url=/XFree86/Linux-x86/280.13/NVIDIA-Linux-x86-280.13.run&lang=us&type=GeForce](http://www.nvidia.com/content/DriverDownload-March2009/confirmation.php?url=/XFree86/Linux-x86/280.13/NVIDIA-Linux-x86-280.13.run&lang=us&type=GeForce)



chmod u+x (the nvidia file you downloaded)

first add the [B]disable-nouveau.conf
into
[/B][B]/etc/modprobe.d/

reboot

then run the nvidia install .....

./[/B](the nvidia file you downloaded)

_____________________________________________________________________

So go through the slackex install 

Then do the above ......

( to make it easy - everything needs to be available on a drive that is already mounted .....)

We have a fully working version ..... on Hard Drive now ..... using slackex ..... to Desktop Main drive ....

[IMG]http://img814.imageshack.us/img814/9340/screenshot4dz.jpg[/IMG]


[http://ftp.dk.debian.org/gsb/gsb-3.0_slackware-13.37/extra/gnome-tweak-tool/](http://ftp.dk.debian.org/gsb/gsb-3.0_slackware-13.37/extra/gnome-tweak-tool/)

pkgtool

add Gnome-Tweak-tool

[IMG]http://img153.imageshack.us/img153/1497/screenshot7hk.jpg[/IMG]


can we [_***load a .rpm into slackware ***_]("http://neiland.dyndns.org/blog/article/extract-rpm-or-deb-packages-in-slackware/")... ?

[IMG]http://img692.imageshack.us/img692/7264/screenshot9zm.jpg[/IMG]



Did not last long ..... gslapt package manager ...... updated to see what I would get .....

got this ....

```

bash-4.1$ gnome-shell --replace
shm_open() failed: Permission denied
*** glibc detected *** gnome-shell: realloc(): invalid next size: 0x08249618 ***
======= Backtrace: =========
/lib/libc.so.6(+0x6f68a)[0xb5b5768a]
/lib/libc.so.6(+0x73b1e)[0xb5b5bb1e]
/lib/libc.so.6(realloc+0xdd)[0xb5b5d26d]
/usr/lib/seamonkey/libmozjs.so(+0xbd7cd)[0xb74017cd]
/usr/lib/seamonkey/libmozjs.so(+0xbe86f)[0xb740286f]
/usr/lib/seamonkey/libmozjs.so(+0x12120c)[0xb746520c]
/usr/lib/seamonkey/libmozjs.so(+0x12154b)[0xb746554b]
/usr/lib/seamonkey/libmozjs.so(+0x1219fa)[0xb74659fa]
/usr/lib/seamonkey/libmozjs.so(+0xc4e17)[0xb7408e17]
/usr/lib/seamonkey/libmozjs.so(+0xc521f)[0xb740921f]
/usr/lib/seamonkey/libmozjs.so(JS_InitStandardClasses+0x68)[0xb736f858]
/usr/lib/libgjs.so.0(gjs_init_context_standard+0x48)[0xb76499a8]
/usr/lib/libgjs.so.0(+0x879f)[0xb764679f]
/usr/lib/libgobject-2.0.so.0(g_object_newv+0x30c)[0xb5d82ffc]
/usr/lib/libgobject-2.0.so.0(g_object_new_valist+0x328)[0xb5d84318]
/usr/lib/libgobject-2.0.so.0(g_object_new+0x77)[0xb5d84437]
/usr/lib/gnome-shell/libgnome-shell.so(+0x2a6a6)[0xb773f6a6]
/usr/lib/libgobject-2.0.so.0(g_type_create_instance+0x3f1)[0xb5da37b1]
/usr/lib/libgobject-2.0.so.0(+0xdf45)[0xb5d7ff45]
/usr/lib/libgobject-2.0.so.0(g_object_newv+0x9cf)[0xb5d836bf]
/usr/lib/libgobject-2.0.so.0(g_object_new+0xa0)[0xb5d84460]
/usr/lib/gnome-shell/libgnome-shell.so(shell_global_get+0x3d)[0xb773fa2d]
gnome-shell(main+0x522)[0x804a772]
/lib/libc.so.6(__libc_start_main+0xe6)[0xb5afedb6]
gnome-shell[0x8049ce1]
======= Memory map: ========
08048000-0804b000 r-xp 00000000 08:04 287343     /usr/bin/gnome-shell
0804b000-0804c000 rw-p 00003000 08:04 287343     /usr/bin/gnome-shell
0804c000-08254000 rw-p 00000000 00:00 0          [heap]
ad200000-ad221000 rw-p 00000000 00:00 0 
ad221000-ad300000 ---p 00000000 00:00 0 
ad400000-ad500000 rw-p 00000000 00:00 0 
ad5d5000-ad5e5000 rwxp 00000000 00:00 0 
ad5e5000-ad9e5000 rw-p 00000000 00:00 0 
ad9e5000-ad9f5000 rwxp 00000000 00:00 0 
ad9f5000-ad9f6000 ---p 00000000 00:00 0 
ad9f6000-ae1f5000 rw-p 00000000 00:00 0 
ae1f5000-ae1f6000 ---p 00000000 00:00 0 
ae1f6000-b29f5000 rw-p 00000000 00:00 0 
b29f5000-b29fb000 r-xp 00000000 08:04 819280     /usr/lib/libcanberra-0.28/libcanberra-pulse.so
b29fb000-b29fc000 rw-p 00005000 08:04 819280     /usr/lib/libcanberra-0.28/libcanberra-pulse.so
b29fc000-b29fd000 ---p 00000000 00:00 0 
b29fd000-b31fc000 rw-p 00000000 00:00 0 
b31fc000-b31fd000 ---p 00000000 00:00 0 
b31fd000-b39fc000 rw-p 00000000 00:00 0 
b39fc000-b39fe000 r--p 00000000 08:04 271722     /home/keith/.config/dconf/user
b39fe000-b39ff000 r--s 00000000 08:04 271724     /home/keith/.cache/dconf/user
b39ff000-b3a05000 r-xp 00000000 08:04 24390      /usr/lib/gio/modules/libdconfsettings.so
b3a05000-b3a06000 rw-p 00005000 08:04 24390      /usr/lib/gio/modules/libdconfsettings.so
b3a06000-b3a17000 r-xp 00000000 08:04 24400      /usr/lib/gio/modules/libgioremote-volume-monitor.so
b3a17000-b3a18000 rw-p 00011000 08:04 24400      /usr/lib/gio/modules/libgioremote-volume-monitor.so
b3a18000-b3a2c000 r-xp 00000000 08:04 820226     /usr/lib/libgvfscommon.so.0.0.0
b3a2c000-b3a2d000 rw-p 00013000 08:04 820226     /usr/lib/libgvfscommon.so.0.0.0
b3a2d000-b3a51000 r-xp 00000000 08:04 24404      /usr/lib/gio/modules/libgvfsdbus.so
b3a51000-b3a52000 rw-p 00024000 08:04 24404      /usr/lib/gio/modules/libgvfsdbus.so
b3a52000-b3a69000 r--p 00000000 08:04 23897      /usr/share/glib-2.0/schemas/gschemas.compiled
b3a69000-b3a80000 r--p 00000000 08:04 23897      /usr/share/glib-2.0/schemas/gschemas.compiled
b3a80000-b3a82000 r-xs 00000000 08:04 660758     /tmp/gll8wIef (deleted)
b3a82000-b3a84000 rw-s 00000000 08:04 660758     /tmp/gll8wIef (deleted)
b3a84000-b3ac4000 rw-s efb3a000 00:05 7186       /dev/nvidia0
b3ac4000-b3bc4000 rw-s d0114000 00:05 7186       /dev/nvidia0
b3bc4000-b3bc5000 rw-s f0c02000 00:05 7186       /dev/nvidia0
b3bc5000-b3cc5000 rw-s d0011000 00:05 7186       /dev/nvidia0
b3cc5000-b3dcf000 rw-p 00000000 00:00 0 
b3dcf000-b3dd0000 rw-s f0001000 00:05 7186       /dev/nvidia0
b3dd0000-b4250000 rw-s e0000000 00:05 7186       /dev/nvidia0
b4250000-b426b000 rw-s 1eea0000 00:05 7186       /dev/nvidia0
b426b000-b42e4000 rw-p 00000000 00:00 0 
b42e4000-b42ee000 r-xp 00000000 08:04 392836     /lib/libnss_files-2.13.so
b42ee000-b42ef000 r--p 00009000 08:04 392836     /lib/libnss_files-2.13.so
b42ef000-b42f0000 rw-p 0000a000 08:04 392836     /lib/libnss_files-2.13.so
b42f0000-b4305000 r-xp 00000000 08:04 392830     /lib/libnsl-2.13.so
b4305000-b4306000 r--p 00014000 08:04 392830     /lib/libnsl-2.13.so
b4306000-b4307000 rw-p 00015000 08:04 392830     /lib/libnsl-2.13.so
b4307000-b4309000 rw-p 00000000 00:00 0 
b430b000-b430d000 r-xp 00000000 08:04 392880     /lib/libutil-2.13.so
b430d000-b430e000 r--p 00001000 08:04 392880     /lib/libutil-2.13.so
b430e000-b430f000 rw-p 00002000 08:04 392880     /lib/libutil-2.13.so
b430f000-b431b000 r-xp 00000000 08:04 392875     /lib/libudev.so.0.10.0
b431b000-b431c000 rw-p 0000b000 08:04 392875     /lib/libudev.so.0.10.0
b431c000-b4320000 rw-s 1c126000 00:05 7186       /dev/nvidia0
b4320000-b4321000 rw-s efb7b000 00:05 7186       /dev/nvidia0
b4321000-b4322000 rw-s 1c2e6000 00:05 7186       /dev/nvidia0
b4322000-b4323000 rw-s d0112000 00:05 7186       /dev/nvidia0
b4323000-b4324000 rw-s 1cccd000 00:05 7186       /dev/nvidia0
b4324000-b4325000 r--p 00000000 08:04 808640     /usr/share/locale/en/LC_MESSAGES/gtk30-properties.mo
b4325000-b4326000 r-xp 00000000 08:04 23816      /usr/lib/gconv/ISO8859-1.so
b4326000-b4327000 r--p 00000000 08:04 23816      /usr/lib/gconv/ISO8859-1.so
b4327000-b4328000 rw-p 00001000 08:04 23816      /usr/lib/gconv/ISO8859-1.so
b4328000-b435f000 r--p 00000000 08:04 147690     /usr/lib/locale/en_US/LC_CTYPE
b435f000-b4365000 rw-p 00000000 00:00 0 
b4365000-b4369000 r-xp 00000000 08:04 392761     /lib/libattr.so.1.1.0
b4369000-b436a000 rw-p 00003000 08:04 392761     /lib/libattr.so.1.1.0
b436a000-b436b000 rw-p 00000000 00:00 0 
b436b000-b5a20000 r-xp 00000000 08:04 820758     /usr/lib/libnvidia-glcore.so.270.41.06
b5a20000-b5a7c000 rwxp 016b4000 08:04 820758     /usr/lib/libnvidia-glcore.so.270.41.06
b5a7c000-b5a8d000 rwxp 00000000 00:00 0 
b5a8d000-b5a8e000 r-xp 00000000 08:04 824061     /usr/lib/tls/libnvidia-tls.so.270.41.06
b5a8e000-b5a8f000 rw-p 00000000 08:04 824061     /usr/lib/tls/libnvidia-tls.so.270.41.06
b5a8f000-b5a90000 rw-p 00000000 00:00 0 
b5a90000-b5ac1000 r-xp 00000000 08:04 833244     /usr/lib/seamonkey-2.2/libnspr4.so
b5ac1000-b5ac2000 rw-p 00031000 08:04 833244     /usr/lib/seamonkey-2.2/libnspr4.so
b5ac2000-b5ac4000 rw-p 00000000 00:00 0 
b5ac4000-b5ac7000 r-xp 00000000 08:04 833239     /usr/lib/seamonkey-2.2/libplc4.so
b5ac7000-b5ac8000 rw-p 00002000 08:04 833239     /usr/lib/seamonkey-2.2/libplc4.so
b5ac8000-b5aca000 r-xp 00000000 08:04 833235     /usr/lib/seamonkey-2.2/libplds4.so
b5aca000-b5acb000 rw-p 00001000 08:04 833235     /usr/lib/seamonkey-2.2/libplds4.so
b5acb000-b5ae6000 r-xp 00000000 08:04 819710     /usr/lib/libgcc_s.so.1
b5ae6000-b5ae7000 rw-p 0001a000 08:04 819710     /usr/lib/libgcc_s.so.1
b5ae7000-b5ae8000 rw-p 00000000 00:00 0 
b5ae8000-b5c44000 r-xp 00000000 08:04 392767     /lib/libc-2.13.so
b5c44000-b5c45000 ---p 0015c000 08:04 392767     /lib/libc-2.13.so
b5c45000-b5c47000 r--p 0015c000 08:04 392767     /lib/libc-2.13.so
b5c47000-b5c48000 rw-p 0015e000 08:04 392767     /lib/libc-2.13.so
b5c48000-b5c4b000 rw-p 00000000 00:00 0 
b5c4b000-b5c52000 r-xp 00000000 08:04 392861     /lib/librt-2.13.so
b5c52000-b5c53000 r--p 00006000 08:04 392861     /lib/librt-2.13.so
b5c53000-b5c54000 rw-p 00007000 08:04 392861     /lib/librt-2.13.so
b5c54000-b5d53000 r-xp 00000000 08:04 819896     /usr/lib/libglib-2.0.so.0.2800.6
b5d53000-b5d54000 rw-p 000ff000 08:04 819896     /usr/lib/libglib-2.0.so.0.2800.6
b5d54000-b5d69000 r-xp 00000000 08:04 392857     /lib/libpthread-2.13.so
b5d69000-b5d6a000 r--p 00014000 08:04 392857     /lib/libpthread-2.13.so
b5d6a000-b5d6b000 rw-p 00015000 08:04 392857     /lib/libpthread-2.13.so
b5d6b000-b5d6d000 rw-p 00000000 00:00 0 
b5d6d000-b5d70000 r-xp 00000000 08:04 820129     /usr/lib/libgthread-2.0.so.0.2800.6
b5d70000-b5d71000 rw-p 00003000 08:04 820129     /usr/lib/libgthread-2.0.so.0.2800.6
b5d71000-b5d72000 rw-p 00000000 00:00 0 
b5d72000-b5db6000 r-xp 00000000 08:04 819990     /usr/lib/libgobject-2.0.so.0.2800.6
b5db6000-b5db7000 rw-p 00043000 08:04 819990     /usr/lib/libgobject-2.0.so.0.2800.6
b5db7000-b5db8000 rw-p 00000000 00:00 0 
b5db8000-b5ddc000 r-xp 00000000 08:04 392821     /lib/libm-2.13.so
b5ddc000-b5ddd000 r--p 00023000 08:04 392821     /lib/libm-2.13.so
b5ddd000-b5dde000 rw-p 00024000 08:04 392821     /lib/libm-2.13.so
b5dde000-b5de0000 r-xp 00000000 08:04 392791     /lib/libdl-2.13.so
b5de0000-b5de1000 r--p 00001000 08:04 392791     /lib/libdl-2.13.so
b5de1000-b5de2000 rw-p 00002000 08:04 392791     /lib/libdl-2.13.so
b5de2000-b5de5000 r-xp 00000000 08:04 392772     /lib/libcap.so.2.20
b5de5000-b5de6000 rw-p 00003000 08:04 392772     /lib/libcap.so.2.20
b5de6000-b5deb000 r-xp 00000000 08:04 819755     /usr/lib/libgdbm.so.3.0.0
b5deb000-b5dec000 rw-p 00004000 08:04 819755     /usr/lib/libgdbm.so.3.0.0
b5dec000-b5e27000 r-xp 00000000 08:04 819446     /usr/lib/libdbus-1.so.3.5.3
b5e27000-b5e28000 r--p 0003b000 08:04 819446     /usr/lib/libdbus-1.so.3.5.3
b5e28000-b5e29000 rw-p 0003c000 08:04 819446     /usr/lib/libdbus-1.so.3.5.3
b5e29000-b5e2a000 rw-p 00000000 00:00 0 
b5e2a000-b5e2f000 r-xp 00000000 08:04 820776     /usr/lib/libogg.so.0.7.1
b5e2f000-b5e30000 rw-p 00004000 08:04 820776     /usr/lib/libogg.so.0.7.1
b5e30000-b5e56000 r-xp 00000000 08:04 821432     /usr/lib/libvorbis.so.0.4.5
b5e56000-b5e57000 rw-p 00025000 08:04 821432     /usr/lib/libvorbis.so.0.4.5
b5e57000-b5fbc000 r-xp 00000000 08:04 821436     /usr/lib/libvorbisenc.so.2.0.8
b5fbc000-b5fcd000 rw-p 00165000 08:04 821436     /usr/lib/libvorbisenc.so.2.0.8
b5fcd000-b601b000 r-xp 00000000 08:04 818643     /usr/lib/libFLAC.so.8.2.0
b601b000-b601c000 rw-p 0004e000 08:04 818643     /usr/lib/libFLAC.so.8.2.0
b601c000-b607c000 r-xp 00000000 08:04 821140     /usr/lib/libsndfile.so.1.0.24
b607c000-b607e000 rw-p 00060000 08:04 821140     /usr/lib/libsndfile.so.1.0.24
b607e000-b6083000 rw-p 00000000 00:00 0 Aborted
bash-4.1$ 


```The XFCE desktop still works so will try compiling it using jhbuild .... now ..... (wasted effort)
might as well just re-install from the DVD ,,, works fine on the main drive ..... 
does not work on USB externals though .... for some reason .... no Graphics ....

C Bowmans Pack ..... still very useful indeed all in one place ....
putting link here as I keep losing it .....
[Direct download gNatty Pack (Contains themes & extensions) or just the gNatty Extensions]("http://cid-32ec6e89f4aa803b.office.live.com/self.aspx/Linux/gNatty%20Pack.tar.gz") [COLOR=Red]*[/COLOR] Updated 29 June 2011]


we need it to set the theme to Elegant ......

so open up /home/.themes

and drop all the themes in there .....

---

### Post by 23dornot23d on 2011-08-22
We can have Gnome-Shell up and running in 20 minutes now ..... 

[***Slackex ***]("http://sourceforge.net/projects/slackex/")- to sda4 ..... for me was perfect .....

[IMG]http://img163.imageshack.us/img163/2669/screenshotnan.png[/IMG]

For a quick Gnome-Shell ...... and I mean quick in install and quick in working .... this is the way to go .......

add[]("http://www.blender.org/index.php?id=1262&f=http://download.blender.org/release/Blender2.59/blender-2.59-linux-glibc27-x86_64.tar.bz2")[_***Blender***_]("http://www.blender.org/index.php?id=1262&f=http://download.blender.org/release/Blender2.59/blender-2.59-linux-glibc27-i686.tar.bz2") - Linux 32 bit
and [_**WINGS3d**_]("http://www.wings3d.com/redirect_download.php?title=stable_linux")
TRON BIKE ..... Latest Download - Now a 3ds File .....[ _*[COLOR=Red]**LINK**[/COLOR]*_]("https://sites.google.com/site/blenderlearn/assignments/blenderfiles/003-TRON-BIKE4-only.3ds?attredirects=0&d=1")                                              
import in my TRON bike .... 

and have a play ..... this is fast for 3D on this old machine of mine too ....

Try to stay away from the Gslapt upgrades though ..... ( not keen on any upgrades on this DISTRO )

New installs are ok ...... though .... or seem to be ......

---

### Post by cbowman57 on 2011-08-23
I tried to boot Slackex from pen drive, no luck at all. :(

Looks good though, congratulations. :)

---

### Post by 23dornot23d on 2011-08-23
Cheers Chuck ......

I found there are some [[COLOR=Red]_***more instructions for USB s***_[/COLOR] ]("http://linux.exton.net/")..... [[COLOR=Blue]_***ENGLISH LINK***_[/COLOR]]("http://linux.exton.net/english")... but the only install that is working is
from the Main Drive ..... maybe it was made on the same partition who knows ,,,, sda4 is good
sda6 = problem .

Got one good install and will continue to see if it can be upgraded ....... only a month to go now ... ;)

Taken me a full week to get it working ..... also learned a lot about slackware and quite like some
things about it ...... ever so fast ,,,



_______________
[B]
Latest ,,,  splice works ....[/B]

[IMG]http://img33.imageshack.us/img33/4695/screenshot5ji.jpg[/IMG]
[URL="http://img6.imageshack.us/img6/6648/screenshot8jq.jpg"][COLOR=Sienna][U][I][B]
FULLSIZE SCREENSHOT[/B][/I][/U][/COLOR][/URL] ( and I do really like this now )

must look into these themes more now too ...... ;) ... Cheers to Chuck ... and [[COLOR=Sienna]_***Sam Riggs***_[/COLOR]]("http://samriggs.deviantart.com/gallery/#/d45x2o9") ..... for the Steampunk look - really is amazing once you have it on your computer you see the detail ..... never looks the same on the net ...

Install in the SLACKEX 32 bit
Straight after that Install in the Full Slackware 32 bit distro ..... no Format ......
Now load in the latest Nvidia drivers .....

best way I found was go on the same drive in another distro ..... download the NVIDIA drivers from Nvidia

copy the driver file 33Meg to root .... on the new install drive .....
also add the Blacklist Nouveau File we created earlier and put it in /etc/modprobe.d/


Then boot into it ..... do the following first ......

cd /usr/src/linux
make prepare

chmod u+x ( Nvidia file so it will run )
./(Nvidia File)

startx .......

Then we have this ...... with a totally fully working GS build ....... plus KDE runs too
and all the files for movies etc too ... as myth TV is installed and runs as good on
this 512 Meg machine as it does using other OS on my Acer Aspire 7720 Laptop 


Steampunk ..... ideas

[IMG]http://img153.imageshack.us/img153/9158/screenshot1lz.jpg[/IMG]

[http://severi4n.deviantart.com/art/fond-d-ecran-ababakar1-183716388](http://severi4n.deviantart.com/art/fond-d-ecran-ababakar1-183716388)

I need some steampunk icons now ..... too ....

[IMG]http://img683.imageshack.us/img683/254/screenshot2kw.jpg[/IMG]


[http://my.opera.com/ubuntunerd1/blog/u](http://my.opera.com/ubuntunerd1/blog/u)

---

### Post by 23dornot23d on 2011-08-24
To get Conky going  ...... we need lua5 from here ..... 

[http://pkgs.org/download/slackware-13.1/slacky-i486/lua-5.1.4.2-i486-1sl.txz.html](http://pkgs.org/download/slackware-13.1/slacky-i486/lua-5.1.4.2-i486-1sl.txz.html)


as well as conky ,,,, from sourceforge

[http://sourceforge.net/projects/conky/](http://sourceforge.net/projects/conky/)


[IMG]http://img163.imageshack.us/img163/8671/screenshot5tf.jpg[/IMG]

---

### Post by cbowman57 on 2011-08-24
I am impressed Keith, it's like you've crammed a whole computer science course into a week.

I wish I shared your tenacity.  Really looks great, and what an accomplishment. =D>

---

### Post by 23dornot23d on 2011-08-24
Cheers Chuck .....

Could not have done half of it without all the work you have put into the Ubuntu version
plus the gNatty pack ..... and also the latest theme ..... SteamPunk .....

Plus all the problem solving you have done on Gnome Shell ....

Really makes it a joy doing this ...... and hopefully someone will find it useful too
at some time in the future ....

Thinking about what to do next now ..... Arch is looking good .... for a tryout now ...

:confused:

---

### Post by cbowman57 on 2011-08-24
I'd like to know how Arch would compare to your latest creation.  I just don't have the patience to do what you did here.

I hope el_koraco has popped in & seen this latest project. :)

---

### Post by 23dornot23d on 2011-08-24
Well to do this properly (up to date I mean as its version 3.0.0 ) 

I did download the Gnome-Shell 3.0.2 .... and that is running at the moment on one build ,,,

It would take a lot of work - someone already did that (EXTON) creating Slackex .....
I took the easy option once I found it ......

But it still needs bringing up to date .... version 3.1.5 ......
So may come back to it again ....

Needs Jhbuild doing from start to Finish .... but with version 3.2 if I am going to do it
as it should be stable then and worth the effort ....

But another one working and very good too .... 
Low memory usage ......... and ever so fast .... love films on it .....
Could never run them properly before ..... on this machine ... without them lagging.

---

### Post by cbowman57 on 2011-08-24
While you've been doing this I buried myself in Arch, I'm really pleased with the result too.  I've done a lot of optimization, and with the Raid0 working it's the probably my best G-S installation to date.  I think my quest for the perfect linux may be over. :)

It doesn't have a real small memory footprint (anymore) but I've attempted to optimize it for max performance, and with 2 GB of RAM available I don't think it's a crime to use 35-40% of it for the snap it has. The only way it could feel faster would be if it anticipated my keystrokes or used telepathy.

---

### Post by 23dornot23d on 2011-08-24
Sounds good ..... do you want to do a thread on The Arch one  ..... and go through it in more detail ..... 
or do you already have one somewhere .... ?

I would be happy to go along with a new build now on it .....

And hopefully use your experience for setting it up right ......

Just need to clear another partition ..... hope it will run on my external USB 


as the little drive 80 Gig on the 512 Meg Celeron 3100 machine is Full at the moment ....

Do you have a link to the download too ..... the one that runs good ......

---

### Post by cbowman57 on 2011-08-24
No, haven't even thought of starting a thread on it & haven't a clue how to go about creating an installation iso out of it.  That's kind of what is making it so much fun, with gNatty &  Debian I was to the point I could almost do it in my sleep.  Like your Slackware project here, it's really occupied my time & kept me busy.

---

### Post by 23dornot23d on 2011-08-24
Lets start one and see where it goes .... then ..... 

Shall we call it ....

Arch - finding the quickest way for Gnome Shell to run on it :)
or something else ... you choose ... as I do not even know if I can get it running yet ....

If an installation can be created from it all well and good ..... 

but a recipe may be all that is needed.

We could create the LINUX COOKBOOK for GNOME SHELL    .... ;)

Ok I am downloading the top one from here ...... [http://mir.archlinux.fr/iso/2011.08.19/](http://mir.archlinux.fr/iso/2011.08.19/)

If I get it installed ....  will go from there .... play it by ear so to speak .....

[COLOR=Red][B]Arch next Project ..... 

Go back a page to see the Slackware .... solutions ....[/B][/COLOR]

---

### Post by cbowman57 on 2011-08-24
Yeah, see where it goes.  Net or core install both give you basically all the same options & installation interface so any one of those is good.  The multi-arch versions are handy, especially with your mix of hardware.

---

### Post by 23dornot23d on 2011-08-24
Ok its Installing now ..... will create a thread once its working .....

---

### Post by cbowman57 on 2011-08-24
After what you did with Slackex I'm sure this is going to be a piece of cake.

---

### Post by 23dornot23d on 2011-08-24
:lolflag:   Got it installed ...... and have the same problems I had with Slackware ....

USB ...... does not seem to pick up on the BIOS on the desktop machine ......

So all I see is the sda ..... sdb is invisible at boot time to this ..... only way I can get it to boot ....

Is to use Grub2 ....... or chainload ...... as Grub is not working .... 

and I have no space on my main hard drive now for another install ........

[IMG]http://img9.imageshack.us/img9/601/arch2z.jpg[/IMG]


I get the boot loader same as in Slack too ...... but cannot get it to see the USB drive ....

In Slackware I had to load it to my main drive ....... 

What to do .... is there a way to get Grub 2 to boot it up from my external hard drive.

I should have used UUIDs .... I think on it ..... to make it easier for Grub2 .....

The installation went fine ..... though ....

---

### Post by cbowman57 on 2011-08-24
If you can get into it again you can pacman -S grub2-bios and AUR has os-prober.  I've never done any chain loading, you probably know it better than I do.

I did see something about booting from USB drive somewhere though and I think the solution was to give udev more wait time, but I'm not positive I remember it correctly.

Might be time for you to start the Arch thread. :)

---

### Post by 23dornot23d on 2011-08-24
Just having a quick read ..... may have to install it on the main drive .... means kicking one version of Slackware off ...... 

Maybe I missed something though ..... 
as I can usually get things to boot after installing to a drive .... by going into another
install and just by running 

grub-install /dev/sdb

Would be up and running ...... But this time its a no go ...... saying the partition does not exist - and I know it does .... checked it and the contents from another OS 

So its installed ...... just the boot process ..... 

I even changed to  using UUIDs ......

So maybe its time to install on sda and remove a slackware install ...... but that then
stops me using one for testing on ..... Decisions Decisions ......

or learn how the boot process works ....... 

I guess this is time to start reading about where and how it does what it does to
start the System going .......

Going to sleep on it ...... never got anywhere by rushing into things ..... 
will maybe post some more tomorrow
and start a new thread for it too .......

---

### Post by cbowman57 on 2011-08-24
Yeah, sometimes it's just best to walk away for a bit.

Catch you tomorrow.

---

### Post by 23dornot23d on 2011-08-24
Yep will be on this early I think ..... catch you later ..... cheers for the ideas too ....
I did have had a quick scan around ..... one thing is with Arch its not short of information.;)


Have Started a new Thread here for [[COLOR=Red]_***Arch and Archbang***_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1832919")

---

### Post by cbowman57 on 2011-08-24
Yeah, the forums are much different than here but the wiki's are incredible.  And the people that are into using Arch are REALLY into Arch.

---

### Post by 23dornot23d on 2011-08-25
[IMG]http://img163.imageshack.us/img163/8671/screenshot5tf.jpg[/IMG]

---

### Post by 23dornot23d on 2011-08-25
cd /usr/src/linux
make prepare


Disabling the novea driver involves creating a file **/etc/modprobe.d/disable-nouveau.conf** with the following lines:     Code:
     
blacklist nouveau 
options nouveau modeset=0 



This was the solution for Slackware ...... 

Slackex - was the Distro I ended up using ......

( But if you have problems with getting the Nvidia drivers to load up ...... this is what I did to get mine
working properly )

Download NVIDIA-Linux-x86_64-275.09.07.run OR NVIDIA-Linux-x86-275.09.07.run

I actually used this  link though for my Nvidia 6200

[http://www.nvidia.com/content/Driver...s&type=GeForce]("http://www.nvidia.com/content/DriverDownload-March2009/confirmation.php?url=/XFree86/Linux-x86/280.13/NVIDIA-Linux-x86-280.13.run&lang=us&type=GeForce")

chmod u+x (the nvidia file you downloaded)

first add the [B]disable-nouveau.conf
into
[/B][B]/etc/modprobe.d/

reboot

then run the nvidia install .....

./[/B](the nvidia file you downloaded)

---

