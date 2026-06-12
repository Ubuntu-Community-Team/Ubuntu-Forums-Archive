---
title: "Banshee 0.12.1"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by simonsocial on 2007-04-15
Can anyone help me install this app please?

[http://banshee-project.org/Releases/0.12.1](http://banshee-project.org/Releases/0.12.1)

I have downloaded the tarball, unzipped it, the run the configure script, then when I type in** make** in the terminal I get the following message: make: *** No targets specified and no makefile found. Stop.

---

### Post by Patrick K on 2007-04-15
Banshee 0.11.1 is available in Add/Remove. I don't know what the differences are between the two versions. Could be minor or major.

---

### Post by simonsocial on 2007-04-16
The one inside add and remove is the older version and I wanted to try out the new version to see if it fixed a few problems i've been having.

---

### Post by jvc26 on 2007-04-16
Should be:
Download the tarball, on your desktop, extract here. This is predominantly following the instructions on the banshee website.
Then in terminal:
```

sudo apt-get build-dep banshee

sudo apt-get install libmono-sqlite2.0-cil libmono-cairo2.0-cil libglib2.0-dev libtool subversion autoconf automake1.9 gnome-common libavahi1.0-cil monodoc

cd /home/USER/Desktop/banshee-0.12.1
./configure --prefix=/usr
make
sudo make install

```

To uninstall:
```

cd /path/to/banshee/make/directory
sudo make uninstall
gconftool-2 --recursive-unset /apps/Banshee
gconftool-2 --recursive-unset /apps/banshee
rm ~/.gnome2/banshee/banshee.db
rm -rf ~/.gnome2/banshee/

```

Il

---

### Post by Seisen on 2007-04-16
Did you install build-essential, without it won't compile.

```
sudo aptitude install build-essential
```

---

### Post by 3rdalbum on 2007-04-16
Sorry to confuse you, if this confuses you :-)

But I'd recommend performing:

```
sudo apt-get install checkinstall
```

as well, and then instead of "sudo make install", you should type "sudo checkinstall".

Follow the prompts, and you'll end off with a Deb package that can be removed using Synaptic if you ever wanted to go back to the old version.

---

### Post by jvc26 on 2007-04-16
Good point I'd forgotten about check install. The reason you're getting the makefile errors is likely to be because you arent able to configure it properly because you're lacking the build dependencies of the banshee package (how to get them is in my post above)
Il

---

### Post by simonsocial on 2007-04-16
Have just done what you said but I get an error at the end....

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libmono-sqlite2.0-cil is already the newest version.
libmono-cairo2.0-cil is already the newest version.
libglib2.0-dev is already the newest version.
monodoc is already the newest version.
The following extra packages will be installed:
  autotools-dev intltool libapr0 libsvn0
Suggested packages:
  autoconf2.13 autobook autoconf-archive gnu-standards autoconf-doc
  libtool-doc g77 fortran77-compiler gcj subversion-tools db4.3-util
Recommended packages:
  automaken libltdl3-dev
The following NEW packages will be installed:
  autoconf automake1.9 autotools-dev gnome-common intltool libapr0
  libavahi1.0-cil libsvn0 libtool subversion
0 upgraded, 10 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 2400kB of archives.
After unpacking 9753kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com edgy/main autoconf 2.60-1 [440kB]
Get:2 http://archive.ubuntu.com edgy/main autotools-dev 20060223.1 [60.1kB]
Get:3 http://archive.ubuntu.com edgy/main automake1.9 1.9.6-4 [517kB]
Get:4 http://archive.ubuntu.com edgy/main libtool 1.5.22-4 [328kB]
Get:5 http://archive.ubuntu.com edgy/main intltool 0.35.0-2 [112kB]
Get:6 http://archive.ubuntu.com edgy/main gnome-common 2.12.0-2ubuntu1 [24.0kB]
Get:7 http://archive.ubuntu.com edgy/main libapr0 2.0.55-4ubuntu4 [137kB]
Get:8 http://archive.ubuntu.com edgy/universe libavahi1.0-cil 0.6.11-1 [31.9kB]
Get:9 http://archive.ubuntu.com edgy/main libsvn0 1.3.2-3ubuntu2 [542kB]
Get:10 http://archive.ubuntu.com edgy/main subversion 1.3.2-3ubuntu2 [208kB]
Fetched 2400kB in 6s (355kB/s)                                                 
Selecting previously deselected package autoconf.
(Reading database ... 140478 files and directories currently installed.)
Unpacking autoconf (from .../autoconf_2.60-1_all.deb) ...
Selecting previously deselected package autotools-dev.
Unpacking autotools-dev (from .../autotools-dev_20060223.1_all.deb) ...
Selecting previously deselected package automake1.9.
Unpacking automake1.9 (from .../automake1.9_1.9.6-4_all.deb) ...
Selecting previously deselected package libtool.
Unpacking libtool (from .../libtool_1.5.22-4_i386.deb) ...
Selecting previously deselected package intltool.
Unpacking intltool (from .../intltool_0.35.0-2_all.deb) ...
Selecting previously deselected package gnome-common.
Unpacking gnome-common (from .../gnome-common_2.12.0-2ubuntu1_all.deb) ...
Selecting previously deselected package libapr0.
Unpacking libapr0 (from .../libapr0_2.0.55-4ubuntu4_i386.deb) ...
Selecting previously deselected package libavahi1.0-cil.
Unpacking libavahi1.0-cil (from .../libavahi1.0-cil_0.6.11-1_all.deb) ...
Selecting previously deselected package libsvn0.
Unpacking libsvn0 (from .../libsvn0_1.3.2-3ubuntu2_i386.deb) ...
Selecting previously deselected package subversion.
Unpacking subversion (from .../subversion_1.3.2-3ubuntu2_i386.deb) ...
Setting up graphviz-cairo (2.8-2) ...
/var/lib/dpkg/info/graphviz-cairo.postinst: 11: dot: not found
dpkg: error processing graphviz-cairo (--configure):
 subprocess post-installation script returned error exit status 127
Setting up autoconf (2.60-1) ...

Setting up autotools-dev (20060223.1) ...
Setting up automake1.9 (1.9.6-4) ...

Setting up libtool (1.5.22-4) ...
Setting up intltool (0.35.0-2) ...
Setting up gnome-common (2.12.0-2ubuntu1) ...
Setting up libapr0 (2.0.55-4ubuntu4) ...

Setting up libavahi1.0-cil (0.6.11-1) ...
* Installing 1 assembly from libavahi1.0-cil into Mono

Setting up libsvn0 (1.3.2-3ubuntu2) ...

Setting up subversion (1.3.2-3ubuntu2) ...
Errors were encountered while processing:
 graphviz-cairo
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Any ideas??

---

### Post by simonsocial on 2007-04-16
Right sorted that problem out now I've got a different one... MONO??

```
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
checking whether to enable maintainer-specific portions of Makefiles... no
checking for intltool >= 0.21... 0.35.0 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... /usr/bin/msgfmt
checking for msgmerge... /usr/bin/msgmerge
checking for xgettext... /usr/bin/xgettext
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
checking for a BSD-compatible install... /usr/bin/install -c
checking what warning flags to pass to the C compiler... -Wall -Wmissing-prototypes
checking what language compliance flags to pass to the C compiler... 
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for ANSI C header files... (cached) yes
checking for pkg-config... /usr/bin/pkg-config
checking for GLIB - version >= 2.0.0... yes (version 2.12.4)
checking for GLIB... yes
checking for DBUS... yes
checking for GTK... yes
checking for GNOMEVFS... yes
checking for MUSICBRAINZ... yes
checking for LIBNAUTILUS_BURN... yes
yes
checking for LIBNAUTILUS_BURN... yes
yes
checking for LIBNAUTILUS_BURN... yes
checking for GST... yes
checking for gst-inspect... /usr/bin/gst-inspect-0.10
checking for GStreamer 0.10 decodebin plugin... yes
checking for GStreamer 0.10 playbin plugin... yes
checking for GStreamer 0.10 cdparanoia plugin... yes
checking for GStreamer 0.10 gnomevfssink plugin... yes
checking for GStreamer 0.10 gnomevfssrc plugin... yes
checking for GStreamer 0.10 audioconvert plugin... yes
checking for GStreamer 0.10 gconfaudiosink plugin... yes
checking for gconftool-2... /usr/bin/gconftool-2
Using config source xml:merged:/etc/gconf/gconf.xml.defaults for schema installation
Using $(sysconfdir)/gconf/schemas as install directory for schema files
checking for MONO_MODULE... configure: error: Package requirements (mono >= 1.1.10) were not met:

No package 'mono' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables MONO_MODULE_CFLAGS
and MONO_MODULE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

Once again any ideas??

---

### Post by jvc26 on 2007-04-16
EDIT:: Forget that, now looking at your new problem
Does this fix it?
```

sudo apt-get install mono mono-common

```
perhaps?

Il

---

### Post by simonsocial on 2007-04-16
I get the following...

```
simon@simon-desktop:~/Downloads/Programs/banshee-0.12.1$ sudo apt-get install mono mono-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mono-common is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mono: Depends: mono-common (= 1.1.17.1-1ubuntu7.1) but 1.2.3.1-1ubuntu1~dhx1 is to be installed
        Depends: mono-jit (= 1.1.17.1-1ubuntu7.1) but 1.2.3.1-1ubuntu1~dhx1 is to be installed
E: Broken packages
```

Should I try removing MONO and then re installing? If so how would I do this?

---

