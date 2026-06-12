---
title: "How to install this theme?"
date: 2005-05-02
forum: Art &amp; Design
---

### Post by joplass on 2005-05-02
I have no idea how to install this theme: [http://art.gnome.org/themes/gtk2/777/](http://art.gnome.org/themes/gtk2/777/)
I unpacked it but I can't apply it.
Thank you for your help,

---

### Post by XDevHald on 2005-05-02
[QUOTE=joplass]I have no idea how to install this theme: [http://art.gnome.org/themes/gtk2/777/]("http://art.gnome.org/themes/gtk2/777/")
I unpacked it but I can't apply it.
Thank you for your help,[/QUOTE]
 Not a problem, simply save the file to your desktop, then open your Theme Manager, located in your **System > Preferences > Theme Manager **

Then drag the tar.gz file to the theme manager and it will install it for you, then just click ok once it says that is has successfuly installed the theme, and choose the theme name, and you will be set up. :)

---

### Post by bvc on 2005-05-03
did you compile the engine first?
[http://art.gnome.org/themes/gtk_engines/760/](http://art.gnome.org/themes/gtk_engines/760/)

download then uncompress that to somewhere in your home dir and from a terminal cd into it and do
./configure --prefix=/usr
make
sudo make install

look for and post any errors here if you can't figure them out.
[http://www.kernow-webhosting.com/~bvc/theme/screenshots/eXperience.jpg](http://www.kernow-webhosting.com/~bvc/theme/screenshots/eXperience.jpg)

---

### Post by joplass on 2005-05-03
[QUOTE=bvc]did you compile the engine first?
[http://art.gnome.org/themes/gtk_engines/760/](http://art.gnome.org/themes/gtk_engines/760/)

download then uncompress that to somewhere in your home dir and from a terminal cd into it and do
./configure --prefix=/usr
make
sudo make install

look for and post any errors here if you can't figure them out.
[http://www.kernow-webhosting.com/~bvc/theme/screenshots/eXperience.jpg](http://www.kernow-webhosting.com/~bvc/theme/screenshots/eXperience.jpg)[/QUOTE]

This is more than what I was expecting.  Where to start now  :roll: 

job@ubuntunotebook:~$ cd experience-engine-0.9.0
job@ubuntunotebook:~/experience-engine-0.9.0$ ./configure --prefix=/usr
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... missing
checking for working autoconf... missing
checking for working automake-1.4... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... (cached) yes
checking for bison... no
checking for byacc... no
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
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
checking how to run the C++ preprocessor... g++ -E
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
checking for pkg-config... /usr/bin/pkg-config
checking for gtk+-2.0 >= 2.1.0... Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found

configure: error: Library requirements (gtk+-2.0 >= 2.1.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
job@ubuntunotebook:~/experience-engine-0.9.0$

---

### Post by Nis on 2005-05-03
Try
```

sudo apt-get build-dep gtk-engines-clearlooks

```
This should install everything you need to compile and build the Clearlooks engine.  Everything installed should also be enough to compile the eXPerience engine as well.

---

### Post by joplass on 2005-05-03
[QUOTE=Nis]Try
```

sudo apt-get build-dep gtk-engines-clearlooks

```
This should install everything you need to compile and build the Clearlooks engine.  Everything installed should also be enough to compile the eXPerience engine as well.[/QUOTE]

No good.  Maybe I am doing something wrong here.
job@ubuntunotebook:~$ sudo apt-get build-dep gtk-engines-clearlooks
Reading package lists... Done
Building dependency tree... Done
E: Unable to find a source package for gtk-engines-clearlooks
job@ubuntunotebook:~$

---

### Post by bvc on 2005-05-04
install libgtk2.0-dev
or maybe this new one I've never seen b4
gtk2-engines-dev

---

