---
title: "Help compiling please"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by bwhite82 on 2007-01-30
I've been trying to compile a program, haven't had any problems in the past doing so.
Per the included program instructions I type:

> ./autogen.sh && make

and the output is:

> soldierboy@ubuntu-laptop:~/UMark$ ./autogen.sh && make
**Warning**: I am going to run `configure' with no arguments.
If you wish to pass any to it, please specify them on the
`./autogen.sh' command line.

processing .
Running aclocal  ...
Running autoheader...
Running automake --gnu  ...
automake: configure.in: installing `./install-sh'; error while making link: File exists

automake: configure.in: installing `./mkinstalldirs'
automake: configure.in: installing `./missing'; error while making link: File exists

automake: configure.in: installing `./config.guess'
automake: configure.in: installing `./config.sub'
Running autoconf ...
Running ./configure --enable-maintainer-mode ...
configure: error: cannot find install-sh or install.sh in "." "./.." "./../.."
soldierboy@ubuntu-laptop:~/UMark$

Any ideas? I'm fairly certain nothing is wrong with the source code, because I went to another forum and looked at a different problem relating to this same install, and someone trying to help him did indeed compile it and provided a screenshot as proof:

[http://www.suseforums.net/index.php?showtopic=18589]("http://www.suseforums.net/index.php?showtopic=18589")

The program I'm trying to install is UMark, avail for download [here.]("http://sourceforge.net/project/downloading.php?groupname=ut2k3botbench&filename=UMark-for-Linux-v200-Beta3.tar.gz&use_mirror=umn") Could someone possibly download and try compiling to confirm? It's only 219kb.

PS: Yes I have UT2004 Demo installed AND booted it up once, (although it's not needed to compile)

---

### Post by lisje on 2007-01-30
> **soldierboy101st said:**
> I've been trying to compile a program, haven't had any problems in the past doing so.
Per the included program instructions I type:



and the output is:



Any ideas? I'm fairly certain nothing is wrong with the source code, because I went to another forum and looked at a different problem relating to this same install, and someone trying to help him did indeed compile it and provided a screenshot as proof:

[http://www.suseforums.net/index.php?showtopic=18589]("http://www.suseforums.net/index.php?showtopic=18589")

The program I'm trying to install is UMark, avail for download [here.]("http://sourceforge.net/project/downloading.php?groupname=ut2k3botbench&filename=UMark-for-Linux-v200-Beta3.tar.gz&use_mirror=umn") Could someone possibly download and try compiling to confirm? It's only 219kb.

PS: Yes I have UT2004 Demo installed AND booted it up once, (although it's not needed to compile)
I found on a forum you might want to try installing automake1.8

If you know french: [http://forum.ubuntu-fr.org/]("http://forum.ubuntu-fr.org/viewtopic.php?pid=535644")

---

### Post by bwhite82 on 2007-01-30
Merci beaucoup! It got me a little closer at least, now it seems to be complaining about my GTK+ version:

> soldierboy@ubuntu-laptop:~/UMark$ ./autogen.sh && make
**Warning**: I am going to run `configure' with no arguments.
If you wish to pass any to it, please specify them on the
`./autogen.sh' command line.

processing .
Running aclocal  ...
/usr/share/aclocal/libmcrypt.m4:17: warning: underquoted definition of AM_PATH_LIBMCRYPT
  run info '(automake)Extending aclocal'
  or see [http://sources.redhat.com/automake/automake.html#Extending%20aclocal](http://sources.redhat.com/automake/automake.html#Extending%20aclocal)
Running autoheader...
Running automake --gnu  ...
Running autoconf ...
Running ./configure --enable-maintainer-mode ...
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
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
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for PACKAGE... configure: error: Package requirements (gtk+-2.0 >= 2.0.0) were not met:

No package 'gtk+-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PACKAGE_CFLAGS
and PACKAGE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

---

### Post by konst88 on 2007-01-30
sudo aptitude install libgtk2.0-dev
Alsways search the files started with lib, and ends with -dev.

---

### Post by bwhite82 on 2007-01-30
Yep, that did it, thanks both!

---

