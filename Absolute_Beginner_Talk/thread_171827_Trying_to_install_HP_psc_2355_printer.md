---
title: "Trying to install HP psc 2355 printer"
date: 2006-05-07
forum: Absolute Beginner Talk
---

### Post by JGMN on 2006-05-07
I went ti the linux printing page and downloaded a driver in .tar format. 

the files is hplip-0.9.10. I followed the instructions in the read me file, but it still can't make the file. 

this is what I get.  after the ./configure step and then make command doesn't work

juan@FRED:~$ cd /home/juan/Desktop/hplip-0.9.10
juan@FRED:~/Desktop/hplip-0.9.10$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
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
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... f77
checking whether we are using the GNU Fortran 77 compiler... yes
checking whether f77 accepts -g... yes
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
checking for f77 option to produce PIC... -fPIC
checking if f77 PIC flag -fPIC works... no
checking if f77 supports -c -o file.o... no
checking whether the f77 linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... /usr/bin/f77: Illegal option: -print-search-dirs
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking whether we are using the GNU C++ compiler... (cached) yes
checking whether g++ accepts -g... (cached) yes
checking dependency style of g++... (cached) gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking for a Python interpreter with version >= 2.2... python
checking for python... /usr/bin/python
checking for python version... 2.4
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.4/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.4/site-packages
checking for chkconfig... no
checking for install_initd... no
checking for pthread_create in -lpthread... yes
checking for CRYPTO_free in -lcrypto... no
checking for snmp_timeout in -lnetsnmp... no
checking for usb_init in -lusb... no
configure: error: cannot find libusb support
juan@FRED:~/Desktop/hplip-0.9.10$ make
make: *** No targets specified and no makefile found.  Stop.
juan@FRED:~/Desktop/hplip-0.9.10$

---

### Post by shutupimpoor on 2006-05-07
try going to system - administration - printing and see if you can auto install it. that solved my prolem earlier today with my epson

---

### Post by JGMN on 2006-05-07
I went to detect lan printers and then selected the same one as before but this time it printed. 


Thanks for the help 

:D

---

