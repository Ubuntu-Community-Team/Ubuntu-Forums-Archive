---
title: "gutsy - compiling requires X11 but X11 dev installed and it still wants it???!"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by cogvos on 2008-01-13
Dear all,

I am trying to compile sheepshaver, which requires the X11 development headers. 

Its ./configure script cannot find these, yet the libx11-dev package is installed.

Could someone please tell me what Gutsy gibbon calls its X11 headers? I'm going nuts!

J.

---

### Post by SOULRiDER on 2008-01-13
Could you please pos the output from ./configure? You may be missing other libraries.

---

### Post by cogvos on 2008-01-14
Hi SOULRiDER,

Many thanks for the offer of help. After a lot of trial and error, basically adding packages that mentioned X11 development I added GTK1.2 (GTX2.0 was installed already.) This got my past the fail point and produced this result (sorry it is very long) More follows at the end of this list, however as you can see I can now get the ,/configure part to work, or can I?

 + Running aclocal: done.
 + Running autoheader: done.
 + Running autoconf: done.
 + Running 'configure ':
   ** If you wish to pass arguments to ./configure, please
   ** specify them on the command line.
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking whether make sets $(MAKE)... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for file... /usr/bin/file
checking for perl... /usr/bin/perl
checking for PowerPC target CPU... no
checking for mon... no
checking for sem_init in -lposix4... no
checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for pthread_create in -lpthread... yes
checking for pthread_cancel... yes
checking for pthread_cond_init... yes
checking for pthread_testcancel... yes
checking for pthread_mutexattr_setprotocol... yes
checking for pthread_mutexattr_settype... yes
checking for pthread_mutexattr_setpshared... yes
checking for sem_init... yes
checking linux/fb.h usability... yes
checking linux/fb.h presence... yes
checking for linux/fb.h... yes
checking for XF86DGAQueryExtension in -lXxf86dga... yes
checking for XF86VidModeQueryExtension in -lXxf86vm... no
checking for pkg-config... /usr/bin/pkg-config
checking for GTK+ - version >= 1.3.15... yes (version 2.12.0)
checking for esd-config... /usr/bin/esd-config
checking for ESD - version >= 0.2.8... yes
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for ANSI C header files... yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking stdint.h usability... yes
checking stdint.h presence... yes
checking for stdint.h... yes
checking mach/vm_map.h usability... no
checking mach/vm_map.h presence... no
checking for mach/vm_map.h... no
checking mach/mach_init.h usability... no
checking mach/mach_init.h presence... no
checking for mach/mach_init.h... no
checking sys/mman.h usability... yes
checking sys/mman.h presence... yes
checking for sys/mman.h... yes
checking unistd.h usability... yes
checking unistd.h presence... yes
checking for unistd.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking byteswap.h usability... yes
checking byteswap.h presence... yes
checking for byteswap.h... yes
checking dirent.h usability... yes
checking dirent.h presence... yes
checking for dirent.h... yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/filio.h usability... no
checking sys/filio.h presence... no
checking for sys/filio.h... no
checking sys/bitypes.h usability... yes
checking sys/bitypes.h presence... yes
checking for sys/bitypes.h... yes
checking for sys/wait.h... (cached) yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking sys/poll.h usability... yes
checking sys/poll.h presence... yes
checking for sys/poll.h... yes
checking sys/select.h usability... yes
checking sys/select.h presence... yes
checking for sys/select.h... yes
checking arpa/inet.h usability... yes
checking arpa/inet.h presence... yes
checking for arpa/inet.h... yes
checking for linux/if.h... yes
checking for linux/if_tun.h... yes
checking for net/if.h... yes
checking for net/if_tun.h... no
checking AvailabilityMacros.h usability... no
checking AvailabilityMacros.h presence... no
checking for AvailabilityMacros.h... no
checking IOKit/storage/IOBlockStorageDevice.h usability... no
checking IOKit/storage/IOBlockStorageDevice.h presence... no
checking for IOKit/storage/IOBlockStorageDevice.h... no
checking fenv.h usability... yes
checking fenv.h presence... yes
checking for fenv.h... yes
checking whether byte ordering is bigendian... no
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for short... yes
checking size of short... 2
checking for int... yes
checking size of int... 4
checking for long... yes
checking size of long... 4
checking for long long... yes
checking size of long long... 8
checking for float... yes
checking size of float... 4
checking for double... yes
checking size of double... 8
checking for void *... yes
checking size of void *... 4
checking for off_t... yes
checking for loff_t... yes
checking for size_t... yes
checking return type of signal handlers... void
checking whether time.h and sys/time.h may both be included... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for socklen_t... yes
checking whether struct sigaction has sa_restorer... yes
checking for strdup... yes
checking for strerror... yes
checking for strlcpy... no
checking for cfmakeraw... yes
checking for nanosleep... yes
checking for sigaction... yes
checking for signal... yes
checking for mmap... yes
checking for mprotect... yes
checking for munmap... yes
checking for vm_allocate... no
checking for vm_deallocate... no
checking for vm_protect... no
checking for exp2f... yes
checking for log2f... yes
checking for exp2... yes
checking for log2... yes
checking for floorf... yes
checking for roundf... yes
checking for ceilf... yes
checking for truncf... yes
checking for floor... yes
checking for round... yes
checking for ceil... yes
checking for trunc... yes
checking for poll... yes
checking for inet_aton... yes
checking for mach_task_self... no
checking for task_self... no
checking for library containing clock_gettime... -lrt
checking for clock_gettime... yes
checking for clock_nanosleep... yes
checking strings.h usability... yes
checking strings.h presence... yes
checking for strings.h... yes
checking login.h usability... no
checking login.h presence... no
checking for login.h... no
checking sys/bsdtty.h usability... no
checking sys/bsdtty.h presence... no
checking for sys/bsdtty.h... no
checking sys/stat.h usability... yes
checking sys/stat.h presence... yes
checking for sys/stat.h... yes
checking util.h usability... no
checking util.h presence... no
checking for util.h... no
checking pty.h usability... yes
checking pty.h presence... yes
checking for pty.h... yes
checking for _getpty... no
checking for vhangup... yes
checking for strlcpy... (cached) no
checking for /dev/ptc... no
checking whether compiler supports framework Carbon... no
checking whether compiler supports framework IOKit... no
checking whether compiler supports framework CoreFoundation... no
checking whether TUN/TAP is supported... no
checking whether mmap supports MAP_ANON... yes
checking whether mmap supports MAP_ANONYMOUS... yes
checking whether mprotect works... yes
checking whether __PAGEZERO can be Low Memory area 0x0000-0x3000... no
checking whether we can map Low Memory area 0x0000-0x3000... yes
checking whether signal handlers need to be reinstalled... no
checking whether sigaction handlers need to be reinstalled... no
checking whether your system supports Mach exceptions... no
checking whether your system supports Windows exceptions... no
checking whether your system supports extended signal handlers... yes
checking whether we can skip instruction in SIGSEGV handler... yes
checking for addressing mode to use... real
checking floating point format... IEEE (little-endian)
checking for true... /bin/true
checking for GCC 2.7 or higher... yes
checking for GCC 3.0 or higher... yes
checking for ICC... no
checking the format of compiler generated objects... elf
checking whether the compiler supports -fno-strict-aliasing... yes
checking whether the compiler supports -mdynamic-no-pic... no
checking whether dyngen can be used... yes
checking whether static data regions are executable... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating ../MacOSX/Info.plist
config.status: creating config.h
config.status: config.h is unchanged

SheepShaver configuration summary:

SDL support ...................... : none
FBDev DGA support ................ : yes
XFree86 DGA support .............. : yes
XFree86 VidMode support .......... : no
Using PowerPC emulator ........... : yes
Enable JIT compiler .............. : yes
Enable video on SEGV signals ..... : yes
ESD sound support ................ : yes
GTK user interface ............... : gtk2
mon debugger support ............. : no
Addressing mode .................. : real
Bad memory access recovery type .. : siginfo

Configuration done. Now type "make".

I also get some errors (?) in the terminal,

configure.ac:435: warning: underquoted definition of AC_CHECK_FRAMEWORK
  run info '(automake)Extending aclocal'
  or see [http://sources.redhat.com/automake/automake.html#Extending-aclocal](http://sources.redhat.com/automake/automake.html#Extending-aclocal)
configure.ac:539: warning: underquoted definition of AC_TRANSLATE_DEFINE
configure: WARNING: Could not find mon, ignoring --with-mon.
configure: WARNING: Could not find XFree86 VidMode extension, ignoring --enable-xf86-vidmode.
config.status: WARNING:  Makefile.in seems to ignore the --datarootdir setting

You''l notice that it's picked up GTK2, but flatly refused to even get this far without GTX1.2 installed, No idea why.

Also I am getting ACLOCAL warnings. Now I have run into ACLOCAL problems before, and I confess never managed to solve them, giving it up as just baffling. I also do not know if I need worry about finding the XFree86 VidMode headers or what on Earth SDL is.

Typing make produces a lot of warnings and then the following error - sorry again this is long, but I guess there is a lot of linking involved (?)

gcc -I../kpx_cpu/include -I../kpx_cpu/src -DUSE_JIT -I../include -I. -I../slirp -DHAVE_CONFIG_H -D_REENTRANT -DDATADIR=\"/usr/local/share/SheepShaver\" -g -O2  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -c ../kpx_cpu/src/cpu/jit/dyngen.c -o obj/dyngen.o
g++ -I../kpx_cpu/include -I../kpx_cpu/src -DUSE_JIT -I../include -I. -I../slirp -DHAVE_CONFIG_H -D_REENTRANT -DDATADIR=\"/usr/local/share/SheepShaver\" -g -O2  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -c ../kpx_cpu/src/cpu/jit/cxxdemangle.cpp -o obj/cxxdemangle.o
g++ -o dyngen   obj/dyngen.o obj/cxxdemangle.o
./dyngen -o basic-dyngen-ops.hpp obj/basic-dyngen-ops.o
g++ -I../kpx_cpu/include -I../kpx_cpu/src -DUSE_JIT -I../include -I. -I../slirp -DHAVE_CONFIG_H -D_REENTRANT -DDATADIR=\"/usr/local/share/SheepShaver\" -g -O2  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -c ../kpx_cpu/src/cpu/jit/basic-dyngen.cpp -o obj/basic-dyngen.o
g++ -I../kpx_cpu/include -I../kpx_cpu/src -DUSE_JIT -I../include -I. -I../slirp -DHAVE_CONFIG_H -D_REENTRANT -DDATADIR=\"/usr/local/share/SheepShaver\" -g -O2  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -fomit-frame-pointer -mpreferred-stack-boundary=2 -falign-functions=0 -finline-functions -finline-limit=10000 -fno-exceptions -g0 -fno-reorder-blocks -fno-optimize-sibling-calls -c ../kpx_cpu/src/cpu/ppc/ppc-dyngen-ops.cpp -o obj/ppc-dyngen-ops.o
../kpx_cpu/src/cpu/ppc/ppc-dyngen-ops.cpp:39: warning: register used for two global register variables
../kpx_cpu/src/cpu/ppc/ppc-dyngen-ops.cpp:40: warning: register used for two global register variables
../kpx_cpu/src/cpu/ppc/ppc-dyngen-ops.cpp:41: warning: register used for two global register variables
../kpx_cpu/src/cpu/ppc/ppc-dyngen-ops.cpp:42: warning: register used for two global register variables
./dyngen -o ppc-dyngen-ops.hpp obj/ppc-dyngen-ops.o
dyngen: ret or jmp expected at the end of op_jump_next_A0
make: *** [ppc-dyngen-ops.hpp] Error 1

I confess that I do not understand the error at all. I used to programme (years ago) in C, but I guess the code is in C++, a totally different animal. I am not even sure if the current Ubuntu GCC (which I think is 4) is capable of compiling this, the web I downloaded the source from talks about 3.2 and 3.3 as RPMS... but Ubuntu does not use RPMs, does it?

Sorry I am very confused.

J.

---

### Post by SOULRiDER on 2008-01-14
Ok, first of all, lets try to install all the needed (or at least the ones i see are needed)
```
sudo aptitude install libgtk2.0-dev checkinstall libesd0 libesd0-dev
```

Now, download the source from here:
[http://gwenole.beauchesne.free.fr/sheepshaver/files/SheepShaver-2.2-20031125.tar.bz2](http://gwenole.beauchesne.free.fr/sheepshaver/files/SheepShaver-2.2-20031125.tar.bz2) extract, enter the directory and then go to src/unix.

Now do
```
./autogen.sh
```
and finally to compile
```
make
```
Now lets make a deb package and install it
```
checkinstall
```


If that fails try
```
./configure --prefix=/usr
```
```
make
```
```
checkinstall
```

Lets hope this works. If you ahve any errors please post them using the **[code]** tags so theya re much more readable. Theres also an alternative to compiling which is converting an RPM to DEB with alien, but its not really recommended.

Good luck!

---

### Post by cogvos on 2008-01-16
Hi SOULRiDER,

Well I added the package as suggested and obtained the source and success! what is more there were no problems with ACLOCAL. This suggests to me that the source I was using was either old, or corrupted in some way.

Many many thanks for all your help and advice, and also for pointing out the code tag. I didn't know there was one on the forum.

Cheers.

J.

---

### Post by SOULRiDER on 2008-01-16
Awesome, im glad you got it working!! Now, could you please mark the tread as solved? Check out the instructions on how to do it here: 	[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

