---
title: "paranoid about virus scanning"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by japtar10101 on 2007-10-05
I'm very paranoid about viruses, and wanted to ask about updates.  After installing KDE desktop and Klamav (and, of course, clamav), it tells me whether I want to update.  When I do, the following error comes up:
```
checking for zlib installation... /usr
 * configure: error: Please install zlib and zlib-devel packages
***** Return value 1
```
Now, I know this means I should install something, but which one?  I checked out Synaptic, and it seems that way too many packages has the same name.  Please help my technical immune system!

---

### Post by Steveway on 2007-10-05
You don't need Antivirus software on Ubuntu.
You can install it to check your files so you don't spread viruses to your Windows-using friends per E-Mail.
But you don't need it to protect yourself.

---

### Post by skymera on 2007-10-05
welcome to the free world :wink:

---

### Post by russell.h on 2007-10-05
```
sudo aptitude install zlib zlib-dev
```probably ought to do the trick. Not sure though, as I don't have Ubuntu running at the moment.

---

### Post by Pumalite on 2007-10-05
Forget about viruses in Ubuntu.

---

### Post by japtar10101 on 2007-10-05
> **russell.h said:**
> ```
sudo aptitude install zlib zlib-dev
```probably ought to do the trick. Not sure though, as I don't have Ubuntu running at the moment.

Well, I did just that, ran the update, and then.....
```
checking for zlib installation... /usr
 * configure: error: Please install zlib and zlib-devel packages
***** Return value 1
```
So unfortunately, no:(, that didn't solve it.

Perhaps it might help if I copy all the logs over:
```
***** Clamav
***** Running configure (./configure)...
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
creating target.h - canonical system defines
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gawk... (cached) gawk
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking how to recognize dependent libraries... pass_all
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
checking the maximum length of command line arguments... 98304
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
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
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
checking termios.h usability... yes
checking termios.h presence... yes
checking for termios.h... yes
checking iconv.h usability... yes
checking iconv.h presence... yes
checking for iconv.h... yes
checking stdbool.h usability... yes
checking stdbool.h presence... yes
checking for stdbool.h... yes
checking pwd.h usability... yes
checking pwd.h presence... yes
checking for pwd.h... yes
checking grp.h usability... yes
checking grp.h presence... yes
checking for grp.h... yes
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
checking for libiconv_open in -liconv... no
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
checking for mkstemp... yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for getpagesize... yes
checking for working mmap... yes
checking for _LARGEFILE_SOURCE value needed for large files... no
checking whether snprintf correctly terminates long strings... yes
checking pthread.h usability... yes
checking pthread.h presence... yes
checking for pthread.h... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for zlib installation... /usr
 * configure: error: Please install zlib and zlib-devel packages
***** Return value 1
```

---

### Post by wormser on 2007-10-05
> **japtar10101 said:**
> Well, I did just that, ran the update, and then.....
```
checking for zlib installation... /usr
 * configure: error: Please install zlib and zlib-devel packages
***** Return value 1
```
So unfortunately, no:(, that didn't solve it.

That error is telling you to install zlib and zlib-devel packages.  Did you try installing them?

```
sudo apt-get install zlib zlib-devel
```

Then run the command that produced that error.

---

### Post by japtar10101 on 2007-10-05
> **wormser said:**
> That error is telling you to install zlib and zlib-devel packages.  Did you try installing them?

```
sudo apt-get install zlib zlib-devel
```

Then run the command that produced that error.
apt-get couldn't find either.

---

### Post by por100pre1 on 2007-10-05
Try this:

```
sudo apt-get install zlib1g zlib1g-dev
```

---

### Post by japtar10101 on 2007-10-05
> **por100pre1 said:**
> Try this:

```
sudo apt-get install zlib1g zlib1g-dev
```
Ah!  It's compiling!:)

---

### Post by japtar10101 on 2007-10-05
> **japtar10101 said:**
> Ah!  It's compiling!:)

OK, so clamav in now successfully updated.  Klamav isn't.  new error:
```
 * configure: error: Can't find X libraries. Please check your installation and add the correct paths!
***** Return value 1
```
What the heck are the X libraries!?!?!

---

### Post by Kilz on 2007-10-05
You are aware that there are no known linux viruses in the wild. That the anti virus programs for linux like clam are for mail servers that have windows clients connecting. So that windows people dont get attachment viruses. That the scanners are command line and are not constant scanning. That you will have to issue command line commands in a terminal to have them scan each file.

---

### Post by por100pre1 on 2007-10-05
Try this first:

```
sudo aptitude reinstall klamav
```

It seems to be another dependency issue. :-k

---

### Post by japtar10101 on 2007-10-05
> **por100pre1 said:**
> Try this first:

```
sudo aptitude reinstall klamav
```

It seems to be another dependency issue. :-k

...Nope, no dependencies:confused:

---

