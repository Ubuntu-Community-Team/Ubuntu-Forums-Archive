---
title: "Trying to compile conky 1.4.5."
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by crimesaucer on 2006-12-23
Hello, I am in the middle of my first compiling. I think I have done something wrong becasue of this last message at the end of the sudo checkinstall, here is my terminal process: 

blah@blah-blah:~$ tar xvzf conky-1.4.5.tar.gz
conky-1.4.5/
conky-1.4.5/extras/
conky-1.4.5/extras/nano/
conky-1.4.5/extras/nano/README
conky-1.4.5/extras/nano/conky.nanorc
conky-1.4.5/extras/vim/
conky-1.4.5/extras/vim/ftdetect/
conky-1.4.5/extras/vim/ftdetect/conkyrc.vim
conky-1.4.5/extras/vim/syntax/
conky-1.4.5/extras/vim/syntax/conkyrc.vim
conky-1.4.5/extras/vim/README
conky-1.4.5/src/
conky-1.4.5/src/Makefile.am
conky-1.4.5/src/Makefile.in
conky-1.4.5/src/build.h.in
conky-1.4.5/src/config.h.in
conky-1.4.5/src/audacious.c
conky-1.4.5/src/audacious.h
conky-1.4.5/src/bmpx.c
conky-1.4.5/src/common.c
conky-1.4.5/src/conky.c
conky-1.4.5/src/conky.h
conky-1.4.5/src/freebsd.c
conky-1.4.5/src/fs.c
conky-1.4.5/src/hddtemp.c
conky-1.4.5/src/linux.c
conky-1.4.5/src/top.c
conky-1.4.5/src/mail.c
conky-1.4.5/src/mixer.c
conky-1.4.5/src/mpd.c
conky-1.4.5/src/libmpdclient.c
conky-1.4.5/src/libtcp-portmon.h
conky-1.4.5/src/libtcp-portmon.c
conky-1.4.5/src/remotec.c
conky-1.4.5/src/remotec.h
conky-1.4.5/src/remoted.c
conky-1.4.5/src/remoted.h
conky-1.4.5/src/timed_thread.c
conky-1.4.5/src/timed_thread.h
conky-1.4.5/src/x11.c
conky-1.4.5/src/xmms2.c
conky-1.4.5/src/ftp.c
conky-1.4.5/src/ftp.h
conky-1.4.5/src/libmpdclient.h
conky-1.4.5/src/netbsd.c
conky-1.4.5/src/solaris.c
conky-1.4.5/src/top.h
conky-1.4.5/README
conky-1.4.5/configure.ac
conky-1.4.5/aclocal.m4
conky-1.4.5/Makefile.am
conky-1.4.5/Makefile.in
conky-1.4.5/configure
conky-1.4.5/AUTHORS
conky-1.4.5/COPYING
conky-1.4.5/ChangeLog
conky-1.4.5/INSTALL
conky-1.4.5/NEWS
conky-1.4.5/TODO
conky-1.4.5/config.guess
conky-1.4.5/config.sub
conky-1.4.5/depcomp
conky-1.4.5/install-sh
conky-1.4.5/ltmain.sh
conky-1.4.5/missing
conky-1.4.5/autogen.sh
conky-1.4.5/configure.ac.in
conky-1.4.5/doc/
conky-1.4.5/doc/Makefile.am
conky-1.4.5/doc/Makefile.in
conky-1.4.5/doc/conky.1
conky-1.4.5/doc/docs.html
conky-1.4.5/doc/variables.html
conky-1.4.5/doc/config_settings.html
conky-1.4.5/doc/conkyrc.sample
conky-1.4.5/doc/command_options.xml
conky-1.4.5/doc/config_settings.xml
conky-1.4.5/doc/docgen.sh
conky-1.4.5/doc/docs.xml
conky-1.4.5/doc/variables.xml
conky-1.4.5/doc/variables.xsl
conky-1.4.5/doc/config_settings.xsl
blah@blah-blah:~$ rm conky-1.4.5.tar.gz
blah@blah-blah:~$ cd ~/conky-1.4.5
blah@blah-blah:~/conky-1.4.5$ ./configure --prefix=/usr --mandir=/usr/share/man --infodir=/usr/share/info --datadir=/usr/share --sysconfdir=/etc --localstatedir=/var/lib --enable-xft --enable-seti --enable-double-buffer --enable-own-window --enable-proc-uptime --enable-mpd --enable-mldonkey --enable-x11 --enable-portmon --enable-infopipe make
configure: WARNING: you should use --build, --host, --target
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for make-gcc... no
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
checking build system type... Invalid configuration `make': machine `make' not recognized
configure: error: /bin/bash ./config.sub make failed
blah@blah-blah:~/conky-1.4.5$ sudo checkinstall
Password:

checkinstall 1.6.0, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist. 
Should I create a default set of package docs?  [y]: y

Preparing package documentation...OK

Please write a description for the package.
End your description with an empty line or EOF.
>> conky sensors EOF
>> EOF
>> 

*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@blah-blah ]
1 -  Summary: [ conky sensors EOF ]
2 -  Name:    [ conky ]
3 -  Version: [ 1.4.5 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ conky-1.4.5 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
make: *** No rule to make target `install'.  Stop.

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.


...I also am not sure of which command to put in my autostarted applications for my xubuntu desktop.

Thanks for any help.

---

### Post by pay on 2006-12-23
Compile it like this ```
./configure --prefix=/usr --mandir=/usr/share/man --infodir=/usr/share/info --datadir=/usr/share --sysconfdir=/etc --localstatedir=/var/lib --enable-xft --enable-seti --enable-double-buffer --enable-own-window --enable-proc-uptime --enable-mpd --enable-mldonkey --enable-x11 --enable-portmon --enable-infopipe
```and then type make, not on the configure line like before!```
make
```and then you can build the debian package```
sudo checkinstall -D make install
```If it says anything about missing dependencies try ```
sudo apt-get build-dep conky
```

---

### Post by v8YKxgHe on 2006-12-23
you could always do 

```
sudo apt-get install conky
```

if your on Edgy

---

### Post by crimesaucer on 2006-12-23
It started to work, but then I got the error saying I needed glib-2.0 (which I searched in ubuntu's package search and didn't find).

This is the new error:

blah@blah-blah:~/conky-1.4.5$ ./configure --prefix=/usr --mandir=/usr/share/man --infodir=/usr/share/info --datadir=/usr/share --sysconfdir=/etc --localstatedir=/var/lib --enable-xft --enable-seti --enable-double-buffer --enable-own-window --enable-proc-uptime --enable-mpd --enable-mldonkey --enable-x11 --enable-portmon --enable-infopipe
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
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
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking for correct ltmain.sh version... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
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
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.17.2... yes
checking netdb.h usability... yes
checking netdb.h presence... yes
checking for netdb.h... yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking netinet/tcp.h usability... yes
checking netinet/tcp.h presence... yes
checking for netinet/tcp.h... yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking arpa/inet.h usability... yes
checking arpa/inet.h presence... yes
checking for arpa/inet.h... yes
checking for GLIB... configure: error: Package requirements (glib-2.0) were not met:

No package 'glib-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GLIB_CFLAGS
and GLIB_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

blah@blah-blah:~/conky-1.4.5$ make
make: *** No targets specified and no makefile found.  Stop.
blah@blah-blah:~/conky-1.4.5$ 

...so, am I missing an important library?...and if I install the correct library then will the make command work? Thanks for any help.

---

### Post by NeoLithium on 2006-12-23
I just installed conky with the help of [this thread]("http://www.ubuntuforums.org/showthread.php?t=205865"), just a couple of little annoyances, but I just gotta hunt through my script to figure them out...

---

### Post by eXisor on 2006-12-23
I just did compiled conky 1.4.5 today so you're in luck.

You need the packages from the conky 1.4.2 howto and then the list below to compile conky 1.4.5.


```
sudo aptitude install libglib2.0-dev libxft-dev libx11-dev libxdamage-dev
```

That should get you to the 'make' step in the howto.

---

### Post by crimesaucer on 2006-12-23
Thank you very much for walking me through my first compiling.

I think it worked perfectly, but I added what I just wrote in terminal anyway so if I missed something important, someone could help me with a tip.

I do have another question though, at the end of this "how-to" ( [http://doc.gwos.org/index.php/Conky_1.4.2](http://doc.gwos.org/index.php/Conky_1.4.2) ) step #6 says I should add conky to the autostarted apps, I want to add it from /usr/bin/conky ,right?


blah@blah-blah:~$ cd ~/conky-1.4.5
blah@blah-blah:~/conky-1.4.5$ make
make: *** No targets specified and no makefile found.  Stop.
blah@blah-blah:~/conky-1.4.5$ ./configure --prefix=/usr --mandir=/usr/share/man --infodir=/usr/share/info --datadir=/usr/share --sysconfdir=/etc --localstatedir=/var/lib --enable-xft --enable-seti --enable-double-buffer --enable-own-window --enable-proc-uptime --enable-mpd --enable-mldonkey --enable-x11 --enable-portmon --enable-infopipe
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
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
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking for correct ltmain.sh version... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
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
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.17.2... yes
checking netdb.h usability... yes
checking netdb.h presence... yes
checking for netdb.h... yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking netinet/tcp.h usability... yes
checking netinet/tcp.h presence... yes
checking for netinet/tcp.h... yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking arpa/inet.h usability... yes
checking arpa/inet.h presence... yes
checking for arpa/inet.h... yes
checking for GLIB... yes
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... /bin/bash: ./config.rpath: No such file or directory
done
checking for iconv... yes
checking for iconv declaration... 
         extern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);
checking for X11... yes
checking for XEXT... yes
checking for XDAMAGE... yes
checking for XFT... yes
checking signal.h usability... yes
checking signal.h presence... yes
checking for signal.h... yes
checking for unistd.h... (cached) yes
checking sys/utsname.h usability... yes
checking sys/utsname.h presence... yes
checking for sys/utsname.h... yes
checking for sys/stat.h... (cached) yes
checking linux/soundcard.h usability... yes
checking linux/soundcard.h presence... yes
checking for linux/soundcard.h... yes
checking dirent.h usability... yes
checking dirent.h presence... yes
checking for dirent.h... yes
checking mcheck.h usability... yes
checking mcheck.h presence... yes
checking for mcheck.h... yes
checking sys/statfs.h usability... yes
checking sys/statfs.h presence... yes
checking for sys/statfs.h... yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking pthread.h usability... yes
checking pthread.h presence... yes
checking for pthread.h... yes
checking assert.h usability... yes
checking assert.h presence... yes
checking for assert.h... yes
checking errno.h usability... yes
checking errno.h presence... yes
checking for errno.h... yes
checking time.h usability... yes
checking time.h presence... yes
checking for time.h... yes
checking for sys/mount.h... yes
checking for calloc... yes
checking for malloc... yes
checking for free... yes
checking for popen... yes
checking for library containing clock_gettime... none required
checking for db2x_xsltproc... no
checking for db2x_manxml... no
checking for xsltproc... xsltproc
checking for sysinfo... yes
checking for getloadavg... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating doc/Makefile
config.status: creating src/Makefile
config.status: creating src/build.h
config.status: creating src/config.h
config.status: executing depfiles commands

conky 1.4.5 configured successfully:

 Installing into:       /usr
 C compiler flags:       -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include         -I/usr/include/freetype2   -Wall -W
 Linker flags:
 Libraries:              -lglib-2.0    -lX11   -lXext   -lXdamage -lXfixes   -lXft -lfontconfig  

 * x11:
  x11 support:          yes
  xdamage support:      yes
  xdbe support:         yes
  xft support:          yes

 * music detection:
  audacious:            no
  bmpx:                 no
  mpd:                  yes
  xmms2:                no

 * general:
  hddtemp:              yes
  portmon:              yes

blah@blah-blah:~/conky-1.4.5$ make
Making all in src
make[1]: Entering directory `/home/blah/conky-1.4.5/src'
make  all-am
make[2]: Entering directory `/home/blah/conky-1.4.5/src'
if gcc -DHAVE_CONFIG_H -I. -I. -I.     -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include         -I/usr/include/freetype2   -Wall -W -MT common.o -MD -MP -MF ".deps/common.Tpo" -c -o common.o common.c; \
        then mv -f ".deps/common.Tpo" ".deps/common.Po"; else rm -f ".deps/common.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.     -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include         -I/usr/include/freetype2   -Wall -W -MT conky.o -MD -MP -MF ".deps/conky.Tpo" -c -o conky.o conky.c; \
        then mv -f ".deps/conky.Tpo" ".deps/conky.Po"; else rm -f ".deps/conky.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.     -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include         -I/usr/include/freetype2   -Wall -W -MT fs.o -MD -MP -MF ".deps/fs.Tpo" -c -o fs.o fs.c; \
        then mv -f ".deps/fs.Tpo" ".deps/fs.Po"; else rm -f ".deps/fs.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.     -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include         -I/usr/include/freetype2   -Wall -W -MT hddtemp.o -MD -MP -MF ".deps/hddtemp.Tpo" -c -o hddtemp.o hddtemp.c; \
        then mv -f ".deps/hddtemp.Tpo" ".deps/hddtemp.Po"; else rm -f ".deps/hddtemp.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.     -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include         -I/usr/include/freetype2   -Wall -W -MT linux.o -MD -MP -MF ".deps/linux.Tpo" -c -o linux.o linux.c; \
        then mv -f ".deps/linux.Tpo" ".deps/linux.Po"; else rm -f ".deps/linux.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.     -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include         -I/usr/include/freetype2   -Wall -W -MT top.o -MD -MP -MF ".deps/top.Tpo" -c -o top.o top.c; \
        then mv -f ".deps/top.Tpo" ".deps/top.Po"; else rm -f ".deps/top.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.     -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include         -I/usr/include/freetype2   -Wall -W -MT mail.o -MD -MP -MF ".deps/mail.Tpo" -c -o mail.o mail.c; \
        then mv -f ".deps/mail.Tpo" ".deps/mail.Po"; else rm -f ".deps/mail.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.     -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include         -I/usr/include/freetype2   -Wall -W -MT mixer.o -MD -MP -MF ".deps/mixer.Tpo" -c -o mixer.o mixer.c; \
        then mv -f ".deps/mixer.Tpo" ".deps/mixer.Po"; else rm -f ".deps/mixer.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.     -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include         -I/usr/include/freetype2   -Wall -W -MT mpd.o -MD -MP -MF ".deps/mpd.Tpo" -c -o mpd.o mpd.c; \
        then mv -f ".deps/mpd.Tpo" ".deps/mpd.Po"; else rm -f ".deps/mpd.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.     -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include         -I/usr/include/freetype2   -Wall -W -MT libmpdclient.o -MD -MP -MF ".deps/libmpdclient.Tpo" -c -o libmpdclient.o libmpdclient.c; \
        then mv -f ".deps/libmpdclient.Tpo" ".deps/libmpdclient.Po"; else rm -f ".deps/libmpdclient.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.     -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include         -I/usr/include/freetype2   -Wall -W -MT libtcp-portmon.o -MD -MP -MF ".deps/libtcp-portmon.Tpo" -c -o libtcp-portmon.o libtcp-portmon.c; \
        then mv -f ".deps/libtcp-portmon.Tpo" ".deps/libtcp-portmon.Po"; else rm -f ".deps/libtcp-portmon.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.     -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include         -I/usr/include/freetype2   -Wall -W -MT remotec.o -MD -MP -MF ".deps/remotec.Tpo" -c -o remotec.o remotec.c; \
        then mv -f ".deps/remotec.Tpo" ".deps/remotec.Po"; else rm -f ".deps/remotec.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.     -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include         -I/usr/include/freetype2   -Wall -W -MT remoted.o -MD -MP -MF ".deps/remoted.Tpo" -c -o remoted.o remoted.c; \
        then mv -f ".deps/remoted.Tpo" ".deps/remoted.Po"; else rm -f ".deps/remoted.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.     -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include         -I/usr/include/freetype2   -Wall -W -MT timed_thread.o -MD -MP -MF ".deps/timed_thread.Tpo" -c -o timed_thread.o timed_thread.c; \
        then mv -f ".deps/timed_thread.Tpo" ".deps/timed_thread.Po"; else rm -f ".deps/timed_thread.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.     -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include         -I/usr/include/freetype2   -Wall -W -MT x11.o -MD -MP -MF ".deps/x11.Tpo" -c -o x11.o x11.c; \
        then mv -f ".deps/x11.Tpo" ".deps/x11.Po"; else rm -f ".deps/x11.Tpo"; exit 1; fi
/bin/bash ../libtool --tag=CC --mode=link gcc  -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include         -I/usr/include/freetype2   -Wall -W -lpthread -lm  -o conky    common.o conky.o  fs.o hddtemp.o linux.o top.o mail.o mixer.o mpd.o libmpdclient.o libtcp-portmon.o remotec.o remoted.o timed_thread.o x11.o   -lglib-2.0    -lX11   -lXext   -lXdamage -lXfixes   -lXft -lfontconfig  
mkdir .libs
gcc -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -Wall -W -o conky common.o conky.o fs.o hddtemp.o linux.o top.o mail.o mixer.o mpd.o libmpdclient.o libtcp-portmon.o remotec.o remoted.o timed_thread.o x11.o  -lpthread -lm /usr/lib/libglib-2.0.so -lrt -lX11 -lXext -lXdamage -lXfixes -lXft -lfontconfig
make[2]: Leaving directory `/home/blah/conky-1.4.5/src'
make[1]: Leaving directory `/home/blah/conky-1.4.5/src'
Making all in doc
make[1]: Entering directory `/home/blah/conky-1.4.5/doc'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/blah/conky-1.4.5/doc'
make[1]: Entering directory `/home/blah/conky-1.4.5'
make[1]: Nothing to be done for `all-am'.
make[1]: Leaving directory `/home/blah/conky-1.4.5'
blah@blah-blah:~/conky-1.4.5$ sudo checkinstall -D make install

checkinstall 1.6.0, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.



*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@blah-blah ]
1 -  Summary: [ conky sensors EOF ]
2 -  Name:    [ conky ]
3 -  Version: [ 1.4.5 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ conky-1.4.5 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
Making install in src
make[1]: Entering directory `/home/blah/conky-1.4.5/src'
make[2]: Entering directory `/home/blah/conky-1.4.5/src'
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /bin/bash ../libtool --mode=install /usr/bin/install -c 'conky' '/usr/bin/conky'
/usr/bin/install -c conky /usr/bin/conky
/usr/bin/install: setting permissions for `/usr/bin/conky': No such file or directory
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/blah/conky-1.4.5/src'
make[1]: Leaving directory `/home/blah/conky-1.4.5/src'
Making install in doc
make[1]: Entering directory `/home/blah/conky-1.4.5/doc'
make[2]: Entering directory `/home/blah/conky-1.4.5/doc'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './conky.1' '/usr/share/man/man1/conky.1'
/usr/bin/install: setting permissions for `/usr/share/man/man1/conky.1': No such file or directory
make[2]: Leaving directory `/home/blah/conky-1.4.5/doc'
make[1]: Leaving directory `/home/blah/conky-1.4.5/doc'
make[1]: Entering directory `/home/blah/conky-1.4.5'
make[2]: Entering directory `/home/blah/conky-1.4.5'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/blah/conky-1.4.5'
make[1]: Leaving directory `/home/blah/conky-1.4.5'

======================== Installation successful ==========================

Copying documentation directory...
./
./AUTHORS
./COPYING
./ChangeLog
./INSTALL
./NEWS
./README
./TODO
./doc/
./doc/Makefile.am
./doc/Makefile.in
./doc/conky.1
./doc/docs.html
./doc/variables.html
./doc/config_settings.html
./doc/conkyrc.sample
./doc/command_options.xml
./doc/config_settings.xml
./doc/docgen.sh
./doc/docs.xml
./doc/variables.xml
./doc/variables.xsl
./doc/config_settings.xsl

Copying files to the temporary directory...OK

Striping ELF binaries and libraries...OK

Compressing man pages...OK

Building file list...OK

Building Debian package...OK

Installing Debian package...OK

Erasing temporary files...OK

Deleting temp dir...OK


**********************************************************************

 Done. The new package has been installed and saved to

 /home/blah/conky-1.4.5/conky_1.4.5-1_i386.deb

 You can remove it from your system anytime using: 

      dpkg -r conky

**********************************************************************
 
... if everything looks good, then thank you, and if not, then please let me know if I missed a step or anything for a proper compiling.

---

### Post by pay on 2006-12-23
Congratulations you have succesfully compilled conky:KS 
/usr/bin/conky is where your executables go. Like the scripts to run the program (unless if you don't configure it with --prefix-/usr then it would be /usr/local/bin). The make install step (or in your case checkinstall) should have installed the executables for you. To make it start type in the terminal```
conky
```to test if everything is working fine and if you are okay with that then add it to System --> Sessions --> Startup Programs. You might want to read ```
man conky
```for information on what corner of the screen you want it.

---

### Post by crimesaucer on 2006-12-23
Thanks for the help earlier, I did get everything working and am reading up about customization. 

I do have one major error though. I have this weird problem where the apps that I have running behind whatever app I have open, and the apps that are minimized to the task bar, both keep popping up infront of whatever window I have open.

I can even switch to a different workspace, and for no reason, my cube will spin back to the app that I kept opening for no reason.

Any idea of what that might be?

*******edit@@@@@@

I fixed it myself, but to share the tip, here it goes. If you have Beryl as your window manager and you used this guide: [http://doc.gwos.org/index.php/Conky_1.4.2](http://doc.gwos.org/index.php/Conky_1.4.2)
you will run into this same thing. The last line of the .conkyrc "${execi 60 wmctrl -a conky}" won't work with Beryl, so delete it, or even better, check this similar guide that seems to have a better .conkyrc with better graphs and everything. Here is this link I found after installing. It's got a better section for Beryl AiGLX also:

[http://www.ubuntuforums.org/showthread.php?t=205865](http://www.ubuntuforums.org/showthread.php?t=205865)

---

