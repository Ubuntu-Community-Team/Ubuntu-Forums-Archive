---
title: "Compiling BMPX 0.40.12 Help!!"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by Kosimo on 2007-10-15
Hi guys.
I'm getting crazy... It's been long time that I'm trying to compile BmPX from the source code always unsuccessfully.... :(   
That's the way I do:

First I download the source code from BMPX webpage (latest version is 0.40.12)

The file is extracted, then I go into the folder in terminal.

I install the needed tools:
sudo apt-get install build-essential checkinstall

Then some dependencies:
sudo apt-get install boost-build libboost-dev libboost-regex-dev libboost-iostreams-dev libboost-thread-dev libsoup2.2-dev libglibmm-2.4-dev librsvg2-dev libgtkmm2.0-dev libgtkmm-2.4-dev libglademm-2.4-dev libsexymm-dev libgstreamer0.10-dev libdbus-1-dev libdbus-glib-1-dev libstartup-notification0-dev libofa0-dev libcdparanoia0-dev


then I invoke ./configure

and I got this error:
> checking for extern in libsoup headers... no
checking for SQLITE... configure: error: Package requirements (sqlite3 >= 3.3) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the SQLITE_CFLAGS and SQLITE_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.


Ok, I'm missing sqlite3, let's install it

Going to synaptic and search for sqlite3 witch is installed already but I realize the dev one is not installed.  OK, i proced installing that one. 

./configure again:

more errors:

> checking for GST... configure: error: Package requirements (gstreamer-0.10 >= 0.10.14 gstreamer-base-0.10 >= 0.10.14) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the GST_CFLAGS and GST_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.


I'm missing gstreamer-0.10...  and Here I'm lost...  I have lots of gstreamer installed... 

Please guys can someone tell me how can I enable what BMPX is missing to compile?

Honestly I have to say that installing things on linux is an endless fight...  I get depressed!!!
:cry::cry::cry::cry::cry:

---

### Post by Perfect Storm on 2007-10-15
That's why we have .deb packages for those who doesn't want to wrestle with source codes. Use them instead or better yet use Synaptic or add/remove.

---

### Post by Kosimo on 2007-10-15
> **Artificial Intelligence said:**
> That's why we have .deb packages for those who doesn't want to wrestle with source codes. Use them instead or better yet use Synaptic or add/remove.

Yes I know.
From apt-get I can easily install BMPX. The only problem is that the current version in repository is 0.36.1. Not the one I want.
Then I know getdeb.net witch have a newest version: 0.40.1 witch is still old.
I want to install the latest one 0.40.12 and I'm having troubles.
That's why I'm asking for help here.
I think this is the right place to ask... Isn't? :confused:

---

### Post by Perfect Storm on 2007-10-15
It needs newer libs than Feisty can provide. You can now a) wait for Ubuntu 7.10 (in a couple of days) or try another player. I would recommend audacious, I have plenty of success to compile that from source.

[http://audacious-media-player.org/index.php?title=Main_Page](http://audacious-media-player.org/index.php?title=Main_Page)

> I think this is the right place to ask... Isn't? 
Well, yeah. My reply was for the little rant you made in the end of your post ;)

---

### Post by Kosimo on 2007-10-15
> **Artificial Intelligence said:**
> It needs newer libs than Feisty can provide. You can now a) wait for Ubuntu 7.10 (in a couple of days) or try another player. I would recommend audacious, I have plenty of success to compile that from source.

[http://audacious-media-player.org/index.php?title=Main_Page](http://audacious-media-player.org/index.php?title=Main_Page)

[
Well, yeah. My reply was for the little rant you made in the end of your post ;)

Thanks for your answer.
So, if I follow the same procedure in Gutsy it should work right away?
About audacious I actually use it and I like it. I will try the new 1.4 Beta witch was released today!
But I need a media library witch Audacious doesn't have.

> Well, yeah. My reply was for the little rant you made in the end of your post 
Sorry for the Flame, I know I have to make a bigger effort.. Is just that sometimes I get depressed when I try, and try and try with no results! Anyway today I got one. :KS

---

### Post by Perfect Storm on 2007-10-15
No problem :)

Report back when you tried it on Gutsy, good luck.


regards
A.I. Dude

---

### Post by Kosimo on 2007-10-15
Here I am again...

Now from Gutsy RC (updated)

still same problems, missing some libraries but I installed them one by one.

After ./configure  I got this:

> BMPx Build Configuration
========================

    C compiler flags.............: -g -O2 -std=c99 -pedantic  -fno-strict-aliasing -fmessage-length=0 -Wall -D_FORTIFY_SOURCE=2
    C++ compiler flags...........: -g -O2  -fno-strict-aliasing -fmessage-length=0 -Wall -D_FORTIFY_SOURCE=2
    Linker flags.................:  -Wl,--as-needed -Wl,-O1
      ** Linker workarounds are disabled. Do *NOT* report *ANY* linking errors
      ** when building with gcc 4.0.X - 4.2.1 and binutils >=2.17.X.

    Documentation generation.....: no

    Audio: Default Sink..........: alsasink (device default)

    X Session Management.........: yes
    Startup-notification Support.: yes
    HAL Storage Management.......: no
    Optional taglib plugins......:


Now I get the point to (make)  
this is the result:

> cosimo@cosimo-laptop:~/Desktop/b$ make
/home/cosimo/Desktop/b/mkbuild_h.sh /home/cosimo/Desktop/b /home/cosimo/Desktop/b
Generating build.h
/home/cosimo/Desktop/b/mkrevision_h.sh /home/cosimo/Desktop/b /home/cosimo/Desktop/b
make  all-recursive
make[1]: Entering directory `/home/cosimo/Desktop/b'
Making all in debian
make[2]: Entering directory `/home/cosimo/Desktop/b/debian'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/cosimo/Desktop/b/debian'
Making all in scripts
make[2]: Entering directory `/home/cosimo/Desktop/b/scripts'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/cosimo/Desktop/b/scripts'
Making all in po
make[2]: Entering directory `/home/cosimo/Desktop/b/po'
file=`echo af | sed 's,.*/,,'`.gmo \
          && rm -f $file &&  -o $file af.po
/bin/sh: -o: not found
make[2]: *** [af.gmo] Error 127
make[2]: Leaving directory `/home/cosimo/Desktop/b/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/cosimo/Desktop/b'
make: *** [all] Error 2


I've got some errors here, but I tried to continue with sudo checkinstall

> cosimo@cosimo-laptop:~/Desktop/b$ sudo checkinstall
[sudo] password for cosimo:

checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist. 
Should I create a default set of package docs?  [y]: y

Preparing package documentation...OK

Please write a description for the package.
End your description with an empty line or EOF.
>> bmpx
>> 

*****************************************
**** Debian package creation selected ***
*****************************************

*** Warning: The package version "0.40.12
0.40.12
0.40.12
0.40.12
0.40.12
0.40.12
0.40.12
0.40.12
0.40.12
0.40.12
0.40.12" is not a
*** Warning: debian policy compliant one. Please specify an alternate one


This package will be built according to these values: 

0 -  Maintainer: [ root@cosimo-laptop ]
1 -  Summary: [ bmpx ]
2 -  Name:    [ b ]
3 -  Version: [  ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ b ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
/home/cosimo/Desktop/b/mkrevision_h.sh /home/cosimo/Desktop/b /home/cosimo/Desktop/b
make  install-recursive
make[1]: Entering directory `/home/cosimo/Desktop/b'
Making install in debian
make[2]: Entering directory `/home/cosimo/Desktop/b/debian'
make[3]: Entering directory `/home/cosimo/Desktop/b/debian'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/cosimo/Desktop/b/debian'
make[2]: Leaving directory `/home/cosimo/Desktop/b/debian'
Making install in scripts
make[2]: Entering directory `/home/cosimo/Desktop/b/scripts'
make[3]: Entering directory `/home/cosimo/Desktop/b/scripts'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/cosimo/Desktop/b/scripts'
make[2]: Leaving directory `/home/cosimo/Desktop/b/scripts'
Making install in po
make[2]: Entering directory `/home/cosimo/Desktop/b/po'
file=`echo af | sed 's,.*/,,'`.gmo \
          && rm -f $file &&  -o $file af.po
/bin/sh: -o: not found
make[2]: *** [af.gmo] Error 127
make[2]: Leaving directory `/home/cosimo/Desktop/b/po'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/cosimo/Desktop/b'
make: *** [install] Error 2

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.



This is getting difficult!    What I'm doing wrong?

Thank you guys... :(

---

### Post by Rui Pais on 2007-10-15
why do you give up the previous thread [http://ubuntuforums.org/showthread.php?p=3496796#post3496796](http://ubuntuforums.org/showthread.php?p=3496796#post3496796) ?
It's difficult to see what you have done with things in 2 different threads...

About your last post, don't go to checkinstall until you finish compilation (the make step) with success , no errors in the output. 

from your post i don't get if ./configure end up with success or stopped  at taglib plugins dependencies... 
it's the same thing, if ./configure don't finish with success don't proceed any further. You need some -dev package. 
My previous list was for Feisty, if you want i can try to compile it under gutsy and check the dependencies on it.

---

### Post by Perfect Storm on 2007-10-15
> HAL Storage Management.......: no
Optional taglib plugins......:

you're missing -dev of libhal and taglib (to get most out of it).

---

### Post by Kosimo on 2007-10-15
> **Rui Pais said:**
> why do you give up the previous thread [http://ubuntuforums.org/showthread.php?p=3496796#post3496796](http://ubuntuforums.org/showthread.php?p=3496796#post3496796) ?
It's difficult to see what you have done with things in 2 different threads...

About your last post, don't go to checkinstall until you finish compilation (the make step) with success , no errors in the output. 

from your post i don't get if ./configure end up with success or stopped  at taglib plugins dependencies... 
it's the same thing, if ./configure don't finish with success don't proceed any further. You need some -dev package. 
My previous list was for Feisty, if you want i can try to compile it under gutsy and check the dependencies on it.

Hey Rui Pais!  
Sorry so much. I didn't read your last post in that topic! 	#-o Desculpe!

(As you can see, I'm still trying to install this d*** program)  
Let's hope this time will be the right one.

I'm going to paste everything since the beginning:

./configure

> cosimo@cosimo-laptop:~$ cd Desktop
cosimo@cosimo-laptop:~/Desktop$ cd b
cosimo@cosimo-laptop:~/Desktop/b$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for library containing strerror... none required
checking whether we are using the GNU C++ compiler... (cached) yes
checking whether g++ accepts -g... (cached) yes
checking dependency style of g++... (cached) gcc3
checking whether g++ understands -c and -o together... yes
checking for gawk... (cached) mawk
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking whether gcc and cc understand -c and -o together... yes
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking how to run the C++ preprocessor... g++ -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking for working alloca.h... yes
checking for alloca... yes
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking for ANSI C header files... (cached) yes
checking argz.h usability... yes
checking argz.h presence... yes
checking for argz.h... yes
checking arpa/inet.h usability... yes
checking arpa/inet.h presence... yes
checking for arpa/inet.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking float.h usability... yes
checking float.h presence... yes
checking for float.h... yes
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
checking netdb.h usability... yes
checking netdb.h presence... yes
checking for netdb.h... yes
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
checking wchar.h usability... yes
checking wchar.h presence... yes
checking for wchar.h... yes
checking for stdbool.h that conforms to C99... yes
checking for _Bool... no
checking for an ANSI C-conforming const... yes
checking for uid_t in sys/types.h... yes
checking for inline... inline
checking for mode_t... yes
checking for off_t... yes
checking for pid_t... yes
checking for size_t... yes
checking whether time.h and sys/time.h may both be included... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for working volatile... yes
checking for ptrdiff_t... yes
checking for error_at_line... yes
checking vfork.h usability... no
checking vfork.h presence... no
checking for vfork.h... no
checking for fork... yes
checking for vfork... yes
checking for working fork... yes
checking for working vfork... (cached) yes
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
checking whether lstat dereferences a symlink specified with a trailing slash... yes
checking whether stat accepts an empty string... no
checking for strftime... yes
checking for vprintf... yes
checking for _doprnt... no
checking for __argz_count... yes
checking for __argz_next... yes
checking for __argz_stringify... yes
checking for dup2... yes
checking for fdatasync... yes
checking for ftime... yes
checking for ftruncate... yes
checking for getcwd... yes
checking for gethostbyname... yes
checking for gettimeofday... yes
checking for localtime_r... yes
checking for mempcpy... yes
checking for memset... yes
checking for mkdir... yes
checking for munmap... yes
checking for nl_langinfo... yes
checking for rmdir... yes
checking for select... yes
checking for setlocale... yes
checking for socket... yes
checking for stpcpy... yes
checking for strcasecmp... yes
checking for strchr... yes
checking for strcspn... yes
checking for strdup... yes
checking for strerror... yes
checking for strncasecmp... yes
checking for strrchr... yes
checking for strstr... yes
checking for strtol... yes
checking for strtoul... yes
checking for memmem... yes
checking for access... yes
checking for int... yes
checking size of int... 4
checking for long... yes
checking size of long... 4
checking for short... yes
checking size of short... 2
checking for long long... yes
checking size of long long... 8
checking for library containing connect... none required
checking for library containing getrpcbyname... none required
checking for intltool >= 0.35.0... 0.36.2 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for locale.h... (cached) yes
checking for LC_MESSAGES... yes
checking for libintl.h... (cached) yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... no
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking how to recognize dependent libraries... pass_all
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking how to run the C++ preprocessor... g++ -E
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
checking whether to build static libraries... no
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
checking whether /usr/bin/ld accepts --as-needed... yes
checking whether /usr/bin/ld accepts -O1... yes
checking for X... libraries , headers 
checking for gethostbyname... (cached) yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for boostlib >= 1.33.1... yes
checking whether the Boost::Filesystem library is available... no
checking whether the Boost::Regex library is available... yes
checking for exit in -lboost_regex-gcc41-1_34_1... yes
checking whether the Boost::IOStreams library is available... yes
checking for exit in -lboost_iostreams-gcc41-1_34_1... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for SOUP... yes
checking for extern in libsoup headers... no
checking for SQLITE... yes
checking for SQLite3 library >= 3.3.11... yes
checking for GLIB... yes
checking for GLIBMM... yes
checking for SIGC... yes
checking for GTK... yes
checking for RSVG... yes
checking for GTKMM... yes
checking for GLADEMM... yes
checking for CAIROMM... yes
checking for _init in -lsexymm... yes
checking for XML... yes
checking for GST... yes
checking for GST_PLUGINS_BASE... yes
checking for DBUS... yes
checking for TAGLIB... yes
checking for SmcOpenConnection in -lSM... yes
checking for STARTUP_NOTIFY... yes
checking for zip... zip
checking for LIBOFA... yes
checking for ALSA... yes
checking cdda_interface.h usability... yes
checking cdda_interface.h presence... yes
checking for cdda_interface.h... yes
checking for cdda_open in -lcdda_interface... yes
checking for XPROTO... yes
checking for xsltproc... xsltproc
configure: creating ./config.status
config.status: creating Makefile
config.status: creating scripts/Makefile
config.status: creating include/Makefile
config.status: creating include/bmp/Makefile
config.status: creating include/bmp/types/Makefile
config.status: creating include/bmp/dbus.hh
config.status: creating remote/Makefile
config.status: creating sentinel/Makefile
config.status: creating widgets/Makefile
config.status: creating libhal++/Makefile
config.status: creating mcs/Makefile
config.status: creating jnetlib/Makefile
config.status: creating json/Makefile
config.status: creating src/Makefile
config.status: creating src/parser/Makefile
config.status: creating src/musicbrainz/Makefile
config.status: creating src/audio/Makefile
config.status: creating src/dbus-obj-BMP.xml
config.status: creating src/dbus-obj-root.xml
config.status: creating src/dbus-obj-player.xml
config.status: creating src/dbus-obj-tracklist.xml
config.status: creating plugins/Makefile
config.status: creating plugins/vfs/Makefile
config.status: creating plugins/vfs/container/Makefile
config.status: creating plugins/vfs/transport/Makefile
config.status: creating plugins/taglib/Makefile
config.status: creating plugins/taglib/id3v2/Makefile
config.status: creating plugins/taglib/xiph/Makefile
config.status: creating plugins/taglib/common/Makefile
config.status: creating plugins/taglib/mp4/Makefile
config.status: creating plugins/taglib/asf/Makefile
config.status: creating plugins/taglib/sid/Makefile
config.status: creating plugins/taglib/mod/Makefile
config.status: creating plugins/taglib/ogg/Makefile
config.status: creating plugins/taglib/flac/Makefile
config.status: creating plugins/taglib/mp3/Makefile
config.status: creating plugins/taglib/mpc/Makefile
config.status: creating data/Makefile
config.status: creating data/glade/Makefile
config.status: creating data/icons/Makefile
config.status: creating data/icons/tray-icons/Makefile
config.status: creating data/icons/themes/Makefile
config.status: creating data/icons/themes/plastic/Makefile
config.status: creating data/icons/themes/display/Makefile
config.status: creating data/icons/themes/red/Makefile
config.status: creating data/icons/themes/tango/Makefile
config.status: creating data/icons/themes/darksphere/Makefile
config.status: creating data/images/Makefile
config.status: creating data/images/cdda/Makefile
config.status: creating data/images/lastfm/Makefile
config.status: creating data/images/main/Makefile
config.status: creating data/images/podcast/Makefile
config.status: creating data/images/svg/Makefile
config.status: creating data/images/rating/Makefile
config.status: creating data/images/sources/Makefile
config.status: creating data/images/stock/Makefile
config.status: creating data/desktop/Makefile
config.status: creating data/desktop/bmp-2.0.desktop
config.status: creating data/desktop/bmp-2.0-offline.desktop
config.status: creating data/desktop/bmp-play-2.0.desktop
config.status: creating xpi/Makefile
config.status: creating xpi/chrome/content/bmp/BMPOverlay.js
config.status: creating xpi/chrome/Makefile
config.status: creating xpi/chrome/skin/Makefile
config.status: creating xpi/chrome/skin/classic/Makefile
config.status: creating xpi/chrome/skin/classic/bmp/Makefile
config.status: creating xpi/chrome/content/Makefile
config.status: creating xpi/chrome/content/bmp/Makefile
config.status: creating po/Makefile.in
config.status: creating docs/Makefile
config.status: creating docs/images/Makefile
config.status: creating docs/chapters/Makefile
config.status: creating docs/xsl/Makefile
config.status: creating docs/xsl/bump.xsl
config.status: creating debian/Makefile
config.status: creating bmp-2.0.pc
config.status: creating beep-media-player-2.1
config.status: creating bmpx.spec
config.status: creating config.h
config.status: executing depfiles commands
config.status: executing intltool commands
config.status: executing default-1 commands
config.status: executing po/stamp-it commands

BMPx Build Configuration
========================

    C compiler flags.............: -g -O2 -std=c99 -pedantic  -fno-strict-aliasing -fmessage-length=0 -Wall -D_FORTIFY_SOURCE=2
    C++ compiler flags...........: -g -O2  -fno-strict-aliasing -fmessage-length=0 -Wall -D_FORTIFY_SOURCE=2
    Linker flags.................:  -Wl,--as-needed -Wl,-O1
      ** Linker workarounds are disabled. Do *NOT* report *ANY* linking errors
      ** when building with gcc 4.0.X - 4.2.1 and binutils >=2.17.X.

    Documentation generation.....: no

    Audio: Default Sink..........: alsasink (device default)

    X Session Management.........: yes
    Startup-notification Support.: yes
    HAL Storage Management.......: no
    Optional taglib plugins......:
cosimo@cosimo-laptop:~/Desktop/b$ 



./make

> cosimo@cosimo-laptop:~/Desktop/b$ make
/home/cosimo/Desktop/b/mkbuild_h.sh /home/cosimo/Desktop/b /home/cosimo/Desktop/b
Generating build.h
/home/cosimo/Desktop/b/mkrevision_h.sh /home/cosimo/Desktop/b /home/cosimo/Desktop/b
make  all-recursive
make[1]: Entering directory `/home/cosimo/Desktop/b'
Making all in debian
make[2]: Entering directory `/home/cosimo/Desktop/b/debian'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/cosimo/Desktop/b/debian'
Making all in scripts
make[2]: Entering directory `/home/cosimo/Desktop/b/scripts'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/cosimo/Desktop/b/scripts'
Making all in po
make[2]: Entering directory `/home/cosimo/Desktop/b/po'
file=`echo af | sed 's,.*/,,'`.gmo \
          && rm -f $file &&  -o $file af.po
/bin/sh: -o: not found
make[2]: *** [af.gmo] Error 127
make[2]: Leaving directory `/home/cosimo/Desktop/b/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/cosimo/Desktop/b'
make: *** [all] Error 2


---

### Post by Rui Pais on 2007-10-15
No problem Kosimo :) 
i assumed that meanwhile you have managed to compile it... sorry to hear you still have problems.

In theory configure finished without errors. Those references not founded, should be optional stuff... but, if i remember well, bmpx configuration not always list all dependencies correctly and some of them, listed as optional, was in fact needed. 
Try to install the suggested by Artificial Intelligence, then do a:
```
make clean
```
before the
```
./configure
```
I will try to compile under gutsy and let you know how it goes, ok.

---

### Post by Kosimo on 2007-10-15
> **Rui Pais said:**
> No problem Kosimo :) 
i assumed that meanwhile you have managed to compile it... sorry to hear you still have problems.

In theory configure finished without errors. Those references not founded, should be optional stuff... but, if i remember well, bmpx configuration not always list all dependencies correctly and some of them, listed as optional, was in fact needed. 
Try to install the suggested by Artificial Intelligence, then do a:
```
make clean
```
before the
```
./configure
```
I will try to compile under gutsy and let you know how it goes, ok.


Looking forward to know how it goes for you.

About me, following Artificial I did install the -dev of -dev of libhal. But I couldn't find anything related with taglib searching it in synaptic I get no results.
I tried to do it again following your instructions (make clean) but the result is still the same.
So, I guess I'll wait till you try it. Then I'm sure we'll get the answer.
Obrigado ;)

---

### Post by Perfect Storm on 2007-10-15
In ubuntu it called libtag.

To get a better view run first ./configure --help to see what options are available.

---

### Post by sethvath on 2007-10-15
I tried compiling 2 days ago, crashed the moment I start bmpx. 

The offline player works, online doesnt work. If anyone wants the deb I can upload it somewhere. For my case I used ./configure --prefix=/usr --disable-hal to compile without hal support. Tried with and without hal, same crash error.

---

### Post by Rui Pais on 2007-10-15
Ok, i compile it under gutsy. 
No need for hal or taglib -dev, they are optional.

Theres a missing on my previous list of dependencies, libgstreamer-plugins-base0.10-dev, i must have forget that one when i write it on your other thread. Appart from that it's the same for 0.40.12/gutsy.
Here it is:
```
 sudo apt-get install boost-build libboost-dev libboost-regex-dev libboost-iostreams-dev libboost-thread-dev libsoup2.2-dev libglibmm-2.4-dev librsvg2-dev libgtkmm2.0-dev libgtkmm-2.4-dev libglademm-2.4-dev libsexymm-dev libgstreamer-plugins-base0.10-dev libgstreamer0.10-dev libdbus-1-dev libdbus-glib-1-dev libstartup-notification0-dev libofa0-dev libcdparanoia0-dev
```

Maybe it's better start from a fresh one, deleting your bmpx code folder, unzip it again, then copy past all of the above to the terminal navigate to bmpx folder, ./configure, make and sudo checkinstall.

Don't forget, post if any of those commands fail. 

Good Luck

---

### Post by Rui Pais on 2007-10-15
> **sethvath said:**
> I tried compiling 2 days ago, crashed the moment I start bmpx. 

The offline player works, online doesnt work. If anyone wants the deb I can upload it somewhere. For my case I used ./configure --prefix=/usr --disable-hal to compile without hal support. Tried with and without hal, same crash error.

I just launched here, i didn't try to play offline music... It crashes too. 
To solve that you need to install plugins and some extra packages:
gstreamer0.10-ffmpeg (0.10.2-2ubuntu1)
gstreamer0.10-fluendo-mpegdemux (0.10.12-0ubuntu1)
gstreamer0.10-plugins-ugly (0.10.6-0ubuntu2)
liba52-0.7.4 (0.7.4-11)
libmpeg2-4 (0.4.1-1)
libsidplay1 (1.36.59-4)

hth


PS i compiled without hal support and with a plain ./configure (no flags)

---

### Post by sethvath on 2007-10-15
"BMPx tried to start up but crashed" This is my 6th compile, doesnt seem to work on gutsy. Anyone able to compile and verify that it is working?

---

### Post by Rui Pais on 2007-10-15
> **sethvath said:**
> "BMPx tried to start up but crashed" This is my 6th compile, doesnt seem to work on gutsy. Anyone able to compile and verify that it is working?

have you seen my last 2 posts ;)

[ATTACH]46411[/ATTACH]

---

### Post by sethvath on 2007-10-15
Exact same error. Crashed when starting up.

---

### Post by Rui Pais on 2007-10-15
> **sethvath said:**
> Exact same error. Crashed when starting up.

even with gstreamer0.10-ffmpeg gstreamer0.10-fluendo-mpegdemux gstreamer0.10-plugins-ugly liba52-0.7.4 libmpeg2-4 libsidplay1 ? 

Btw i compiled under 64bits, if anyone interested in that arch i can upload a deb.

---

### Post by sethvath on 2007-10-15
Yes, I followed your last 2 posts. Doing 1 final compile without hal before I give up.

---

### Post by sethvath on 2007-10-15
Still doesnt work. Reverting to the 0.40 in the gutsy repo. 

If anyone wishes to share an i386 deb please upload it to [www.zshare.com](www.zshare.com)

---

### Post by Rui Pais on 2007-10-15
> **sethvath said:**
> Still doesnt work.

Humm, maybe trying to remove any config file and start from fresh:
```
rm -rf ~/.local/share/bmpx
rm -rf ~/.config/bmpx
```

---

### Post by Kosimo on 2007-10-15
> **Rui Pais said:**
> Ok, i compile it under gutsy. 
No need for hal or taglib -dev, they are optional.

Theres a missing on my previous list of dependencies, libgstreamer-plugins-base0.10-dev, i must have forget that one when i write it on your other thread. Appart from that it's the same for 0.40.12/gutsy.
Here it is:
```
 sudo apt-get install boost-build libboost-dev libboost-regex-dev libboost-iostreams-dev libboost-thread-dev libsoup2.2-dev libglibmm-2.4-dev librsvg2-dev libgtkmm2.0-dev libgtkmm-2.4-dev libglademm-2.4-dev libsexymm-dev libgstreamer-plugins-base0.10-dev libgstreamer0.10-dev libdbus-1-dev libdbus-glib-1-dev libstartup-notification0-dev libofa0-dev libcdparanoia0-dev
```

Maybe it's better start from a fresh one, deleting your bmpx code folder, unzip it again, then copy past all of the above to the terminal navigate to bmpx folder, ./configure, make and sudo checkinstall.

Don't forget, post if any of those commands fail. 

Good Luck

Hey! I'm back ;)

Well, I tried to install the new list of dependencies you just gave me, but I had all of them already. So I didn't update anyone and of course I'm still having the same problem.

Did you do something different?  

ps:I tried to ./configure from a new archive.

Obrigado ;)

---

### Post by Rui Pais on 2007-10-15
> **Kosimo said:**
> Hey! I'm back ;)

Well, I tried to install the new list of dependencies you just gave me, but I had all of them already. So I didn't update anyone and of course I'm still having the same problem.

Did you do something different?  
i'm starting to think i'm a lucky guy :(
I just installed the list i give to you and done a plain ./configure on bmpx unzipped folder ...

> ps:I tried to ./configure from a new archive.

Obrigado ;)

so the error happen with a fresh new code folder? In that case don't know what else suggest... do you have 32 or 64bits install?

de nada pelo obrigado, pelo menos até agora  (don't know how to say it in Catalan, but i suspect that you can read my Portuguese and i would understand the Catalan version :) we have close languages)

---

### Post by sethvath on 2007-10-15
Finally got it working I had a missing dependency somewhere. 

```
sudo apt-get install libboost-dev libboost-filesystem-dev libboost-regex-dev libboost-iostreams-dev libdbus-1-dev libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev gstreamer0.10-ffmpeg gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly gstreamer0.10-plugins-bad libtag1-dev libgtkmm-2.4-dev libglademm-2.4-dev libstartup-notification0-dev libasound2-dev libcdparanoia0-dev libsoup2.2-dev libsqlite3-dev librsvg2-dev libsexymm-dev libofa0-dev libdbus-glib-1-dev gettext
```

Thanks for the help Rui :D

---

### Post by Rui Pais on 2007-10-15
> **Kosimo said:**
> 
```
cosimo@cosimo-laptop:~/Desktop/b$ make
/home/cosimo/Desktop/b/mkbuild_h.sh /home/cosimo/Desktop/b /home/cosimo/Desktop/b
Generating build.h
/home/cosimo/Desktop/b/mkrevision_h.sh /home/cosimo/Desktop/b /home/cosimo/Desktop/b
make all-recursive
make[1]: Entering directory `/home/cosimo/Desktop/b'
Making all in debian
make[2]: Entering directory `/home/cosimo/Desktop/b/debian'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/cosimo/Desktop/b/debian'
Making all in scripts
make[2]: Entering directory `/home/cosimo/Desktop/b/scripts'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/cosimo/Desktop/b/scripts'
Making all in po
make[2]: Entering directory `/home/cosimo/Desktop/b/po'
file=`echo af | sed 's,.*/,,'`.gmo \
&& rm -f $file && -o $file af.po
/bin/sh: -o: not found
make[2]: *** [af.gmo] Error 127
make[2]: Leaving directory `/home/cosimo/Desktop/b/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/cosimo/Desktop/b'
make: *** [all] Error 2 
```

btw why noted you run from a folder named 'b' and the error seems related to a bash/script action... maybe it don't like the rename of the folder. Try to uncompress the code to a folder without change the name, should be /bmpx-0.40.12/

good luck

---

### Post by Rui Pais on 2007-10-15
> **sethvath said:**
> Finally got it working I had a missing dependency somewhere. 

```
sudo apt-get install libboost-dev libboost-filesystem-dev libboost-regex-dev libboost-iostreams-dev libdbus-1-dev libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev gstreamer0.10-ffmpeg gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly gstreamer0.10-plugins-bad libtag1-dev libgtkmm-2.4-dev libglademm-2.4-dev libstartup-notification0-dev libasound2-dev libcdparanoia0-dev libsoup2.2-dev libsqlite3-dev librsvg2-dev libsexymm-dev libofa0-dev libdbus-glib-1-dev gettext
```
Thanks for the help Rui :D

Glad to know it's working. Great :)

do you copied the dependency list from the old thread of Kosimo? i don't know if in feisty the libgstreamer-plugins-base0.10-dev it's needed or it's a laps of me... 
(i will check and correct there)

---

### Post by Kosimo on 2007-10-15
> **Rui Pais said:**
> i'm starting to think i'm a lucky guy :(
I just installed the list i give to you and done a plain ./configure on bmpx unzipped folder ...



so the error happen with a fresh new code folder? In that case don't know what else suggest... do you have 32 or 64bits install?

de nada pelo obrigado, pelo menos até agora  (don't know how to say it in Catalan, but i suspect that you can read my Portuguese and i would understand the Catalan version :) we have close languages)


Did again from the normal folder name, (btw I changed just go find it easily from terminal) and is still not working... I really don't understand it. Fresh new gutsy, updated with all libraries installed...

Again, this is what I get after ./configure:

> cosimo@cosimo-laptop:~$ cd Desktop
cosimo@cosimo-laptop:~/Desktop$ cd bmpx-0.40.12
cosimo@cosimo-laptop:~/Desktop/bmpx-0.40.12$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for library containing strerror... none required
checking whether we are using the GNU C++ compiler... (cached) yes
checking whether g++ accepts -g... (cached) yes
checking dependency style of g++... (cached) gcc3
checking whether g++ understands -c and -o together... yes
checking for gawk... (cached) mawk
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking whether gcc and cc understand -c and -o together... yes
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking how to run the C++ preprocessor... g++ -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking for working alloca.h... yes
checking for alloca... yes
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking for ANSI C header files... (cached) yes
checking argz.h usability... yes
checking argz.h presence... yes
checking for argz.h... yes
checking arpa/inet.h usability... yes
checking arpa/inet.h presence... yes
checking for arpa/inet.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking float.h usability... yes
checking float.h presence... yes
checking for float.h... yes
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
checking netdb.h usability... yes
checking netdb.h presence... yes
checking for netdb.h... yes
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
checking wchar.h usability... yes
checking wchar.h presence... yes
checking for wchar.h... yes
checking for stdbool.h that conforms to C99... yes
checking for _Bool... no
checking for an ANSI C-conforming const... yes
checking for uid_t in sys/types.h... yes
checking for inline... inline
checking for mode_t... yes
checking for off_t... yes
checking for pid_t... yes
checking for size_t... yes
checking whether time.h and sys/time.h may both be included... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for working volatile... yes
checking for ptrdiff_t... yes
checking for error_at_line... yes
checking vfork.h usability... no
checking vfork.h presence... no
checking for vfork.h... no
checking for fork... yes
checking for vfork... yes
checking for working fork... yes
checking for working vfork... (cached) yes
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
checking whether lstat dereferences a symlink specified with a trailing slash... yes
checking whether stat accepts an empty string... no
checking for strftime... yes
checking for vprintf... yes
checking for _doprnt... no
checking for __argz_count... yes
checking for __argz_next... yes
checking for __argz_stringify... yes
checking for dup2... yes
checking for fdatasync... yes
checking for ftime... yes
checking for ftruncate... yes
checking for getcwd... yes
checking for gethostbyname... yes
checking for gettimeofday... yes
checking for localtime_r... yes
checking for mempcpy... yes
checking for memset... yes
checking for mkdir... yes
checking for munmap... yes
checking for nl_langinfo... yes
checking for rmdir... yes
checking for select... yes
checking for setlocale... yes
checking for socket... yes
checking for stpcpy... yes
checking for strcasecmp... yes
checking for strchr... yes
checking for strcspn... yes
checking for strdup... yes
checking for strerror... yes
checking for strncasecmp... yes
checking for strrchr... yes
checking for strstr... yes
checking for strtol... yes
checking for strtoul... yes
checking for memmem... yes
checking for access... yes
checking for int... yes
checking size of int... 4
checking for long... yes
checking size of long... 4
checking for short... yes
checking size of short... 2
checking for long long... yes
checking size of long long... 8
checking for library containing connect... none required
checking for library containing getrpcbyname... none required
checking for intltool >= 0.35.0... 0.36.2 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for locale.h... (cached) yes
checking for LC_MESSAGES... yes
checking for libintl.h... (cached) yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... no
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking how to recognize dependent libraries... pass_all
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking how to run the C++ preprocessor... g++ -E
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
checking whether to build static libraries... no
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
checking whether /usr/bin/ld accepts --as-needed... yes
checking whether /usr/bin/ld accepts -O1... yes
checking for X... libraries , headers 
checking for gethostbyname... (cached) yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for boostlib >= 1.33.1... yes
checking whether the Boost::Filesystem library is available... no
checking whether the Boost::Regex library is available... yes
checking for exit in -lboost_regex-gcc41-1_34_1... yes
checking whether the Boost::IOStreams library is available... yes
checking for exit in -lboost_iostreams-gcc41-1_34_1... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for SOUP... yes
checking for extern in libsoup headers... no
checking for SQLITE... yes
checking for SQLite3 library >= 3.3.11... yes
checking for GLIB... yes
checking for GLIBMM... yes
checking for SIGC... yes
checking for GTK... yes
checking for RSVG... yes
checking for GTKMM... yes
checking for GLADEMM... yes
checking for CAIROMM... yes
checking for _init in -lsexymm... yes
checking for XML... yes
checking for GST... yes
checking for GST_PLUGINS_BASE... yes
checking for DBUS... yes
checking for HAL... yes
checking for TAGLIB... yes
checking for SmcOpenConnection in -lSM... yes
checking for STARTUP_NOTIFY... yes
checking for zip... zip
checking for LIBOFA... yes
checking for ALSA... yes
checking cdda_interface.h usability... yes
checking cdda_interface.h presence... yes
checking for cdda_interface.h... yes
checking for cdda_open in -lcdda_interface... yes
checking for XPROTO... yes
checking for xsltproc... xsltproc
configure: creating ./config.status
config.status: creating Makefile
config.status: creating scripts/Makefile
config.status: creating include/Makefile
config.status: creating include/bmp/Makefile
config.status: creating include/bmp/types/Makefile
config.status: creating include/bmp/dbus.hh
config.status: creating remote/Makefile
config.status: creating sentinel/Makefile
config.status: creating widgets/Makefile
config.status: creating libhal++/Makefile
config.status: creating mcs/Makefile
config.status: creating jnetlib/Makefile
config.status: creating json/Makefile
config.status: creating src/Makefile
config.status: creating src/parser/Makefile
config.status: creating src/musicbrainz/Makefile
config.status: creating src/audio/Makefile
config.status: creating src/dbus-obj-BMP.xml
config.status: creating src/dbus-obj-root.xml
config.status: creating src/dbus-obj-player.xml
config.status: creating src/dbus-obj-tracklist.xml
config.status: creating plugins/Makefile
config.status: creating plugins/vfs/Makefile
config.status: creating plugins/vfs/container/Makefile
config.status: creating plugins/vfs/transport/Makefile
config.status: creating plugins/taglib/Makefile
config.status: creating plugins/taglib/id3v2/Makefile
config.status: creating plugins/taglib/xiph/Makefile
config.status: creating plugins/taglib/common/Makefile
config.status: creating plugins/taglib/mp4/Makefile
config.status: creating plugins/taglib/asf/Makefile
config.status: creating plugins/taglib/sid/Makefile
config.status: creating plugins/taglib/mod/Makefile
config.status: creating plugins/taglib/ogg/Makefile
config.status: creating plugins/taglib/flac/Makefile
config.status: creating plugins/taglib/mp3/Makefile
config.status: creating plugins/taglib/mpc/Makefile
config.status: creating data/Makefile
config.status: creating data/glade/Makefile
config.status: creating data/icons/Makefile
config.status: creating data/icons/tray-icons/Makefile
config.status: creating data/icons/themes/Makefile
config.status: creating data/icons/themes/plastic/Makefile
config.status: creating data/icons/themes/display/Makefile
config.status: creating data/icons/themes/red/Makefile
config.status: creating data/icons/themes/tango/Makefile
config.status: creating data/icons/themes/darksphere/Makefile
config.status: creating data/images/Makefile
config.status: creating data/images/cdda/Makefile
config.status: creating data/images/lastfm/Makefile
config.status: creating data/images/main/Makefile
config.status: creating data/images/podcast/Makefile
config.status: creating data/images/svg/Makefile
config.status: creating data/images/rating/Makefile
config.status: creating data/images/sources/Makefile
config.status: creating data/images/stock/Makefile
config.status: creating data/desktop/Makefile
config.status: creating data/desktop/bmp-2.0.desktop
config.status: creating data/desktop/bmp-2.0-offline.desktop
config.status: creating data/desktop/bmp-play-2.0.desktop
config.status: creating xpi/Makefile
config.status: creating xpi/chrome/content/bmp/BMPOverlay.js
config.status: creating xpi/chrome/Makefile
config.status: creating xpi/chrome/skin/Makefile
config.status: creating xpi/chrome/skin/classic/Makefile
config.status: creating xpi/chrome/skin/classic/bmp/Makefile
config.status: creating xpi/chrome/content/Makefile
config.status: creating xpi/chrome/content/bmp/Makefile
config.status: creating po/Makefile.in
config.status: creating docs/Makefile
config.status: creating docs/images/Makefile
config.status: creating docs/chapters/Makefile
config.status: creating docs/xsl/Makefile
config.status: creating docs/xsl/bump.xsl
config.status: creating debian/Makefile
config.status: creating bmp-2.0.pc
config.status: creating beep-media-player-2.1
config.status: creating bmpx.spec
config.status: creating config.h
config.status: executing depfiles commands
config.status: executing intltool commands
config.status: executing default-1 commands
config.status: executing po/stamp-it commands

BMPx Build Configuration
========================

    C compiler flags.............: -g -O2 -std=c99 -pedantic  -fno-strict-aliasing -fmessage-length=0 -Wall -D_FORTIFY_SOURCE=2
    C++ compiler flags...........: -g -O2  -fno-strict-aliasing -fmessage-length=0 -Wall -D_FORTIFY_SOURCE=2
    Linker flags.................:  -Wl,--as-needed -Wl,-O1
      ** Linker workarounds are disabled. Do *NOT* report *ANY* linking errors
      ** when building with gcc 4.0.X - 4.2.1 and binutils >=2.17.X.

    Documentation generation.....: no

    Audio: Default Sink..........: alsasink (device default)

    X Session Management.........: yes
    Startup-notification Support.: yes
    HAL Storage Management.......: yes
    Optional taglib plugins......:
cosimo@cosimo-laptop:~/Desktop/bmpx-0.40.12$


And this is what I get after make:

> cosimo@cosimo-laptop:~/Desktop/bmpx-0.40.12$ make
/home/cosimo/Desktop/bmpx-0.40.12/mkbuild_h.sh /home/cosimo/Desktop/bmpx-0.40.12 /home/cosimo/Desktop/bmpx-0.40.12
Generating build.h
/home/cosimo/Desktop/bmpx-0.40.12/mkrevision_h.sh /home/cosimo/Desktop/bmpx-0.40.12 /home/cosimo/Desktop/bmpx-0.40.12
make  all-recursive
make[1]: Entering directory `/home/cosimo/Desktop/bmpx-0.40.12'
Making all in debian
make[2]: Entering directory `/home/cosimo/Desktop/bmpx-0.40.12/debian'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/cosimo/Desktop/bmpx-0.40.12/debian'
Making all in scripts
make[2]: Entering directory `/home/cosimo/Desktop/bmpx-0.40.12/scripts'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/cosimo/Desktop/bmpx-0.40.12/scripts'
Making all in po
make[2]: Entering directory `/home/cosimo/Desktop/bmpx-0.40.12/po'
file=`echo af | sed 's,.*/,,'`.gmo \
          && rm -f $file &&  -o $file af.po
/bin/sh: -o: not found
make[2]: *** [af.gmo] Error 127
make[2]: Leaving directory `/home/cosimo/Desktop/bmpx-0.40.12/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/cosimo/Desktop/bmpx-0.40.12'
make: *** [all] Error 2
cosimo@cosimo-laptop:~/Desktop/bmpx-0.40.12$ 


Really confused....   I'm starting to think that you're not lucky, it's me who's unlucky..!!



-- Es clar que puc entendre el Portugés, ja que és una llengua llatina com el català. Tenim molts llaços lingüístics! Podem dir que som pobles germans ;)

---

### Post by Kosimo on 2007-10-15
By the way, can you please just print here what you get after ./configure?

I'm gonna try to compare it if I'm may missing some other dependence.

Gràcies des de Catalunya

---

### Post by sethvath on 2007-10-15
> **Rui Pais said:**
> Glad to know it's working. Great :)

do you copied the dependency list from the old thread of Kosimo? i don't know if in feisty the libgstreamer-plugins-base0.10-dev it's needed or it's a laps of me... 
(i will check and correct there)
Yes the libgstreamer plugin is required. I copied the list from the bmpx wiki. I had a bunch of things installed after verifying from the ./configure errors and there was 1 file from this list that I missed out on. 

Removing the config files and doing an "apt-get remove --purge bmpx" did the job for me. 

Kosimo, here's a deb. Try whether it works for you. [http://www.zshare.net/download/4235838b9d4a1a/](http://www.zshare.net/download/4235838b9d4a1a/)

---

### Post by Rui Pais on 2007-10-15
> **Kosimo said:**
> Did again from the normal folder name, (btw I changed just go find it easily from terminal) and is still not working... I really don't understand it. Fresh new gutsy, updated with all libraries installed...


Really confused....   I'm starting to think that you're not lucky, it's me who's unlucky..!!


i'm confused too... i'm running short in time, now. I'll look at it in a couple of hours and try to check whats failing (po files are files related with with translations... but you seems to run in English). btw in terminal to find paths/folders easyly just type 2~3 characters and then press TAB key to get the full name automatically. Easier then rename ;)

> 
-- Es clar que puc entendre el Portugés, ja que és una llengua llatina com el català. Tenim molts llaços lingüístics! Podem dir que som pobles germans ;)

Eh eh mais que uma língua latina, tem uma raiz comum nas linguas/dialetos da península ibérica, algures o arcaico galaico-português coexistia com o antepassado do que é actualmente o catalão. Por curiosidade, os 't' no final das palavras, em catalão são lidos ou mudos como no françês?
 
> **Kosimo said:**
> By the way, can you please just print here what you get after ./configure?

I'm gonna try to compare it if I'm may missing some other dependence.

Gràcies des de Catalunya
my config output it's exactly yours. The first one, without HAL. But that should not be the issue. Is somewhere on compilation...

I will try to see if i managed to understand. Meanwhile i can post a deb for 64bits and sethvath may give a i386.

'till soon

---

### Post by Kosimo on 2007-10-15
Didn't know about how to get the folder easily from the terminal.
I'm running on 32 bits, and I realize that I'm my ./configure I'm missing some things, like
checking vfork.h usability... no
checking vfork.h presence... no
checking for vfork.h... no

And some others. I'm gonna check it later.

Now I'm downloading the .deb thanks to sethvath. 

I'll be back later as well.

ps: Bé, ja saps que el català és una llengua romànica, com l'Italià, el Francés, El Castellà, El portugués, el romanés. Les llengües ibèriques que es parlàven abans del llatí ja fa molt de temps que han desaparegut! La nostra ( el català ) és un dialècte evolucionat del llatí, igual que ho són totes les altres llengües llatines.  I la resposta a la teva pregunta: EN català una paraula que acabi en T, aquesta última no es pronuncia. Per tant és muda.

---

### Post by Perfect Storm on 2007-10-15
Please keep it english ;)

If you're still interested in trying the latest audacious I'm putting a guide together.

---

### Post by Kosimo on 2007-10-15
Perfect!
The deb posted by sethvath works perfectly. Thank you sooo much.
The only thing that makes me sad... Is... I wasn't able to compile a simple program by myself.... Snif... :(

Anyway thanks so much guys for all the help received.

(When 0.40.13 will come out, I'll be here again trying again!)

---

### Post by Kosimo on 2007-10-15
> **Artificial Intelligence said:**
> Please keep it english ;)

If you're still interested in trying the latest audacious I'm putting a guide together.

Sure, we where talking about linguistics, too much OT that's true. ;)

Looking forward for reading your guide, surely I'll read and follow it. Also because Audacious 1.4 Beta as I said is out already.

Thanks again.

---

### Post by Kosimo on 2007-10-15
Aggghhh!!!!!!!!!

One of the main reasons that keeps me using BMPx is the EQ... Witch is not enabled in the sethvath's deb!!!! :'( !!!!!   Guess is some pluguin witch comes when compiling...

:( :(   

Well, starting again!   Hope to be able to compile it with all pluguins like EQ enabled!


Than you again guys

---

### Post by Perfect Storm on 2007-10-15
OT; Regarding Audacious (if you don't want it in this thread I'll remove it).

Tested in Feisty x86 gnome specific - enabled almost everything, just cut down what you don't need

Libs, tools:
```
sudo aptitude update && sudo aptitude upgrade
sudo aptitude install build-essential checkinstall mercurial autoconf automake autogen
sudo aptitude install bison gettext libgtk2.0-dev libgconf2-dev libglade2-dev libdbus-1-dev libglib2.0-dev libxml2-dev libsamplerate0-dev libmikmod2-dev libpulse-dev libmad0-dev liblircclient0 libgdk-pixbuf-dev libpng12-dev libfreetype6-dev libxinerama-dev libxrender-dev libxcomposite-dev libimlib2-dev libbinio-dev libvorbis-dev libflac-dev libflac++-dev libwavpack-dev libsndfile1-dev libtag1-dev libtagc0-dev libmpcdec-dev libjack0.100.0-dev libsidplay1-dev libasound2-dev libfluidsynth-dev libcdio-dev libcdio-paranoia-dev libcdio-cdda-dev libcddb2-dev libcurl3-dev libneon26-dev libmms-dev libmtp-dev libsdl1.2-dev liblame-dev libadplug-dev ladspa-sdk libaudio-dev
```

libmowgli:
```
cd ~/Desktop
hg clone http://hg.atheme-project.org/libmowgli libmowgli-devel
cd libmowgli-devel
sh autogen.sh
./configure --prefix=/usr
make
sudo make install
```

libmcs
```
cd ~/Desktop
hg clone http://hg.atheme.org/libmcs libmcs-devel
cd libmcs-devel
sh autogen.sh
./configure --prefix=/usr --enable-gconf
make
sudo make install
```


**Audacious**
```
cd ~/Desktop
tar zxfv audacious-1.4.0-beta1.tgz
cd audacious-1.4.0-beta1
./configure --enable-samplerate
make
sudo checkinstall
```

**Audacious Plugin**
```
cd ~/Desktop
tar zxfv audacious-plugins-1.4.0-beta1.tgz
cd audacious-plugins-1.4.0-beta1
./configure
make
sudo checkinstall
```


Found two errors which can be fixed with a little symblink and cp - remind it is still beta-ware.

```
cd ~/Desktop/audacious-1.4.0-beta1/src/libaudclient
sudo cp libaudclient.so /usr/lib/libaudclient.so.1.0.0
cd /usr/local/lib/audacious/Input
sudo ln -s /usr/local/lib/libaudid3tag.so.1.0.0 /usr/lib/libaudid3tag.so.1.0.0

```

I should properly prefixed audacious and its plugin. Oh well...

---

### Post by sethvath on 2007-10-15
Kosimo, you dont need a plugin for EQ. It is located in BMP > Preferences > Playback > Equalizer (check the box)

---

### Post by Kosimo on 2007-10-15
> **sethvath said:**
> Kosimo, you dont need a plugin for EQ. It is located in BMP > Preferences > Playback > Equalizer (check the box)

Yes, I Know where it is. 
But is disabled. Is gray and is not possible to hit.

---

### Post by Kosimo on 2007-10-15
> **Artificial Intelligence said:**
> OT; Regarding Audacious (if you don't want it in this thread I'll remove it).

Tested in Feisty x86 gnome specific - enabled almost everything, just cut down what you don't need

Libs, tools:
```
sudo aptitude update && sudo aptitude upgrade
sudo aptitude install build-essential checkinstall mercurial autoconf automake autogen
sudo aptitude install bison gettext libgtk2.0-dev libgconf2-dev libglade2-dev libdbus-1-dev libglib2.0-dev libxml2-dev libsamplerate0-dev libmikmod2-dev libpulse-dev libmad0-dev liblircclient0 libgdk-pixbuf-dev libpng12-dev libfreetype6-dev libxinerama-dev libxrender-dev libxcomposite-dev libimlib2-dev libbinio-dev libvorbis-dev libflac-dev libflac++-dev libwavpack-dev libsndfile1-dev libtag1-dev libtagc0-dev libmpcdec-dev libjack0.100.0-dev libsidplay1-dev libasound2-dev libfluidsynth-dev libcdio-dev libcdio-paranoia-dev libcdio-cdda-dev libcddb2-dev libcurl3-dev libneon26-dev libmms-dev libmtp-dev libsdl1.2-dev liblame-dev libadplug-dev ladspa-sdk libaudio-dev
```

libmowgli:
```
cd ~/Desktop
hg clone http://hg.atheme-project.org/libmowgli libmowgli-devel
cd libmowgli-devel
sh autogen.sh
./configure --prefix=/usr
make
sudo make install
```

libmcs
```
cd ~/Desktop
hg clone http://hg.atheme.org/libmcs libmcs-devel
cd libmcs-devel
sh autogen.sh
./configure --prefix=/usr --enable-gconf
make
sudo make install
```


**Audacious**
```
cd ~/Desktop
tar zxfv audacious-1.4.0-beta1.tgz
cd audacious-1.4.0-beta1
./configure --enable-samplerate
make
sudo checkinstall
```

**Audacious Plugin**
```
cd ~/Desktop
tar zxfv audacious-plugins-1.4.0-beta1.tgz
cd audacious-plugins-1.4.0-beta1
./configure
make
sudo checkinstall
```


Found two errors which can be fixed with a little symblink and cp - remind it is still beta-ware.

```
cd ~/Desktop/audacious-1.4.0-beta1/src/libaudclient
sudo cp libaudclient.so /usr/lib/libaudclient.so.1.0.0
cd /usr/local/lib/audacious/Input
sudo ln -s /usr/local/lib/libaudid3tag.so.1.0.0 /usr/lib/libaudid3tag.so.1.0.0

```

I should properly prefixed audacious and its plugin. Oh well...

Nice to have it here as well. Just going to follow it now.
Thank you again!

---

### Post by Kosimo on 2007-10-15
I did follow the audacious procedure step by step. It took me 30 minutes.

Then... I invoke this command:  audacious  

and I get this error:

> cosimo@cosimo-laptop:~$ audacious
(mowgli_object_class.c:49) [mowgli_object_class_init]: exception mowgli.object_class.duplicate_object_class_exception thrown

[B]

Guys, I give up....  [/B]

There's no way I spent the whole afternoon and part of the night trying to install two programs unsuccessfully.... 

I will try to find something different, or just accept that I can't have those programs because I don't have the skills required.

It's been almost 7 months I'm using Ubuntu, and I convert 4 people to Ubuntu as well.. But I'm seriously considering to move to Mac Os X.  
Just for "time matters"   I will spend maybe 10 seconds to install the latest software.

Really sorry for the flame, but I had to say it...

Thank you again to everyone. I really appreciate your answers.

From Barcelona.

---

### Post by Perfect Storm on 2007-10-15
Why not keep safe playing and stay with synaptic instead and go for stability instead cutting edge?  :)

(by the way I have reported the errors I found to the audacious devs)

---

### Post by Rui Pais on 2007-10-16
> **Artificial Intelligence said:**
> Please keep it english ;)
Sorry, *mea culpa*. 
I bring the subject, we only discuss linguistics on "weird" languages, keeping all topic related in English. Sorry we go OT :oops:


> **Kosimo said:**
> Didn't know about how to get the folder easily from the terminal.
I'm running on 32 bits, and I realize that I'm my ./configure I'm missing some things, like
checking vfork.h usability... no
checking vfork.h presence... no
checking for vfork.h... no


yes, thats normal, just routine checks for optional stuff. Not fundamental things for compilation. I can't understand why it fails to compile on you.

> **Kosimo said:**
> Yes, I Know where it is. 
But is disabled. Is gray and is not possible to hit.

Well, I have the same issue (not important for me). I can't get EQ.
I have to 1st enable it, like sethvath mentioned, in BMP > Preferences > Playback > Equalizer. But even after enlabled it stills grayed under playback equalizer.
I think we miss some other thing from repos (some decoder or gstreamer related). Don't know enough of that...

> **Kosimo said:**
> ...
It's been almost 7 months I'm using Ubuntu, and I convert 4 people to Ubuntu as well.. But I'm seriously considering to move to Mac Os X.  
Just for "time matters"   I will spend maybe 10 seconds to install the latest software.

Really sorry for the flame, but I had to say it...

Not really a flame rant :)
If you can afford it and if you have software for that OS that satisfy your needs, why not?
Or install both, Linux will always be free. If you want to keep trying bmpx maybe ask about your compilations errors and absence of equalizer under a precompiled deb on bmpx forums. Here the link:
[http://forum.beep-media-player.org/](http://forum.beep-media-player.org/)

The [bugtracker]("http://bugs.beep-media-player.org/my_view_page.php") may have some clues too.

best of luck.

---

### Post by sethvath on 2007-10-16
> **Kosimo said:**
> Yes, I Know where it is. 
But is disabled. Is gray and is not possible to hit.
It works for me and I'm assuming you used the deb I provided? Would someone else try it and let me know whether they encounter the same problem.

---

### Post by sethvath on 2007-10-16
> **Kosimo said:**
> I did follow the audacious procedure step by step. It took me 30 minutes.

Then... I invoke this command:  audacious  

and I get this error:


[B]

Guys, I give up....  [/B]

There's no way I spent the whole afternoon and part of the night trying to install two programs unsuccessfully.... 

I will try to find something different, or just accept that I can't have those programs because I don't have the skills required.

It's been almost 7 months I'm using Ubuntu, and I convert 4 people to Ubuntu as well.. But I'm seriously considering to move to Mac Os X.  
Just for "time matters"   I will spend maybe 10 seconds to install the latest software.

Really sorry for the flame, but I had to say it...

Thank you again to everyone. I really appreciate your answers.

From Barcelona.
If you prefer bleeding edge and like compiling everything for your achitecture, have a look at gentoo. I am a long time Gentoo user and the compilation gets to me at times but I learn to deal with it. Ubuntu is much forgiving in comparison. 

Mac is not really as simple as you think it is. You dont get the latest and greatest of everything and wait till you compile your own .dmg. :D

I'm a photographer by trade and I keep a mac around primarily for photoshop.

---

### Post by Kosimo on 2007-11-06
Finally Getdeb is here to help us

An amazing .deb for gutsy of the latest version 0.40.13 Working perfectly.


[http://www.getdeb.net/app.php?name=Beep+Media+Player](http://www.getdeb.net/app.php?name=Beep+Media+Player)

---

### Post by DarkDead on 2007-11-06
Hi.
It really works. Thanks for the information Kosimo.

I need some help me with the following.
I installed BMPx because I was looking for a music player in which I could navigate through my media using a directory structure view. BMPx is supposed to do that, at least according to it's screenshots: [http://bmpx.beep-media-player.org/images/Bmpx-0.40-screenshot-4.jpg]("http://bmpx.beep-media-player.org/images/Bmpx-0.40-screenshot-4.jpg").
However in my system it looks like this: [http://img129.imageshack.us/img129/7938/bmpmw7.png]("http://img129.imageshack.us/img129/7938/bmpmw7.png")
Does anyone know how to enable the filesystem view?

---

