---
title: "Nvidia drivers in (K)ubuntu Gutsy?"
date: 2007-08-27
forum: Apple Intel Users
---

### Post by violinmandan on 2007-08-27
I have a MacBook Pro with the new Nvidia card. When I installed Kubuntu, there were (and still are) driver issues (having to use the vesa driver to get any video at all).

Are these issues fixed in the current testing version of Gutsy?

---

### Post by cyberdork33 on 2007-08-27
> **violinmandan said:**
> I have a MacBook Pro with the new Nvidia card. When I installed Kubuntu, there were (and still are) driver issues (having to use the vesa driver to get any video at all).

Are these issues fixed in the current testing version of Gutsy?
Please check the Santa Rosa thread:
[http://ubuntuforums.org/showthread.php?t=474144](http://ubuntuforums.org/showthread.php?t=474144)

---

### Post by violinmandan on 2007-08-27
OK, I looked at the link and I'm trying to install new nvidia drivers. But....
When I try to install them, it says I need to quit my x session. So I press ctrl-alt-del to quit my x session, but it comes right back. So I boot into recovery mode and try to install them. It says I need runlevel 3 or higher. So I go to runlevel 3, but then x starts.......
So, how do I get an x-less session in runlevel 3?

---

### Post by alephsmith on 2007-08-27
Something like this should work.

```
sudo /etc/init.d/kdm stop
```

then restart kdm when you're done.

---

### Post by cyberdork33 on 2007-08-28
> **alephsmith said:**
> Something like this should work.

```
sudo /etc/init.d/kdm stop
```then restart kdm when you're done.

Just for anyone else, in normal Ubuntu it would be:
```
sudo /etc/init.d/gdm stop
```

---

### Post by violinmandan on 2007-08-28
I just installed Kubuntu Gutsy Tribe 5 and was about to install the nvidia driver (according to the instructions on the first post of the Santa Rosa thread), but when I got to the last step (the nvidia-installer program), bash said it didn't exist, even though it autocompleted the name itself.

Feisty didn't have this problem. Instead, it said something about the module build failing...

Could this be because I'm using the 64-bit version? I really don't want to have to use the 32-bit, but if it's the only was to get graphics working....

---

### Post by cyberdork33 on 2007-08-28
> **violinmandan said:**
> I just installed Kubuntu Gutsy Tribe 5 and was about to install the nvidia driver (according to the instructions on the first post of the Santa Rosa thread), but when I got to the last step (the nvidia-installer program), bash said it didn't exist, even though it autocompleted the name itself.

Feisty didn't have this problem. Instead, it said something about the module build failing...

Could this be because I'm using the 64-bit version? I really don't want to have to use the 32-bit, but if it's the only was to get graphics working....
make sure you are using the 64bit drivers... and you may need to make the installer executable before running it. You can do this with the following:
```
sudo chmod +x yourfilename.sh
```

---

### Post by violinmandan on 2007-08-28
OK, the binary driver was 32-bit, so I'm trying to install the new x.org nv driver.
Here's what I got:
```

daniel@melchior:~/Desktop/xf86-video-nv-2.1.3$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
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
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
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
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking for correct ltmain.sh version... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking if RANDR is defined... no
checking if RENDER is defined... no
checking if XV is defined... no
checking if DPMSExtension is defined... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for XORG... configure: error: Package requirements (xorg-server >= 1.2 xproto fontsproto ) were not met:

No package 'xorg-server' found
No package 'xproto' found
No package 'fontsproto' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables XORG_CFLAGS
and XORG_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

Any ideas?
Please...

---

### Post by cyberdork33 on 2007-08-28
> **violinmandan said:**
> [code]checking for XORG... configure: error: Package requirements (xorg-server >= 1.2 xproto fontsproto ) were not met:

No package 'xorg-server' found
No package 'xproto' found
No package 'fontsproto' found

The compiler can't find all the required packages. Are they installed? I am not sure that the open nv driver even works with the santa rosa machines...

You might post in the SantaRosa thread, as the guys that really know what they are doing as far as the Santa Rosa hardware read that thread.

---

