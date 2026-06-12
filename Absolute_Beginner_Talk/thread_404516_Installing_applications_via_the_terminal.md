---
title: "Installing applications via the terminal"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by alan_uk on 2007-04-08
I have been practicing installing applications from the web, from source, using the terminal.  The apps all have had .tar.gz extensions.  I have had only a 5% success rate so far.  Basically I have extracted the tars into my home folder, extracted them and run the following:- for example

alan@alan-desktop:~$ cd gnuchess*
alan@alan-desktop:~/gnuchess-5.06$ ./configure
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for mawk... mawk
checking whether make sets ${MAKE}... yes
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for executable suffix...
checking for object suffix... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for a BSD compatible install... /usr/bin/install -c
checking for mawk... (cached) mawk
checking whether ln -s works... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for tputs in -lncurses... no
checking for readline in -lreadline... no
checking how to run the C preprocessor... gcc -E
checking for readline/readline.h... no
checking for readline/history.h... no
checking for ANSI C header files... yes
checking for time.h... yes
checking for sys/time.h... yes
checking for unistd.h... yes
checking for errno.h... yes
checking for gcc option to accept ANSI C... none needed
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... (cached) yes
checking for size_t... yes
checking whether time.h and sys/time.h may both be included... yes
checking for stdint-types....... "(putting them into src/GCint.h)"
checking for uintptr_t... yes
checking for uint64_t... yes
... seen our uintptr_t in stdint.h (uint64_t too)
creating src/GCint.h : _SRC_GCINT_H
checking for int_least32_t... yes
checking for int_fast32_t... yes
..adding include stdint.h
... seen good stdint.h inttypes
... seen good uint64_t
... DONE src/GCint.h
checking return type of signal handlers... void
checking for stdlib.h... (cached) yes
checking for working malloc... yes
checking for working memcmp... yes
checking for gettimeofday... yes
checking for strchr... yes
checking for strcspn... yes
checking for strstr... yes
checking for strerror... yes
checking for memset... yes
checking for nanosleep... yes
checking for usleep... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for the pthreads library -lpthreads... no
checking whether pthreads work without any flags... no
checking whether pthreads work with -Kthread... no
checking whether pthreads work with -kthread... no
checking for the pthreads library -llthread... no
checking whether pthreads work with -pthread... yes
checking for joinable pthread attribute... PTHREAD_CREATE_JOINABLE
checking if more special flags are required for pthreads... no
checking for cc_r... gcc
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating src/config.h
config.status: src/config.h is unchanged
alan@alan-desktop:~/gnuchess-5.06$ make
Making all in src
make[1]: Entering directory `/home/alan/gnuchess-5.06/src'
cd .. \
          && CONFIG_FILES= CONFIG_HEADERS=src/config.h \
             /bin/sh ./config.status
config.status: creating src/config.h
config.status: src/config.h is unchanged
make  all-am
make[2]: Entering directory `/home/alan/gnuchess-5.06/src'
source='atak.c' object='atak.o' libtool=no \
        depfile='.deps/atak.Po' tmpdepfile='.deps/atak.TPo' \
        depmode=gcc3 /bin/sh ../depcomp \
        gcc -DHAVE_CONFIG_H -I. -I. -I.    -pthread -g -O2 -c `test -f atak.c || echo './'`atak.c
source='book.c' object='book.o' libtool=no \
        depfile='.deps/book.Po' tmpdepfile='.deps/book.TPo' \
        depmode=gcc3 /bin/sh ../depcomp \
        gcc -DHAVE_CONFIG_H -I. -I. -I.    -pthread -g -O2 -c `test -f book.c || echo './'`book.c
source='cmd.c' object='cmd.o' libtool=no \
        depfile='.deps/cmd.Po' tmpdepfile='.deps/cmd.TPo' \
        depmode=gcc3 /bin/sh ../depcomp \
        gcc -DHAVE_CONFIG_H -I. -I. -I.    -pthread -g -O2 -c `test -f cmd.c || echo './'`cmd.c
source='debug.c' object='debug.o' libtool=no \
        depfile='.deps/debug.Po' tmpdepfile='.deps/debug.TPo' \
        depmode=gcc3 /bin/sh ../depcomp \
        gcc -DHAVE_CONFIG_H -I. -I. -I.    -pthread -g -O2 -c `test -f debug.c || echo './'`debug.c
source='epd.c' object='epd.o' libtool=no \
        depfile='.deps/epd.Po' tmpdepfile='.deps/epd.TPo' \
        depmode=gcc3 /bin/sh ../depcomp \
        gcc -DHAVE_CONFIG_H -I. -I. -I.    -pthread -g -O2 -c `test -f epd.c || echo './'`epd.c
source='eval.c' object='eval.o' libtool=no \
        depfile='.deps/eval.Po' tmpdepfile='.deps/eval.TPo' \
        depmode=gcc3 /bin/sh ../depcomp \
        gcc -DHAVE_CONFIG_H -I. -I. -I.    -pthread -g -O2 -c `test -f eval.c || echo './'`eval.c
source='genmove.c' object='genmove.o' libtool=no \
        depfile='.deps/genmove.Po' tmpdepfile='.deps/genmove.TPo' \
        depmode=gcc3 /bin/sh ../depcomp \
        gcc -DHAVE_CONFIG_H -I. -I. -I.    -pthread -g -O2 -c `test -f genmove.c || echo './'`genmove.c
source='hash.c' object='hash.o' libtool=no \
        depfile='.deps/hash.Po' tmpdepfile='.deps/hash.TPo' \
        depmode=gcc3 /bin/sh ../depcomp \
        gcc -DHAVE_CONFIG_H -I. -I. -I.    -pthread -g -O2 -c `test -f hash.c || echo './'`hash.c
source='hung.c' object='hung.o' libtool=no \
        depfile='.deps/hung.Po' tmpdepfile='.deps/hung.TPo' \
        depmode=gcc3 /bin/sh ../depcomp \
        gcc -DHAVE_CONFIG_H -I. -I. -I.    -pthread -g -O2 -c `test -f hung.c || echo './'`hung.c
source='init.c' object='init.o' libtool=no \
        depfile='.deps/init.Po' tmpdepfile='.deps/init.TPo' \
        depmode=gcc3 /bin/sh ../depcomp \
        gcc -DHAVE_CONFIG_H -I. -I. -I.    -pthread -g -O2 -c `test -f init.c || echo './'`init.c
source='input.c' object='input.o' libtool=no \
        depfile='.deps/input.Po' tmpdepfile='.deps/input.TPo' \
        depmode=gcc3 /bin/sh ../depcomp \
        gcc -DHAVE_CONFIG_H -I. -I. -I.    -pthread -g -O2 -c `test -f input.c || echo './'`input.c
input.c:95: error: static declaration of ‘input_thread’ follows non-static declaration
common.h:725: error: previous declaration of ‘input_thread’ was here
make[2]: *** [input.o] Error 1
make[2]: Leaving directory `/home/alan/gnuchess-5.06/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/alan/gnuchess-5.06/src'
make: *** [all-recursive] Error 1
alan@alan-desktop:~/gnuchess-5.06$

The vast majority throw up error messages. Is this because of dependencies (or the lack of them)?

---

### Post by mac.ryan on 2007-04-08
I am not an expert in compilation, but while building my version of linux from the scratch, I learnt that most of the ./configure scripts can be passed specific parameters.

Most of the parameters you normally give serve to tell the script where specific libraries are installed on your system, or what functions you want to disable/enable. Some parameters are exactly to "adapt" the compilation process to BSD rather than GNU/Linux rather than other POSIX systems.

Often, if you open the configure script there is documentation on what parameters are expected/possible... it is often not trivial, but maybe...

Anyhow: dependencies are a major issue when installing (otherwise people wouldn't have invented package managers!). If your purpose is just to learn how the entire process works, I highly recommend to try building your [LFS]("http://www.linuxfromscratch.org/lfs/")... it's time consuming but highly rewarding in terms of insight! :)

---

### Post by jhenager on 2007-04-08
I would always try running install/configures as root:
~/gnuchess-5.06$sudo ./configure

---

