---
title: "Clamav  Errors"
date: 2006-01-12
forum: Absolute Beginner Talk
---

### Post by HJThis on 2006-01-12
Hello,To all

First i pray all had a safe newyear

now on to my problem i am trying to install
clamav but i keep gething the old Ver

so i downloaded this here

clamav-0.88.tar.gz

when i try to install as me or root i get this error here

': Permission denied
make[2]: *** [install-libLTLIBRARIES] Error 1
make[2]: Leaving directory `/home/where/clamav-0.88/libclamav'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/where/clamav-0.88/libclamav'
make: *** [install-recursive] Error 1

anyone have any idea what these errors are please

Thank you

---

### Post by paulmilliken on 2006-01-12
[QUOTE=HJThis]Hello,To all

First i pray all had a safe newyear

now on to my problem i am trying to install
clamav but i keep gething the old Ver

so i downloaded this here

clamav-0.88.tar.gz

when i try to install as me or root i get this error here

': Permission denied
make[2]: *** [install-libLTLIBRARIES] Error 1
make[2]: Leaving directory `/home/where/clamav-0.88/libclamav'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/where/clamav-0.88/libclamav'
make: *** [install-recursive] Error 1

anyone have any idea what these errors are please

Thank you[/QUOTE]

Did you do a "./configure" before you typed the "make" command?  If you did then can you please post the output of "./configure"?

Paul

---

### Post by HJThis on 2006-01-12
Hello,paulmilliken

Sorry for the hold-up here

give me one min please

Thank you

---

### Post by HJThis on 2006-01-12
Hi,paulmilliken

I hope this is what you had asked for


@ubuntume:~/clamav-0.88$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
creating target.h - canonical system defines
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gawk... (cached) mawk
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
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking how to recognise dependant libraries... pass_all
checking for egrep... grep -E
checking command to parse /usr/bin/nm -B output... ok
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
checking for ranlib... ranlib
checking for strip... strip
checking for objdir... .libs
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.lo... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking whether the linker (/usr/bin/ld) supports shared libraries... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking whether -lc should be explicitly linked in... no
creating libtool
checking for ANSI C header files... (cached) yes
checking for stdint.h... (cached) yes
checking for unistd.h... (cached) yes
checking sys/int_types.h usability... no
checking sys/int_types.h presence... no
checking for sys/int_types.h... no
checking for dlfcn.h... (cached) yes
checking for inttypes.h... (cached) yes
checking sys/inttypes.h usability... no
checking sys/inttypes.h presence... no
checking for sys/inttypes.h... no
checking for memory.h... (cached) yes
checking ndir.h usability... no
checking ndir.h presence... no
checking for ndir.h... no
checking for stdlib.h... (cached) yes
checking for strings.h... (cached) yes
checking for string.h... (cached) yes
checking sys/mman.h usability... yes
checking sys/mman.h presence... yes
checking for sys/mman.h... yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking for sys/stat.h... (cached) yes
checking for sys/types.h... (cached) yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking poll.h usability... yes
checking poll.h presence... yes
checking for poll.h... yes
checking regex.h usability... yes
checking regex.h presence... yes
checking for regex.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking sys/filio.h usability... no
checking sys/filio.h presence... no
checking for sys/filio.h... no
checking sys/uio.h usability... yes
checking sys/uio.h presence... yes
checking for sys/uio.h... yes
checking syslog.h usability... yes
checking syslog.h presence... yes
checking for syslog.h... yes
checking for off_t... yes
checking size of short... 2
checking size of int... 4
checking size of long... 4
checking size of long long... 8
checking for bind in -lsocket... no
checking for gethostent in -lnsl... yes
checking for poll... yes
checking for setsid... yes
checking for memcpy... yes
checking for snprintf... yes
checking for vsnprintf... yes
checking for strerror_r... yes
checking for strlcpy... no
checking for strlcat... no
checking for inet_ntop... yes
checking for setgroups... yes
checking for initgroups... yes
checking for ctime_r... yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for getpagesize... yes
checking for working mmap... yes
checking for _LARGEFILE_SOURCE value needed for large files... 1
checking for fseeko... yes
checking whether snprintf correctly terminates long strings... yes
checking pthread.h usability... yes
checking pthread.h presence... yes
checking for pthread.h... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for zlib installation... /usr
checking for inflateEnd in -lz... yes
checking for bzReadOpen in -lbz2... no
checking bzlib.h usability... no
checking bzlib.h presence... no
checking for bzlib.h... no
configure: WARNING: ****** bzip2 support disabled
checking for __dn_expand in -lresolv... yes
checking resolv.h usability... yes
checking resolv.h presence... yes
checking for resolv.h... yes
checking whether setpgrp takes no argument... yes
checking for __gmpz_init in -lgmp... no
checking for mpz_init in -lgmp... no
configure: WARNING: ****** GNU MP 2 or newer NOT FOUND - digital signature support will be disabled !
checking for recvmsg... yes
checking for sendmsg... yes
checking for msg_accrights field in struct msghdr... no
checking for msg_control field in struct msghdr... yes
checking for gethostbyname_r... yes, and it takes 6 arguments
checking for readdir_r... support disabled
checking for ctime_r... yes, and it takes 2 arguments
checking for clamav in /etc/passwd... yes, user clamav and group clamav
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether byte ordering is bigendian... no
checking for structure packing via __attribute__((packed))... yes
checking for type aligning via __attribute__((aligned))... yes
checking for fd_set... yes, found in sys/types.h
checking default FD_SETSIZE value... 1024
configure: creating ./config.status
config.status: creating libclamav/Makefile
config.status: creating clamscan/Makefile
config.status: creating database/Makefile
config.status: creating docs/Makefile
config.status: creating clamd/Makefile
config.status: creating clamdscan/Makefile
config.status: creating clamav-milter/Makefile
config.status: creating freshclam/Makefile
config.status: creating sigtool/Makefile
config.status: creating etc/Makefile
config.status: creating Makefile
config.status: creating clamav-config
config.status: creating libclamav.pc
config.status: creating docs/man/clamd.8
config.status: creating docs/man/clamd.conf.5
config.status: creating docs/man/freshclam.1
config.status: creating docs/man/freshclam.conf.5
config.status: creating clamav-config.h
config.status: clamav-config.h is unchanged
config.status: executing depfiles commands
@ubuntume:~/clamav-0.88$

Thank you

---

### Post by HJThis on 2006-01-13
Hello,To all

Anyone have an idea of what clamav is trying
to tell me here.

Thank you

---

