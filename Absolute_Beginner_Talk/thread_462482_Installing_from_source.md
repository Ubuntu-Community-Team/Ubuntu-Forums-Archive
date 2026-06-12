---
title: "Installing from source"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by i-am-me on 2007-06-02
I don't know why, but I keep having problems installing programs from source. I have build-essential installed. I run Kubuntu 7.04. This is what happens every time (Note: I already installed Pidgin by other means, but this is in general and I'm already in the un-tarred file):
```
the-great-one@LinuxofNitish:~/pidgin-2.0.1$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for sed... /bin/sed
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
checking for g77... g77
checking whether we are using the GNU Fortran 77 compiler... yes
checking whether g77 accepts -g... yes
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
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for g77 option to produce PIC... -fPIC
checking if g77 PIC flag -fPIC works... yes
checking if g77 static flag -static works... yes
checking if g77 supports -c -o file.o... yes
checking whether the g77 linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking for a BSD-compatible install... /usr/bin/install -c
checking for perl... /usr/bin/perl
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool
the-great-one@LinuxofNitish:~/pidgin-2.0.1$ make
make: *** No targets specified and no makefile found.  Stop.
```

---

### Post by Swab on 2007-06-02
You are missing a dependency.  Perhaps you need libxml-parser-perl. 

sudo apt-get install libxml-parser-perl

---

### Post by i-am-me on 2007-06-02
I installed g77 and libxml-parser-perl and now the end of the configure says:

```
checking for GLIB... no
no
configure: error:

You must have the GLib 2.0 development headers installed to build.
```

What's the command to install that?

---

### Post by Bachstelze on 2007-06-02
```
sudo apt-get install libglib2.0-dev
```

---

### Post by Swab on 2007-06-02
It might be libglib2.0-dev

sudo apt-get install libglib2.0-dev

---

### Post by i-am-me on 2007-06-02
What's the name for GTK+ 2.0 development headers? Is it libgtk2.0-dev?

---

### Post by Bachstelze on 2007-06-02
libgtk2.0-dev

---

### Post by i-am-me on 2007-06-02
I hate compiling:
```
checking for LIBXML... no
no
configure: error:

You must have libxml2 >= 2.6.0 development headers installed to build.
```

I this one libxml2.6-dev or something?

---

### Post by Bachstelze on 2007-06-02
nope, it's libxml2-dev :p

---

### Post by i-am-me on 2007-06-02
Thanks guys. It works now.:D

---

### Post by i-am-me on 2007-06-02
Never realized the make command took so long, it's still not done.

---

### Post by Swab on 2007-06-02
Yeah, it can take a while depending on what you are compiling.

---

### Post by i-am-me on 2007-07-03
Well, this sucks, I now have another problem with compiling after such a long time. at the end of ./configure, it gives me this error:
```
checking for X... configure: error: Can't find X libraries. Please check your installation and add the correct paths!

```

---

### Post by Swab on 2007-07-03
Try installing the xorg-dev package.

---

### Post by i-am-me on 2007-07-03
new one.........

```
checking for Qt... configure: error: Qt (>= Qt 3.0 and < 4.0) (headers and libraries) not found. Please check your installation!

```

---

### Post by Malibu Illusion on 2007-07-03
```
sudo aptitude install libqt4-dev
```

---

### Post by Bachstelze on 2007-07-03
> **Malibu Illusion said:**
> ```
sudo aptitude install libqt4-dev
```

It needs Qt3...

```
sudo apt-get install libqt3-mt-dev
```

---

### Post by Malibu Illusion on 2007-07-03
Oh.  Guess I should have continued reading inside the brackets after "Qt", eh? =)

Sowwy! =^^=

---

