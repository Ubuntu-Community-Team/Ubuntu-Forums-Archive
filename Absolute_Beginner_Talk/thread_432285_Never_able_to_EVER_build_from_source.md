---
title: "Never able to EVER build from source"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by mevets on 2007-05-03
I usually shy away from building things from source. The few times I do, its when the developer has givin very detailed instructions on how to do it. Everytime I have ever tried to build something, it has always failed. The configure has failures at the end.

I am now trying to build AWN from svn. [http://awn.wetpaint.com/page/SVN+Version+Installation](http://awn.wetpaint.com/page/SVN+Version+Installation) . the ./autogen.sh Step has several errors at the end and the make cannot happen.
```

~/avant-window-navigator$ ./autogen.sh
/usr/bin/gnome-autogen.sh

checking for autoconf >= 2.53...

  testing autoconf2.50... 
not found.
  testing autoconf... 
found 2.61

checking for automake >= 1.9...

  testing automake-1.10... 
not found.
  testing automake-1.9... 
found 1.9.6

checking for libtool >= 1.5...

  testing libtoolize... 
found 1.5.22

checking for glib-gettext >= 2.2.0...

  testing glib-gettextize... 
found 2.12.11

checking for intltool >= 0.30...

  testing intltoolize... 
found 0.35.5

checking for pkg-config >= 0.14.0...

  testing pkg-config... 
found 0.21

Checking for required M4 macros...


Checking for forbidden M4 macros...

**Warning**: I am going to run `configure' with no arguments.
If you wish to pass any to it, please specify them on the
`./autogen.sh' command line.


Processing ./configure.in


Running libtoolize...

You should add the contents of `/usr/share/aclocal/libtool.m4' to `aclocal.m4'.

Running glib-gettextize... Ignore non-fatal messages.

Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
ftp://ftp.gnu.org/pub/gnu/config/.


Running intltoolize...


Running aclocal-1.9...


Running autoconf...


Running autoheader...


Running automake-1.9...

configure.in: installing `./install-sh'
configure.in: installing `./missing'
src/Makefile.am: installing `./depcomp'

Running ./configure --enable-maintainer-mode ...

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
checking whether to enable maintainer-specific portions of Makefiles... yes
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
checking the maximum length of command line arguments... 32768
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
checking for intltool >= 0.34... 0.35.5 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... /usr/bin/msgfmt
checking for msgmerge... /usr/bin/msgmerge
checking for xgettext... /usr/bin/xgettext
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
checking for catalogs to be installed...  cs da de_DE el_GR en_GB fr_FR it_IT pt_BR ru
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.7... yes
checking for GLIB - version >= 2.8.0... yes (version 2.12.11)
checking for AWN... configure: error: Package requirements ( glib-2.0 gobject-2.0 gtk+-2.0 gdk-2.0 libwnck-1.0 gnome-desktop-2.0 libgnome-2.0 gnome-vfs-2.0 gconf-2.0 x11 xproto dbus-glib-1) were not met:

No package 'gnome-desktop-2.0' found
No package 'libgnome-2.0' found
No package 'gnome-vfs-2.0' found
No package 'dbus-glib-1' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables AWN_CFLAGS
and AWN_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

steve@steve-laptop:~/avant-window-navigator$ make
make: *** No targets specified and no makefile found.  Stop.

```**check the end*

Can anyone tell me what has gone wrong?

---

### Post by pebo on 2007-05-03
Rather than go through dependancy hell you might find it easier installing from the repos, I managed to install using [this]("http://ubuntuforums.org/showthread.php?t=385981&highlight=awn+dock") guide, it was fairly painless.
Good luck

---

### Post by mevets on 2007-05-03
yeah i eventually settled on adding their repo to my sources.list, but I was trying to figure out why I seem to never be able to build anything. Is compiler handicapped?

---

### Post by Tenicus on 2007-05-03
You need these dependencies:
No package 'gnome-desktop-2.0' found
No package 'libgnome-2.0' found
No package 'gnome-vfs-2.0' found
No package 'dbus-glib-1' found

---

### Post by mevets on 2007-05-03
when i tried to apt-get any of those package they did not exist. I tried enabling addional sources in the sources manager but its still a no go.

---

### Post by Tenicus on 2007-05-04
apt-get install libgnome-2.0 
some are in the repositories, i just checked

---

### Post by 3rdalbum on 2007-05-04
libgnome-desktop-dev
libgnome2-0-dev
libgnomevfs2-dev
libdbus-glib-1-dev

Those are the packages on Dapper, but they are probably the same on Edgy and Feisty. The trick is: On Ubuntu, the dependencies usually have the word "lib" at the beginning, and you must install the package with "-dev" at the end of the name. That always installs the non -dev package too.

So when you see a message that some libaries or packages are missing, you've just got to go into Synaptic and have a look for what's there. A little bit of detective work.

---

### Post by lazyart on 2007-05-04
I've compiled from source before and finding the dev packages you need is the challenge.  You'll find yourself searching for a few characters in the name the compiler spits out to you to find the packages you need.

Even still, you may find out that you can't compile it no matter what because of the dependency problems (sounds like a topic for an AA meeting, doesn't it)?

For example, I tried compiling Quackle, a Scrabble simulator, on Dapper and Edgy.  I just couldn't find a way to do it.  Upgrading the packages you need scares me into thinking it will break everything.  Every couple weeks I check here to see if anyone has tried and succeeded, but no luck.

---

### Post by sad_iq on 2007-05-04
OK...Here's how easy it is to find those missing libraries...read this: [http://www.howtoforge.com/apt_file_debian_ubuntu](http://www.howtoforge.com/apt_file_debian_ubuntu)
 If this won't do I'll revert back to Windows :lolflag: !!!

---

### Post by pebo on 2007-05-04
Excellent tip sad_iq ;)

---

### Post by jargoman on 2007-05-05
don't go back to windblows. Once you get a hang of it compiling is easy. I remember staying up till 6 in the morning trying to compile a program and wondering if it's even worth it. It is worth the knowledge you gain. the best thing to remember is that the # 1 reason compiles fail is because of missing libraries.

---

### Post by jargoman on 2007-05-05
as an example I got this error 

No package 'dbus-glib-1' found

I opened up synaptic package manager did a search for dbus-glib-1
found and installed libdbus-glib-1-dev 

worked like a charm

---

### Post by Shay Stephens on 2007-05-05
I keep trying on and off, and have only really succeeded once to compile something.  I have the worst luck compiling.

---

