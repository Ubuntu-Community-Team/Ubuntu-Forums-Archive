---
title: "Installing Mysql?"
date: 2005-06-23
forum: Absolute Beginner Talk
---

### Post by danimal87 on 2005-06-23
Hi, I am reI am aly new to linux and I am trying to get mysql working, this is what i tried  (by the way i'm getting this out of a book se bottom for info on that): 
downloaded:  mysql-4.1.12.tar.gz to /root/Desktop
typed: tar -xzf  mysql-4.1.12.tar.gz
typed: cd mysql-4.1.12
typed: ./configure prefix--/usr/local/mysql
which gives this output:

configure: WARNING: you should use --build, --host, --target
configure: WARNING: invalid host type: prefix--/usr/local/mysql
checking build system type... prefix--/usr/local/mysql
checking host system type... prefix--/usr/local/mysql
checking target system type... prefix--/usr/local/mysql
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... (cached) yes
checking for gawk... (cached) mawk
checking for prefix--/usr/local/mysql-gcc... no
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
checking for prefix--/usr/local/mysql-g++... no
checking for prefix--/usr/local/mysql-c++... no
checking for prefix--/usr/local/mysql-gpp... no
checking for prefix--/usr/local/mysql-aCC... no
checking for prefix--/usr/local/mysql-CC... no
checking for prefix--/usr/local/mysql-cxx... no
checking for prefix--/usr/local/mysql-cc++... no
checking for prefix--/usr/local/mysql-cl... no
checking for prefix--/usr/local/mysql-FCC... no
checking for prefix--/usr/local/mysql-KCC... no
checking for prefix--/usr/local/mysql-RCC... no
checking for prefix--/usr/local/mysql-xlC_r... no
checking for prefix--/usr/local/mysql-xlC... no
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C preprocessor... gcc -E
checking "C Compiler version"... "gcc gcc (GCC) 3.3.5 (Debian 1:3.3.5-8ubuntu2)"checking "C++ compiler version"... "g++ g++ (GCC) 3.3.5 (Debian 1:3.3.5-8ubuntu2)"
checking for prefix--/usr/local/mysql-ranlib... no
checking for ranlib... ranlib
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... nm
checking whether ln -s works... yes
checking how to recognise dependent libraries... unknown
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
checking how to run the C++ preprocessor... g++ -E
checking for prefix--/usr/local/mysql-g77... no
checking for prefix--/usr/local/mysql-f77... no
checking for prefix--/usr/local/mysql-xlf... no
checking for prefix--/usr/local/mysql-frt... no
checking for prefix--/usr/local/mysql-pgf77... no
checking for prefix--/usr/local/mysql-fort77... no
checking for prefix--/usr/local/mysql-fl32... no
checking for prefix--/usr/local/mysql-af77... no
checking for prefix--/usr/local/mysql-f90... no
checking for prefix--/usr/local/mysql-xlf90... no
checking for prefix--/usr/local/mysql-pgf90... no
checking for prefix--/usr/local/mysql-epcf90... no
checking for prefix--/usr/local/mysql-f95... no
checking for prefix--/usr/local/mysql-fort... no
checking for prefix--/usr/local/mysql-xlf95... no
checking for prefix--/usr/local/mysql-ifc... no
checking for prefix--/usr/local/mysql-efc... no
checking for prefix--/usr/local/mysql-pgf95... no
checking for prefix--/usr/local/mysql-lf95... no
checking for prefix--/usr/local/mysql-gfortran... no
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
checking command to parse nm output from gcc object... ok
checking for objdir... .libs
checking for prefix--/usr/local/mysql-ar... no
checking for ar... ar
checking for prefix--/usr/local/mysql-ranlib... ranlib
checking for prefix--/usr/local/mysql-strip... no
checking for strip... strip
checking if gcc static flag  works... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... no
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... no
checking whether to build shared libraries... no
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... no
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... no
checking dynamic linker characteristics... no
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
appending configuration tag "F77" to libtool
checking for a BSD-compatible install... /usr/bin/install -c
checking for bison... no
checking for byacc... no
checking for pdftex... no
checking for tex... no
checking "return type of sprintf"... "int"
checking for uname... /bin/uname
checking operating system... Linux
checking "if we should use 'skip-locking' as default for /usr/local/mysql"... "no"
checking for ln... /bin/ln
checking for ln... /bin/ln
checking for mv... /bin/mv
checking for rm... /bin/rm
checking for cp... /bin/cp
checking for sed... /bin/sed
checking for cmp... /usr/bin/cmp
checking for chmod... /bin/chmod
checking for hostname... /bin/hostname
checking for gnutar... no
checking for gtar... no
checking for tar... tar
checking for perl... /usr/bin/perl
checking for doxygen... no
checking for pdflatex... no
checking for makeindex... no
checking for ps... /bin/ps
checking "how to check if pid exists"... "/bin/ps p $$PID | grep mysqld > /dev/null"
checking for kill... /bin/kill
checking "for kill switches"... "/bin/kill -0 $$PID > /dev/null 2> /dev/null"
checking for gcc option to accept ANSI C...
checking if we should use assembler functions... no
checking if we should use RAID... no
checking If we should should enable LOAD DATA LOCAL by default... no
checking for prefix--/usr/local/mysql-getconf... no
checking for getconf... getconf
checking for CFLAGS value to request large file support... -D_FILE_OFFSET_BITS=64
checking for LDFLAGS value to request large file support...
checking for LIBS value to request large file support...
checking for _FILE_OFFSET_BITS... 64
checking for _LARGEFILE_SOURCE... no
checking for _LARGE_FILES... no
checking for size_t... yes
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking for ANSI C header files... (cached) yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking float.h usability... yes
checking float.h presence... yes
checking for float.h... yes
checking floatingpoint.h usability... no
checking floatingpoint.h presence... no
checking for floatingpoint.h... no
checking ieeefp.h usability... no
checking ieeefp.h presence... no
checking for ieeefp.h... no
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking for memory.h... (cached) yes
checking pwd.h usability... yes
checking pwd.h presence... yes
checking for pwd.h... yes
checking select.h usability... no
checking select.h presence... no
checking for select.h... no
checking for stdlib.h... (cached) yes
checking stddef.h usability... yes
checking stddef.h presence... yes
checking for stddef.h... yes
checking for strings.h... (cached) yes
checking for string.h... (cached) yes
checking synch.h usability... no
checking synch.h presence... no
checking for synch.h... no
checking sys/mman.h usability... yes
checking sys/mman.h presence... yes
checking for sys/mman.h... yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking arpa/inet.h usability... yes
checking arpa/inet.h presence... yes
checking for arpa/inet.h... yes
checking sys/timeb.h usability... yes
checking sys/timeb.h presence... yes
checking for sys/timeb.h... yes
checking for sys/types.h... (cached) yes
checking sys/un.h usability... yes
checking sys/un.h presence... yes
checking for sys/un.h... yes
checking sys/vadvise.h usability... no
checking sys/vadvise.h presence... no
checking for sys/vadvise.h... no
checking for sys/wait.h... (cached) yes
checking term.h usability... no
checking term.h presence... no
checking for term.h... no
checking for unistd.h... (cached) yes
checking utime.h usability... yes
checking utime.h presence... yes
checking for utime.h... yes
checking sys/utime.h usability... no
checking sys/utime.h presence... no
checking for sys/utime.h... no
checking termio.h usability... yes
checking termio.h presence... yes
checking for termio.h... yes
checking termios.h usability... yes
checking termios.h presence... yes
checking for termios.h... yes
checking sched.h usability... yes
checking sched.h presence... yes
checking for sched.h... yes
checking crypt.h usability... yes
checking crypt.h presence... yes
checking for crypt.h... yes
checking alloca.h usability... yes
checking alloca.h presence... yes
checking for alloca.h... yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking sys/malloc.h usability... no
checking sys/malloc.h presence... no
checking for sys/malloc.h... no
checking linux/config.h usability... yes
checking linux/config.h presence... yes
checking for linux/config.h... yes
checking sys/resource.h usability... yes
checking sys/resource.h presence... yes
checking for sys/resource.h... yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking for floor in -lm... yes
checking for gethostbyname_r in -lnsl_r... no
checking for gethostbyname_r in -lnsl... yes
checking for gethostbyname_r... yes
checking for setsockopt... yes
checking for yp_get_default_domain... yes
checking for p2open... no
checking for p2open in -lgen... no
checking for bind... yes
checking for crypt in -lcrypt... yes
checking for crypt... yes
checking for sem_init... no
checking for sem_init in -lposix4... no
checking for zlib compression library... system-wide zlib not found, using one bundled with MySQL
checking if we should use pstack...
checking for int8... no
checking "Linux threads"... "no"
checking "DEC threads post OSF/1 3.2"... "no"
checking "SCO threads"... "no"
checking "SCO UnixWare7 native threads"... "no"
checking "OpenUNIX8 native threads"... "no"
checking "Siemens threads"... "no"
checking "Solaris threads"... "no"
checking "named thread libs:"... "no"
checking "for pthread_create in -libc"... "no"
checking "for pthread_create in -lpthread"... "yes"
checking for strtok_r in -lpthread... yes
checking for strtok_r... yes
checking for dlopen in -ldl... yes
checking for unistd.h... (cached) yes
checking for restartable system calls... yes
checking "need of special linking flags"... "none"
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for off_t... yes
checking for struct stat.st_rdev... yes
checking whether time.h and sys/time.h may both be included... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for char... yes
checking size of char... 1
checking for char*... yes
checking size of char*... 4
checking for int... yes
checking size of int... 4
checking for long... yes
checking size of long... 4
checking for long long... yes
checking size of long long... 8
checking size of off_t... 8
checking whether byte ordering is bigendian... no
checking base type of last arg to accept... socklen_t
checking struct type to use with setrlimit... struct rlimit
checking stack direction for C alloca... -1
checking for working alloca.h... (cached) yes
checking for alloca... yes
checking if struct timespec has a ts_sec member... no
checking if we have tzname variable... yes
checking for type ulong... yes
checking for type uchar... no
checking for type uint... yes
checking for type fp_except... no
checking for type in_addr_t... yes
checking if g++ supports bool types... yes
checking if conversion of longlong to float works... yes
checking for sigset_t... yes
checking for off_t... (cached) yes
checking for size_t... (cached) yes
checking for u_int32_t... yes
checking if pthread_yield takes zero arguments... yes
checking if pthread_yield takes 1 argument... no
checking for malloc.h... (cached) yes
checking sys/cdefs.h usability... yes
checking sys/cdefs.h presence... yes
checking for sys/cdefs.h... yes
checking for working alloca.h... yes
checking for alloca... (cached) yes
checking whether gcc needs -traditional... no
checking return type of signal handlers... void
checking for re_comp... yes
checking for regcomp... yes
checking for strdup... yes
checking vis.h usability... no
checking vis.h presence... no
checking for vis.h... no
checking for strlcat... no
checking for strlcpy... no
checking for issetugid... no
checking for fgetln... no
checking for getline... yes
checking for flockfile... yes
checking varargs.h usability... no
checking varargs.h presence... no
checking for varargs.h... no
checking stdarg.h usability... yes
checking stdarg.h presence... yes
checking for stdarg.h... yes
checking dirent.h usability... yes
checking dirent.h presence... yes
checking for dirent.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking ndir.h usability... no
checking ndir.h presence... no
checking for ndir.h... no
checking sys/dir.h usability... yes
checking sys/dir.h presence... yes
checking for sys/dir.h... yes
checking sys/file.h usability... yes
checking sys/file.h presence... yes
checking for sys/file.h... yes
checking sys/ndir.h usability... no
checking sys/ndir.h presence... no
checking for sys/ndir.h... no
checking sys/ptem.h usability... no
checking sys/ptem.h presence... no
checking for sys/ptem.h... no
checking sys/pte.h usability... no
checking sys/pte.h presence... no
checking for sys/pte.h... no
checking sys/select.h usability... yes
checking sys/select.h presence... yes
checking for sys/select.h... yes
checking sys/stream.h usability... no
checking sys/stream.h presence... no
checking for sys/stream.h... no
checking for sys/mman.h... (cached) yes
checking curses.h usability... no
checking curses.h presence... no
checking for curses.h... no
checking termcap.h usability... no
checking termcap.h presence... no
checking for termcap.h... no
checking for termio.h... (cached) yes
checking termbits.h usability... no
checking termbits.h presence... no
checking for termbits.h... no
checking asm/termbits.h usability... yes
checking asm/termbits.h presence... yes
checking for asm/termbits.h... yes
checking grp.h usability... yes
checking grp.h presence... yes
checking for grp.h... yes
checking paths.h usability... yes
checking paths.h presence... yes
checking for paths.h... yes
checking semaphore.h usability... yes
checking semaphore.h presence... yes
checking for semaphore.h... yes
checking for lstat... yes
checking for putenv... yes
checking for select... yes
checking for setenv... yes
checking for setlocale... yes
checking for strcoll... yes
checking for tcgetattr... yes
checking whether stat file-mode macros are broken... no
checking for type of signal functions... posix
checking whether programs are able to redeclare getpw functions... yes
checking for TIOCGWINSZ in sys/ioctl.h... yes
checking for FIONREAD in sys/ioctl.h... yes
checking for TIOCSTAT in sys/ioctl.h... no
checking if struct dirent has a d_ino member... yes
checking if struct dirent has a d_namlen member... no
checking whether signal handlers are of type void... yes
checking for tgetent in -lncurses... no
checking for tgetent in -lcurses... no
checking for tgetent in -ltermcap... no
checking for termcap functions library... configure: error: No curses/termcap library found

I then typed: make
and got this output:
make: *** No targets specified and no makefile found.  Stop.

at which point I gave up, started googlin' and found my way here :-)

The book I have is: Beginning PHP5, Apache, Mysql, Web Development. Wrox Publeshing ISBN: 0-7645-7966-5

Thanks.

---

### Post by abhaysahai on 2005-06-23
Hi,
As we can see from the configure output, that configure did not find ncurses development related files. 
Install the ncurses development libraries and the ndo configure again. After configure passes and creates a makefile, you may do a make. 

OOPS I forgot that this is ubuntu, open synaptic, search for mysql and install. No configure, make etc.... required. ;-)  \\:D/ 

Abhay

---

