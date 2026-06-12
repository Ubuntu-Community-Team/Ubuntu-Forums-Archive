---
title: "Glib not detected"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by treehouse on 2007-02-05
Running Dapper.

I just installed glib 1.2.8 and am trying to compile xmms. When I ran ./configure it didn't detect glib. This is what I got:

```

 ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for prefix by checking for xmms... no
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
checking for strerror in -lcposix... no
checking whether byte ordering is bigendian... no
checking for inline... inline
checking for an ANSI C-conforming const... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking for a sed that does not truncate output... /bin/sed
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
checking whether to build static libraries... no
checking whether -lc should be explicitly linked in... no
creating libtool
checking pthread.h usability... yes
checking pthread.h presence... yes
checking for pthread.h... yes
checking for glib-config... /usr/local/bin/glib-config
checking for GLIB - version >= 1.2.2... no
*** Could not run GLIB test program, checking why...
*** The test program compiled, but did not run. This usually means
*** that the run-time linker is not finding GLIB or finding the wrong
*** version of GLIB. If it is not finding GLIB, you'll need to set your
*** LD_LIBRARY_PATH environment variable, or edit /etc/ld.so.conf to point
*** to the installed location  Also, make sure you have run ldconfig if that
*** is required on your system
***
*** If you have an old version installed, it is best to remove it, although
*** you may also be able to get things to work by modifying LD_LIBRARY_PATH
***
*** If you have a RedHat 5.0 system, you should remove the GTK package that
*** came with the system with the command
***
***    rpm --erase --nodeps gtk gtk-devel
configure: error: *** GLIB >= 1.2.2 not installed - please install first ***

```

I don't have an /etc/ld.so.conf anywhere. I set LD_LIBRARY_PATH to "/usr/local/lib" which contains:

```

/usr/local/lib$ dir
glib                  libgmodule-1.2.so.0      libgthread-1.2.so.0.0.8
libglib-1.2.so.0      libgmodule-1.2.so.0.0.8  libgthread.a
libglib-1.2.so.0.0.8  libgmodule.a             libgthread.la
libglib.a             libgmodule.la            libgthread.so
libglib.la            libgmodule.so            python2.4
libglib.so            libgthread-1.2.so.0

```

Of the four or five programs so far that I've tried compiling, glib is the only thing that has worked without a hitch.

Thanks in advance for any help.

---

### Post by ComplexNumber on 2007-02-05
this is something important to remember when compiling packages from source as you are doing. if, for example, it can't find glib, it means that it **glib-dev** package isn't installed. 
install th following package and all will be well. 
[B]libglib2.0-dev
[/B]
or 
[B]
libglib1.2-dev[/B]


i'm not too sure what the most up to date version of glib is in dapper, so fire up synaptic and do a search on name only for "libglib".

remember: if you come across any further dependencies, INSTALL THE 'DEV' VERSION OF THE PACKAGE. the reason why is because when you are compiling from source, it looks for a ".pc"  file in /usr/lib/pkgconfig and /usr/local/lib/pkgconfig to determine if a particular file is installed and what version is installed. these pc files are only usually installed with the dev version of the package (except source packages because they contain both the package and the dev version of the package). so, for example, if libglib-dev isn't installed, the configure script that you are running will believe that glib isn't installed even if libglib is.

---

### Post by treehouse on 2007-02-05
Synaptic gives me version 1.2.10-10.1build1. I assume that I need version 1.2.2 at least of the dev package to make it work? I can't find any more recent releases though. I got this when I tried to ./configure again after installing:

```

checking for glib-config... /usr/local/bin/glib-config
checking for GLIB - version >= 1.2.2...
*** 'glib-config --version' returned 1.2.8, but GLIB (1.2.10)
*** was found! If glib-config was correct, then it is best
*** to remove the old version of GLIB. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If glib-config was wrong, set the environment variable GLIB_CONFIG
*** to point to the correct copy of glib-config, and remove the file config.cache
*** before re-running configure
no
configure: error: *** GLIB >= 1.2.2 not installed - please install first ***

```

I got the same message after changing the version of glib.pc as well. When it detects the version, is it from a config file or glib-dev itself?

---

### Post by ComplexNumber on 2007-02-05
> I got the same message after changing the version of glib.pc as well. what do you mean when you say that you changed it? do you mean that you hand-edited the file? if so, don't do that. 

> When it detects the version, is it from a config file or glib-dev itself?it gets the info from the pc file in  /usr/lib/pkgconfig or /usr/local/lib/config



> 
checking for glib-config... /usr/local/bin/glib-configthis bit of the output of the configure script is curious. is glib installed in /usr/local/bin? it shouldn't be if you installed glib via synaptic. it should be in /usr/bin/

---

### Post by treehouse on 2007-02-05
Originally I compiled glib 1.2.8. I deleted it and installed libglib2.0-0 and libglib2.0-dev from synaptic, and I'm getting the original message again...

I'm completely lost as to what the actual file it's looking for or how to get it installed.

---

### Post by ComplexNumber on 2007-02-05
> **treehouse said:**
> Originally I compiled glib 1.2.8. I deleted it and installed libglib2.0-0 and libglib2.0-dev from synaptic, and I'm getting the original message again...

I'm completely lost as to what the actual file it's looking for or how to get it installed.
no wonder. you MUST delete the old before installing the new. it cannot be done the other way around because of the possibility of them having shared locations, etc. 

personally, i would only install GUI applications and theme engines from source. i don't think its a good idea for important libraries such as glib to be installed from source. lots of things depend on it, and that is sure to cause headaches somewhere down the line.

---

### Post by treehouse on 2007-02-06
should I just delete every file with glib in the name and try redoing it from Synaptic then?

---

### Post by ComplexNumber on 2007-02-06
> **treehouse said:**
> should I just delete every file with glib in the name and try redoing it from Synaptic then?
you've gone about things in a really messy way, i'm afraid. i suppose you've thrown away the original source package which you compiled. if you still had it, you could have run "make uninstall" from there. 
i don't think i would recommend that you go round your system deleting all the glib packages because gnome/gtk depends upon it so heavily. you will end up breaking your system. i really don't know why you installed glib from source when you could much more easily installed it via synaptic or using apt-get on the command line. 
when you are compiling a program from source, i _STRONGLY_ recommend that you use a package called paco. you can get it from [here]("http://paco.sourceforge.net/downloads.html") and you need to install the paco  package from source. unfortunately, there isnt a deb package available(only source and rpm). 
it will allow you to keep track of what you have installed from source, the date that you installed it, and exactly what files were installed where. it also allows you to uninstall them in about 2 keyclicks.


for the time being, i suggest that you ONLY delete the pc file the pkgconfig directory.

---

### Post by treehouse on 2007-02-06
Thank you so much for the help. Everything's working exactly the way I want now.

---

