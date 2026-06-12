---
title: "x server problem"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by professor on 2006-11-05
i wanted to install the emulator "bochs" but when i run the "./configure" command it tells me that it cannot find x and x libraries are not found. what should i do.

---

### Post by Iarwain ben-adar on 2006-11-05
Hi,
could you post the exact output of that command?

My guess is that you should install X and the -dev package..


Iarwain

---

### Post by professor on 2006-11-05
> checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking if you are configuring for another platform... no
checking for standard CFLAGS on this platform...
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
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
checking whether make sets $(MAKE)... yes
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
checking how to run the C++ preprocessor... /lib/cpp
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
checking for shl_load... no
checking for shl_load in -ldld... no
checking for dlopen... no
checking for dlopen in -ldl... yes
checking whether a program can dlopen itself... yes
checking whether a statically linked program can dlopen itself... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
libtool.m4: error: problem compiling CXX test program
checking for g++ option to produce PIC...
checking if g++ supports -c -o file.o... no
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking for shl_load... (cached) no
checking for shl_load in -ldld... (cached) no
checking for dlopen... (cached) no
checking for dlopen in -ldl... (cached) yes
checking whether a program can dlopen itself... (cached) yes
checking whether a statically linked program can dlopen itself... (cached) yes
appending configuration tag "F77" to libtool
checking for an ANSI C-conforming const... yes
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking which extension is used for loadable modules... .so
checking which variable specifies run-time library path... LD_LIBRARY_PATH
checking for the default library search path... /lib /usr/lib
checking for objdir... .libs
checking whether libtool supports -dlopen/-dlpreopen... yes
checking for shl_load... (cached) no
checking for shl_load in -ldld... (cached) no
checking for dlopen in -ldl... (cached) yes
checking for dlerror... yes
checking for _ prefix in compiled symbols... no
checking whether deplibs are loaded by dlopen... yes
checking argz.h usability... yes
checking argz.h presence... yes
checking for argz.h... yes
checking for error_t... yes
checking for argz_append... yes
checking for argz_create_sep... yes
checking for argz_insert... yes
checking for argz_next... yes
checking for argz_stringify... yes
checking assert.h usability... yes
checking assert.h presence... yes
checking for assert.h... yes
checking ctype.h usability... yes
checking ctype.h presence... yes
checking for ctype.h... yes
checking errno.h usability... yes
checking errno.h presence... yes
checking for errno.h... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking for memory.h... (cached) yes
checking for stdlib.h... (cached) yes
checking stdio.h usability... yes
checking stdio.h presence... yes
checking for stdio.h... yes
checking for unistd.h... (cached) yes
checking dl.h usability... no
checking dl.h presence... no
checking for dl.h... no
checking sys/dl.h usability... no
checking sys/dl.h presence... no
checking for sys/dl.h... no
checking dld.h usability... no
checking dld.h presence... no
checking for dld.h... no
checking mach-o/dyld.h usability... no
checking mach-o/dyld.h presence... no
checking for mach-o/dyld.h... no
checking for string.h... (cached) yes
checking for strchr... yes
checking for strrchr... yes
checking for memcpy... yes
checking for memmove... yes
checking for strcmp... yes
checking for closedir... yes
checking for opendir... yes
checking for readdir... yes
checking for X... no
checking whether byte ordering is bigendian... no
checking for inline... inline
checking for unsigned char... yes
checking size of unsigned char... 1
checking for unsigned short... yes
checking size of unsigned short... 2
checking for unsigned int... yes
checking size of unsigned int... 4
checking for unsigned long... yes
checking size of unsigned long... 4
checking for unsigned long long... yes
checking size of unsigned long long... 8
checking for int *... yes
checking size of int *... 4
checking for getenv... yes
checking for setenv... yes
checking for select... yes
checking for snprintf... yes
checking for vsnprintf... yes
checking for strtoull... yes
checking for strtouq... yes
checking for strdup... yes
checking for strrev... no
checking for sleep... yes
checking for usleep... yes
checking for nanosleep... yes
checking for abort... yes
checking for gettimeofday... yes
checking for socklen_t... yes
checking for struct sockaddr_in.sin_len... no
checking for mkstemp... yes
checking sys/mman.h usability... yes
checking sys/mman.h presence... yes
checking for sys/mman.h... yes
checking for timelocal... yes
checking for gmtime... yes
checking for mktime... yes
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking if large file support is available... yes
checking for cos... no
checking for floor... no
checking if math functions link without -lm... no
checking for sin... yes
checking for ceil... yes
checking if math functions link with -lm... yes
checking for struct timeval... yes
checking if compiler allows empty structs... yes
checking if compiler allows __attribute__... yes
checking for hash_map... no
checking for hash_map.h... no
checking for set... no
checking for set.h... no
checking for new PIT model... yes
checking for idle hack... no
checking for dlfcn.h... (cached) yes
checking for assert.h... (cached) yes
checking for plugins support... no
checking if compiler allows blank labels... no
checking if compiler allows LL for 64-bit constants... yes
checking for x86-64 support... no
checking for SMP support... no
checking for cpu level... 5
checking for APIC support... no
checking zlib.h usability... no
checking zlib.h presence... no
checking for zlib.h... no
checking for compressed hard disk image support... no
checking for NE2000 support... no
checking for i440FX PCI support... no
checking for PCI host device mapping support... no
checking for limited USB support... no
checking for PCI pseudo NIC support... no
checking for 4Meg pages support... yes
checking for PAE support... no
checking for global pages support... no
checking for guest to host TLB support... no
checking for repeated IO and mem copy speedups... no
checking for instruction cache support... no
checking for gcc fast function calls optimization... no
checking for host specific inline assembly accelerations... yes
checking whether to ignore bad MSR references... yes
checking for port e9 hack... yes
checking show IPS... no
checking save/restore support... no
checking for use of .cpp as suffix... no
checking for Bochs internal debugger support... no
checking for external debugger... no
checking for magic breakpoints... no
checking for disassembler support... yes
checking for ALL optimizations enabled... no
checking whether user wants readline... yes
checking whether to use readline... no
checking readline/history.h usability... no
checking readline/history.h presence... no
checking for readline/history.h... no
checking for instrumentation support... no
checking for raw serial support... no
checking for VESA BIOS extensions... no
checking for CLGD54XX emulation... no
checking for FPU emulation... yes
checking for VME support... yes
checking for MMX support... yes
checking for 3DNow! support... no
checking for SSE support... no
checking for DAZ support... no
checking for SEP support... no
checking for x86 debugger support... no
checking IOKit/storage/IOCDMedia.h usability... no
checking IOKit/storage/IOCDMedia.h presence... no
checking for IOKit/storage/IOCDMedia.h... no
checking for CDROM support... yes
checking for Sound Blaster 16 support... no
checking for standard PC gameport support... no
checking for gdb stub enable... no
checking for I/O Interface to the debugger... no
checking for docbook2html... not_found
checking whether to build docbook documentation... no
checking for wx-config... not_found
checking for wxWidgets configuration script... not_found
checking for wxWidgets library version...
configure: WARNING: Bochs for wxWidgets cannot be compiled here, disabling it
checking for default gui on this platform... x11
ERROR: X windows gui was selected, but X windows libraries were not found.
 this is the output

---

### Post by Iarwain ben-adar on 2006-11-05
Hi,
please try this
```
sudo aptitude install libx11-dev
```

That should do the trick i think :D


Iarwain

---

### Post by CatKiller on 2006-11-05
Bochs is in the Universe repository. You can install it with Synaptic.

---

### Post by fakie_flip on 2007-05-10
I see you have usleep, but how did you get it in Ubuntu? I tried searching for it and compiling it, but nothing worked.

```
chris@ubuntu:~/Desktop$ apt-cache search usleep
chris@ubuntu:~/Desktop$ gcc usleep.c -o usleep
usleep.c: In function ‘usleep’:
usleep.c:11: error: ‘NULL’ undeclared (first use in this function)
usleep.c:11: error: (Each undeclared identifier is reported only once
usleep.c:11: error: for each function it appears in.)
chris@ubuntu:~/Desktop$ cat usleep.c 

#include <sys/types.h>
#include <sys/time.h>


void usleep(x) {
        struct timeval  time;

        time.tv_sec= x/1000000;
        time.tv_usec=x%1000000;
        select(0, NULL, NULL, NULL, &time);
        }

chris@ubuntu:~/Desktop$
```

---

### Post by ktulu1115 on 2007-09-12
Having same problem here on Xubuntu Gusty.  I cannot use the pre-compiled package, as I need specific configure options.

./configure --enable-cdrom --enable-sb16 --enable-ne2000 --enable-vbe --enable-pci --enable-clgd54xx --enable-usb --enable-disasm --enable-debugger --enable-apic --enable-plugins --with-x11 --enable-idle-hack

checking for wx-config... not_found
checking for wxWidgets configuration script... not_found
checking for wxWidgets library version... 
configure: WARNING: Bochs for wxWidgets cannot be compiled here, disabling it
checking for default gui on this platform... x11
ERROR: X windows gui was selected, but X windows libraries were not found.

libx11-dev is already installed on my machine:

ktulu@orion:~/coding/bochs-2.3$ dpkg -L libx11-dev | more
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/libx11-dev
/usr/share/doc/libx11-dev/copyright
/usr/share/doc/libx11-dev/changelog.gz
/usr/share/doc/libx11-dev/changelog.Debian.gz
/usr/share/man
/usr/share/man/man3
/usr/share/man/man3/XFlush.3.gz
/usr/share/man/man3/DisplayOfCCC.3.gz
/usr/share/man/man3/IsCursorKey.3.gz
/usr/share/man/man3/XAddConnectionWatch.3.gz
/usr/share/man/man3/XAddHost.3.gz
/usr/share/man/man3/XAllocClassHint.3.gz
/usr/share/man/man3/XAllocColor.3.gz
/usr/share/man/man3/XAllocIconSize.3.gz
/usr/share/man/man3/XAnyEvent.3.gz

I saw in the configure script it spit out...
"checking for X...   no"

Can't figure out exactly why this is coming up, trying to hack away at the configure file and see what I can come up with, but any help is greatly appreciated.

---

### Post by ktulu1115 on 2007-09-12
sudo apt-get install xserver-xorg-dev

---

### Post by RedSquirrel on 2007-09-12
I would recommend installing **xorg-dev**.

EDIT: Whoa. You beat me by just a few seconds. :).

---

### Post by ktulu1115 on 2007-09-12
> **RedSquirrel said:**
> I would recommed installing **xorg-dev**.

I had xorg-dev installed, but it still didn't compile.  xserver-xorg-dev solved the problem.

---

### Post by RedSquirrel on 2007-09-12
> **ktulu1115 said:**
> I had xorg-dev installed, but it still didn't compile.  xserver-xorg-dev solved the problem.
xorg-dev lists xserver-xorg-dev as a dependency.

Some people like to use xlibs-dev instead.

And of course, there's always...

```
sudo apt-get build-dep *package_name*
```if the package is in the repositories. ;)

---

### Post by zellfaze on 2007-11-25
I have installed every package that is mentioned on this page,

xorg-dev
libx11-dev
xserver-xorg-dev
xorg-dev

Still getting the error
ERROR: X windows gui was selected, but X windows libraries were not found.

Any ideas?

---

### Post by RedSquirrel on 2007-11-26
Are you trying to build bochs (like the OP)? If that's in the Ubuntu repositories, you could try:

```
sudo apt-get build-dep bochs
```

That should pull in everything you need for the build. You can do:

```
sudo apt-get build-dep ***package-name***
```

to install the required dependencies for any package that is in the repositories . (man apt-get)

---

### Post by zellfaze on 2007-11-28
I am building it, I would prefer to build this package just so I can configure it to my systems needs. I also no longer have access to the repositories except through the Ubuntu package website. Sorry if I'm coming off as an A-hole, it is unintentional.

---

### Post by RedSquirrel on 2007-11-29
You could try to run apt-get build-dep with the --simulate option to see what would be installed by that command and then get the packages from the web.

Why are you unable to access the repositories? Trying to use a distro without its repositories sounds like a pain in the neck to me. :neutral:

---

### Post by zellfaze on 2007-12-01
Ever since I updated to gutsy the repositories have not been working, keep giving me a connection error. The repositories cant connect to me.... Any how I found a package I can use instead of Bochs its called virtual box. Not bad, sadly the main version of it is not opensource, and the opensource version has less features....

The repositories packages are not listed under APT anymore either (just as an after thought) after I got the could not connect error a few times it decided to take the listings out. I have been getting some packages off the ubuntu packages website, but its very slow doing it that way, since you have to hunt down the dependencies for everything.

---

### Post by RedSquirrel on 2007-12-02
> **zellfaze said:**
> Ever since I updated to gutsy the repositories have not been working, keep giving me a connection error. The repositories cant connect to me.... 

The repositories packages are not listed under APT anymore either (just as an after thought) after I got the could not connect error a few times it decided to take the listings out. I have been getting some packages off the ubuntu packages website, but its very slow doing it that way, since you have to hunt down the dependencies for everything.

I would recommend starting a new thread to sort out the problems you are having with the package manager. It would make your Ubuntu experience much more enjoyable if you didn't have to hunt down packages manually. ;)

---

