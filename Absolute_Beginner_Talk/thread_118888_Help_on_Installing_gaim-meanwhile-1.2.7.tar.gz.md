---
title: "Help on Installing gaim-meanwhile-1.2.7.tar.gz"
date: 2006-01-17
forum: Absolute Beginner Talk
---

### Post by nusigmaforce on 2006-01-17
I'm trying to install gaim-meanwhile-1.2.7 to add sametime plug-in to my Gaim. I'm stuck, and can't compile it. Pleaseeeeeeeeeee, can somebody/anybody help me or send me the command lines that I need to use to get this done? Thanksssss!

---

### Post by mustang on 2006-01-17
Please paste specifically what errors you are receiving in the terminal during the compiling process so we can help you troubleshoot your problem.

---

### Post by nusigmaforce on 2006-01-18
Thanks,mustang. 

First, I want to mention that I was trying to follow the directions found in the install file from the gaim-meanwhile-1.2.7.tar.gz archive. Also, I don't think I ever got to compile anything. I couldn't follow the 'make' commnad from the instructions. (See file attached, step 2)

Just in case here are the generic instructions:
-----------------------------------
The simplest way to compile this package is:

  1. `cd' to the directory containing the package's source code and type
     `./configure' to configure the package for your system.  If you're
     using `csh' on an old version of System V, you might need to type
     `sh ./configure' instead to prevent `csh' from trying to execute
     `configure' itself.

     Running `configure' takes awhile.  While running, it prints some
     messages telling which features it is checking for.

  2. Type `make' to compile the package.

  3. Optionally, type `make check' to run any self-tests that come with
     the package.

  4. Type `make install' to install the programs and any data files and
     documentation.

  5. You can remove the program binaries and object files from the
     source code directory by typing `make clean'.  To also remove the
     files that `configure' created (so you can compile the package for
     a different kind of computer), type `make distclean'.  There is
     also a `make maintainer-clean' target, but that is intended mainly
     for the package's developers.  If you use it, you may have to get
     all sorts of other programs in order to regenerate files that came
     with the distribution.

------------------------------


Second, here is the terminal code:
nusigmaforce@ubuntu:~$ cd /home/nusigmaforce/Desktop/gaim-meanwhile-1.2.7
nusigmaforce@ubuntu:~/Desktop/gaim-meanwhile-1.2.7$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... none
checking dependency style of gcc... none
checking for a BSD-compatible install... /usr/bin/install -c
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
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
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
appending configuration tag "F77" to libtool
checking for ANSI C header files... (cached) yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GAIM... configure: error: Package requirements (gaim >= 1.2.0 gaim < 2.0.0) were not met:

Package gaim was not found in the pkg-config search path.
Perhaps you should add the directory containing `gaim.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gaim' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GAIM_CFLAGS
and GAIM_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

nusigmaforce@ubuntu:~/Desktop/gaim-meanwhile-1.2.7$ make
bash: make: command not found
nusigmaforce@ubuntu:~/Desktop/gaim-meanwhile-1.2.7$

---

### Post by Sef on 2006-01-18
To compile u need to install build-essential, otherwise make will not work.

Sudo apt-get install build-essential

---

### Post by nusigmaforce on 2006-01-18
Hi, Sef:
I installed (sudo apt-get install build-essential) with no problems, but got an error with the 'make' command. Any thoughts? Please check it out:
nusigmaforce@ubuntu:~$ sudo apt-get install build-essential
.
.
.
nusigmaforce@ubuntu:~$ cd /home/nusigmaforce/Desktop/gaim-meanwhile-1.2.7
nusigmaforce@ubuntu:~/Desktop/gaim-meanwhile-1.2.7$ ./configure
.
.
.
nusigmaforce@ubuntu:~/Desktop/gaim-meanwhile-1.2.7$ make
make: *** No targets specified and no makefile found.  Stop.
nusigmaforce@ubuntu:~/Desktop/gaim-meanwhile-1.2.7$ make install
make: *** No rule to make target `install'.  Stop.
nusigmaforce@ubuntu:~/Desktop/gaim-meanwhile-1.2.7$ make check
make: *** No rule to make target `check'.  Stop.

---

### Post by firehead on 2006-01-18
what output did you get this time from ./configure?
because there was another error in the output you posted:
```
checking for GAIM... configure: error: Package requirements (gaim >= 1.2.0 gaim < 2.0.0) were not met:

```
are you sure that gaim is installed on your system?
otherwise try ```
sudo apt-get install gaim
```
and then compile gaim-meanwhile (same as before... ./configure && make && sudo make install)

---

### Post by nusigmaforce on 2006-01-21
Yes, Gaim is already installed. Any ideas? Thanks

nusigmaforce@ubuntu:~$ sudo apt-get install gaim
Password:
Reading package lists... Done
Building dependency tree... Done
gaim is already the newest version.

---

