---
title: "Please help with kismet installation."
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by GelflingOne on 2006-06-02
Hello Ubuntu guru's.
Please help me out here.

I have installed ubuntu 5.1
I have installed the kernel headers and gcc.
What am I forgetting here?
I have selected most of the stuff in the synaptic package manager.
Is there an apt-get command to verify/reinstall the needed packages?

Please help. I'm a newbie and my head is turning at this moment. 
It took me quite some time to figure out how to flash my pcmcia wireless card, but finally i figured it out and got it working. Now this problem. I have build some packages in the past, but never saw this error:

root@PowerStation:/home/mrtsxr01/kismet-2006-04-R1# ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
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
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... no
checking how to run the C preprocessor... gcc -E
checking for platform-specific compiler flags... none needed
checking whether byte ordering is bigendian... no
checking for egrep... grep -E
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
checking errno.h usability... yes
checking errno.h presence... yes
checking for errno.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking sys/wait.h usability... yes
checking sys/wait.h presence... yes
checking for sys/wait.h... yes
checking for unistd.h... (cached) yes
checking for sys/types.h... (cached) yes
checking netdb.h usability... yes
checking netdb.h presence... yes
checking for netdb.h... yes
checking getopt.h usability... yes
checking getopt.h presence... yes
checking for getopt.h... yes
checking for an ANSI C-conforming const... yes
checking whether time.h and sys/time.h may both be included... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for ANSI C header files... (cached) yes
checking return type of signal handlers... void
checking whether lstat dereferences a symlink specified with a trailing slash... yes
checking whether stat accepts an empty string... no
checking for gettimeofday... yes
checking for memset... yes
checking for select... yes
checking for socket... yes
checking for strcasecmp... yes
checking for strftime... yes
checking for strstr... yes
checking for system-level getopt_long()... yes
checking for stdint.h... (cached) yes
checking for accept() addrlen type... socklen_t
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for _LARGE_FILES value needed for large files... no
checking for main in -luClibc++... no
configure: WARNING: uclibc++ not available on this system
checking for main in -lstdc++... no
configure: WARNING: libstdc++ not available on this system
configure: error: Neither uclibc uClibc++ or standard gcc stdc++ libraries found.


anyone?

---

### Post by %hMa@?b&lt;C on 2006-06-02
sudo apt-get install build-essential 

try it after running that.  if it still does not work. do a search for the files it says are not found (either using synaptic or going "sudo apt-cache search packagename" replacing packagename with thte thing you are trying to search ofr

---

