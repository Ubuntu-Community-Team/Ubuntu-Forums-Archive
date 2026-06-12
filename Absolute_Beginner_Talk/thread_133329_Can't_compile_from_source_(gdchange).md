---
title: "Can't compile from source (gdchange)"
date: 2006-02-20
forum: Absolute Beginner Talk
---

### Post by Gadren on 2006-02-20
Since I can't find a way in GNOME's defaults to change the wallpaper at specific intervals (like a slideshow), I found a program called [gdchange](http://sourceforge.net/projects/gdchange) which is supposed to help.  But I can't get it to compile!

To tell the truth, I've never gotten any compiling to work.  Here's the error:

```
daniel@ubuntu:~/Desktop/gdchange-0.2.1$ sudo ./configure
Password:
checking build system type... i686-pc-linux-gnuoldld
checking host system type... i686-pc-linux-gnuoldld
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking whether build environment is sane... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for a BSD-compatible install... /usr/bin/install -c
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

```

So, I have 2 questions:
[b]1: How do I compile programs from source?  I need some kind of newbie's tutorial for this...

2: How can I easily make my desktop wallpaper run as a slideshow in GNOME?[/b]

---

### Post by codejunkie on 2006-02-20
[QUOTE=Gadren]Since I can't find a way in GNOME's defaults to change the wallpaper at specific intervals (like a slideshow), I found a program called [gdchange](http://sourceforge.net/projects/gdchange) which is supposed to help.  But I can't get it to compile!

To tell the truth, I've never gotten any compiling to work.  Here's the error:

```
daniel@ubuntu:~/Desktop/gdchange-0.2.1$ sudo ./configure
Password:
checking build system type... i686-pc-linux-gnuoldld
checking host system type... i686-pc-linux-gnuoldld
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking whether build environment is sane... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for a BSD-compatible install... /usr/bin/install -c
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

```

So, I have 2 questions:
[b]1: How do I compile programs from source?  I need some kind of newbie's tutorial for this...

2: How can I easily make my desktop wallpaper run as a slideshow in GNOME?[/b][/QUOTE]
i dont' know about question 2 but you don't have any c compiler installed copy and paste this in a terminal 
```
sudo apt-get install linux-headers-`uname -r` build-essential
```
this will install your hernel headers and basic compilers
and to compile stuff 
usually this works every time
cd to the package dir and run
```
./configure --prefix=/usr
```
if you have errors look at the output where it stopped it will tell you what package your missing install it and rerun```
./configure --prefix=/usr
```
when it finishes without errors run
```
make
```
again if you have any errors with the make file look through the bottom of the file 
it will tell you what the error was install the required packages and rerun make when it finishes without errors run 
```
sudo make install
```
and your done.

---

### Post by Gadren on 2006-02-20
I can't figure out what I'm missing here...

```
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether build environment is sane... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for a BSD-compatible install... /usr/bin/install -c
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
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking whether make sets $(MAKE)... (cached) yes
checking whether ln -s works... yes
checking whether mkdir accepts -p... yes


POSIX Threads
checking for the pthreads library -lpthreads... no
checking whether pthreads work without any flags... no
checking whether pthreads work with -Kthread... no
checking whether pthreads work with -kthread... no
checking for the pthreads library -llthread... no
checking whether pthreads work with -pthread... yes
checking for joinable pthread attribute... PTHREAD_CREATE_JOINABLE
checking if more special flags are required for pthreads... no
checking for cc_r... gcc
checking how to run the C++ preprocessor... g++ -E
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
checking pthread.h usability... yes
checking pthread.h presence... yes
checking for pthread.h... yes
checking for pthread_create... yes


I/O functions
checking for ANSI C header files... (cached) yes
checking whether stat file-mode macros are broken... no
checking stdio.h usability... yes
checking stdio.h presence... yes
checking for stdio.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking errno.h usability... yes
checking errno.h presence... yes
checking for errno.h... yes
checking for open... yes
checking for read... yes
checking for write... yes
checking for close... yes
checking for printf... yes
checking for sprintf... yes
checking for unlink... yes
checking for exit... no
configure: error: required function missing

```

---

### Post by codejunkie on 2006-02-20
[QUOTE=Gadren]I can't figure out what I'm missing here...

```
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether build environment is sane... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for a BSD-compatible install... /usr/bin/install -c
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
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking whether make sets $(MAKE)... (cached) yes
checking whether ln -s works... yes
checking whether mkdir accepts -p... yes


POSIX Threads
checking for the pthreads library -lpthreads... no
checking whether pthreads work without any flags... no
checking whether pthreads work with -Kthread... no
checking whether pthreads work with -kthread... no
checking for the pthreads library -llthread... no
checking whether pthreads work with -pthread... yes
checking for joinable pthread attribute... PTHREAD_CREATE_JOINABLE
checking if more special flags are required for pthreads... no
checking for cc_r... gcc
checking how to run the C++ preprocessor... g++ -E
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
checking pthread.h usability... yes
checking pthread.h presence... yes
checking for pthread.h... yes
checking for pthread_create... yes


I/O functions
checking for ANSI C header files... (cached) yes
checking whether stat file-mode macros are broken... no
checking stdio.h usability... yes
checking stdio.h presence... yes
checking for stdio.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking errno.h usability... yes
checking errno.h presence... yes
checking for errno.h... yes
checking for open... yes
checking for read... yes
checking for write... yes
checking for close... yes
checking for printf... yes
checking for sprintf... yes
checking for unlink... yes
checking for exit... no
configure: error: required function missing

```[/QUOTE]
i checked out that package you linked to and got the same error trying to compile it. after checking out the site it looks like that package hasn't been worked on in two years it might just be a dead project but those instructions will work compiling most packages.

---

### Post by Gadren on 2006-02-20
:( 'tis a shame.

In that case, does anyone know something else I can use to make my background be a slideshow?

---

### Post by codejunkie on 2006-02-20
i was looking through synaptic and found ```
wallpaper-tray
``` it's in the universe repo if you have it enabled just search synaptic for it, it looks what your asking for.

---

