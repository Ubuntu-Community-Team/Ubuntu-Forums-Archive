---
title: "PPC Software &amp; Repositories"
date: 2005-02-09
forum: Apple PPC Users
---

### Post by dubdubdub on 2005-02-09
Is software available for ubuntu the same for X86 and PPC? 

If so what is a good listing of PPC repositories to use?

I tried enabling repositories I read about when using Ubuntu on my X86, and I can't seem to find simple software like a Macromedia Flash player for Firefox.

I hope it isn't like BeOS, the X86 market was much larger than the PPC one.

Thanks in advance

---

### Post by DJ_Max on 2005-02-09
Macromedia doesn't make their flash plugin for linux-ppc. You have to use [GPLFlash](http://gplflash.sourceforge.net/)

I got a list of repsitories, [http://ubuntuppc.webplazahosting.com/index.php?Repositories](http://ubuntuppc.webplazahosting.com/index.php?Repositories)

---

### Post by dubdubdub on 2005-02-09
./configure error

checking for gzsetparams in -lz... no
configure: error: *** GPLFLash requires libz.


Suggestions?

---

### Post by DJ_Max on 2005-02-09
[QUOTE=dubdubdub]./configure error

checking for gzsetparams in -lz... no
configure: error: *** GPLFLash requires libz.


Suggestions?[/QUOTE]
 It's saying you need libz. Why not install gplflash via apt-get?

```
sudo apt-get install gplflash
```

---

### Post by dubdubdub on 2005-02-09
dub@ubuntu:~ $ sudo apt-get install gplflash
Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package gplflash
dub@ubuntu:~ $


I was trying it before using ./configure in the directory I uncompressed the GBLFlash file recommended above.


my /etc/apt/sources.list below:

deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview powerpc Binary-1 (20041020)]/ unstable main restricted  

## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse

deb [http://honk.physik.uni-konstanz.de/~agx/linux-ppc/debian/](http://honk.physik.uni-konstanz.de/~agx/linux-ppc/debian/) mplayer/

deb [http://apt.cerkinfo.be/](http://apt.cerkinfo.be/) unstable main contrib non-free
deb-src [http://apt.cerkinfo.be/](http://apt.cerkinfo.be/) unstable main contrib non-free

---

### Post by DJ_Max on 2005-02-10
I forgot the name of the gplflash debian file.
do
```
apt-cache search flash
```
Look for gplflash, then install it.

---

### Post by dubdubdub on 2005-02-10
Thanks again for all your help! I used apt-cache search flash and found swf-player and installed it. Tested on a flash file I knew was verson 4 and it worked ok.

Now if the developers would just bring this up to speed I would be happy.

I do freelance web design (including flash) for a living. Its a little frustrating not being able to see your own website or half the sites you have built  :?

---

### Post by Ptero-4 on 2005-02-10
[QUOTE=dubdubdub]./configure error

checking for gzsetparams in -lz... no
configure: error: *** GPLFLash requires libz.


Suggestions?[/QUOTE]
 It says that you need zlib (libz = zlib)

---

### Post by dragon_mac on 2005-04-12
Hi, i'm totally new into linux, i'm trying hard to install flashplayer, i have to use it at work, i'm using hoary in a powerbook, runs awesomely fine, but it's a shame i can't use flash, so i did this:
but it won't work, i don't know what am i doing wrong.., if some one has ppc/linux with flash working, please let me know, i don't wanna go back to windows nor osx.
i managed to configure all the stuff to get my powerbook working fine, even resolution glitches. please help  [-o< 

root@ubuntu:/home/drakkar/gplflash # ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... powerpc-unknown-linux-gnu
checking host system type... powerpc-unknown-linux-gnu
checking for g++... g++
checking for C++ compiler default output file name... a.out
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
checking how to run the C++ preprocessor... g++ -E
checking for g77... g77
checking whether we are using the GNU Fortran 77 compiler... yes
checking whether g77 accepts -g... yes
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
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for g77 option to produce PIC... -fPIC
checking if g77 PIC flag -fPIC works... yes
checking if g77 supports -c -o file.o... yes
checking whether the g77 linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking for jpeg_destroy_decompress in -ljpeg... yes
checking jpeglib.h usability... yes
checking jpeglib.h presence... yes
checking for jpeglib.h... yes
checking for gzsetparams in -lz... yes
checking zlib.h usability... yes
checking zlib.h presence... yes
checking for zlib.h... yes
checking for X... libraries /usr/X11R6/lib, headers /usr/X11R6/include
checking for XOpenDisplay in -lX11... yes
checking X11/XKBlib.h usability... yes
checking X11/XKBlib.h presence... yes
checking for X11/XKBlib.h... yes
checking for mad_frame_decode in -lmad... yes
checking mad.h usability... yes
checking mad.h presence... yes
checking for mad.h... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating lib/Makefile
config.status: creating player/Makefile
config.status: creating plugin/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
root@ubuntu:/home/drakkar/gplflash # make
make  all-recursive
make[1]: Entering directory `/home/drakkar/gplflash'
Making all in lib
make[2]: Entering directory `/home/drakkar/gplflash/lib'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/drakkar/gplflash/lib'
Making all in player
make[2]: Entering directory `/home/drakkar/gplflash/player'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/drakkar/gplflash/player'
Making all in plugin
make[2]: Entering directory `/home/drakkar/gplflash/plugin'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/drakkar/gplflash/plugin'
make[2]: Entering directory `/home/drakkar/gplflash'
make[2]: Leaving directory `/home/drakkar/gplflash'
make[1]: Leaving directory `/home/drakkar/gplflash'
root@ubuntu:/home/drakkar/gplflash # make install
Making install in lib
make[1]: Entering directory `/home/drakkar/gplflash/lib'
make[2]: Entering directory `/home/drakkar/gplflash/lib'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib" || mkdir -p -- "/usr/local/lib"
 /bin/sh ../libtool --mode=install /usr/bin/install -c  'libflash.la' '/usr/loca l/lib/libflash.la'
/usr/bin/install -c .libs/libflash.so.0.13.0 /usr/local/lib/libflash.so.0.13.0
(cd /usr/local/lib && rm -f libflash.so.0 && ln -s libflash.so.0.13.0 libflash.s o.0)
(cd /usr/local/lib && rm -f libflash.so && ln -s libflash.so.0.13.0 libflash.so)
/usr/bin/install -c .libs/libflash.lai /usr/local/lib/libflash.la
PATH="$PATH:/sbin" ldconfig -n /usr/local/lib
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
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
test -z "/usr/local/include" || mkdir -p -- "/usr/local/include"
 /usr/bin/install -c -m 644 'flash.h' '/usr/local/include/flash.h'
make[2]: Leaving directory `/home/drakkar/gplflash/lib'
make[1]: Leaving directory `/home/drakkar/gplflash/lib'
Making install in player
make[1]: Entering directory `/home/drakkar/gplflash/player'
make[2]: Entering directory `/home/drakkar/gplflash/player'
test -z "/usr/local/bin" || mkdir -p -- "/usr/local/bin"
  /bin/sh ../libtool --mode=install /usr/bin/install -c 'swfplayer' '/usr/local/ bin/swfplayer'
/usr/bin/install -c .libs/swfplayer /usr/local/bin/swfplayer
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/drakkar/gplflash/player'
make[1]: Leaving directory `/home/drakkar/gplflash/player'
Making install in plugin
make[1]: Entering directory `/home/drakkar/gplflash/plugin'
make[2]: Entering directory `/home/drakkar/gplflash/plugin'
make[2]: Nothing to be done for `install-exec-am'.
mkdir -p "/usr/local/lib/mozilla/plugins/"
cp ./.libs/libnpflash.so.0.0.0 "/usr/local/lib/mozilla/plugins//libnpflash.so"
make[2]: Leaving directory `/home/drakkar/gplflash/plugin'
make[1]: Leaving directory `/home/drakkar/gplflash/plugin'
make[1]: Entering directory `/home/drakkar/gplflash'
make[2]: Entering directory `/home/drakkar/gplflash'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/drakkar/gplflash'
make[1]: Leaving directory `/home/drakkar/gplflash'
root@ubuntu:/home/drakkar/gplflash #

---

### Post by DJ_Max on 2005-04-12
You gotta finish.
do make
then do
sudo make install

*EDIT*
Seems you already did that, but you might not have had the proper privileges with make install.

---

### Post by dragon_mac on 2005-04-12
[QUOTE=DJ_Max]You gotta finish.
do make
then do
sudo make install

*EDIT*
Seems you already did that, but you might not have had the proper privileges with make install.[/QUOTE]
 swear id dit it, and nothing, can't get it installed, y rebooted the system to make sure, but nothing, what am i missing?

---

### Post by jkr on 2005-04-13
I'm on the net successfully but have real problems with getting packages - keep getting  Couldn't stat source package list [http://archive](http://archive)......

I have the recommended /etc/apt/sources.list

What's going on?

---

### Post by jkr on 2005-04-13
...ok excuse the sloppy work, it worked second try in synaptic.

---

### Post by Aurora on 2005-04-19
[QUOTE=dubdubdub]Thanks again for all your help! I used apt-cache search flash and found swf-player and installed it. Tested on a flash file I knew was verson 4 and it worked ok.

Now if the developers would just bring this up to speed I would be happy.

I do freelance web design (including flash) for a living. Its a little frustrating not being able to see your own website or half the sites you have built  :?[/QUOTE]

Hi,

See if it will work with this site:

[http://www.harley-davidson.com/PR/MOT/2006/VRSCR_minisite/VRSCR_noflash.asp?bmLocale=en_US&dwp_dealer_id=156716&dwp_sid=0422146X4K17K2005J1I57I10JAMQ1106R0&dwp_sid_name=sid&modelYear=05](http://www.harley-davidson.com/PR/MOT/2006/VRSCR_minisite/VRSCR_noflash.asp?bmLocale=en_US&dwp_dealer_id=156716&dwp_sid=0422146X4K17K2005J1I57I10JAMQ1106R0&dwp_sid_name=sid&modelYear=05)

I installed swf-player via apt-get and haven't found a site I can view with it yet.

I am getting so frustrated with all the problems with Linux, I might just go out and buy a machine that can run OSX....I long for the days when I could actually accomplish tasks on a computer, rather than spending tens of hours a week fruitlessly tinkering.  I've spent several hours over the past few days unsuccessfully trying to print a one-page PDF file, but that's another post...

Aurora

---

