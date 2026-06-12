---
title: "what more should i synaptic"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by rahul_bhise on 2007-07-10
i am a 2 week  ubuntu (and also linux) user.
i downloaded a .tar.gz package ( it was not in add/remove)from sourceforge. and am trying to install it.
also i learned that to install a software i should install first its dependency from synaptic. i did so
i am attaching a text of terminal 
could anyone help
```
user@uhome:~$ cd /home/user/Desktop/netmate
user@uhome:~/Desktop/netmate$ ./configure
checking build system type... i686-pc-linux
checking host system type... i686-pc-linux
checking target system type... i686-pc-linux
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
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
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for ranlib... ranlib
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
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
checking for ranlib... (cached) ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking for shl_load... no
checking for shl_load in -ldld... no
checking for dlopen... no
checking for dlopen in -ldl... yes
checking whether a program can dlopen itself... yes
checking whether a statically linked program can dlopen itself... no
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
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking whether make sets $(MAKE)... (cached) yes
checking for off_t... yes
checking size of off_t... 4
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking for ANSI C header files... (cached) yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking net/bpf.h usability... no
checking net/bpf.h presence... no
checking for net/bpf.h... no
checking net/ethernet.h usability... yes
checking net/ethernet.h presence... yes
checking for net/ethernet.h... yes
checking ether.h usability... no
checking ether.h presence... no
checking for ether.h... no
checking arpa/inet.h usability... yes
checking arpa/inet.h presence... yes
checking for arpa/inet.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking float.h usability... yes
checking float.h presence... yes
checking for float.h... yes
checking types.h usability... no
checking types.h presence... no
checking for types.h... no
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking netdb.h usability... yes
checking netdb.h presence... yes
checking for netdb.h... yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking termios.h usability... yes
checking termios.h presence... yes
checking for termios.h... yes
checking for unistd.h... (cached) yes
checking for float.h... (cached) yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for pid_t... yes
checking for size_t... yes
checking whether time.h and sys/time.h may both be included... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for alarm... yes
checking for bzero... yes
checking for floor... no
checking for getaddrinfo... yes
checking for inet_ntoa... yes
checking for gettimeofday... yes
checking for memmove... yes
checking for memset... yes
checking for select... yes
checking for socket... yes
checking for strdup... yes
checking for strchr... yes
checking for strerror... yes
checking for strstr... yes
checking for atoll... yes
checking for strtof... yes
checking for getopt_long... yes
checking for floor in -lm... yes
checking for tgetent in -ltermcap... no
checking readline/readline.h usability... no
checking readline/readline.h presence... no
checking for readline/readline.h... no
configure: error: cannot find libreadline headers
user@uhome:~/Desktop/netmate$ make
make: *** No targets specified and no makefile found.  Stop.
user@uhome:~/Desktop/netmate$ make install
make: *** No rule to make target `install'.  Stop.
user@uhome:~/Desktop/netmate$
```
this software keeps track of total internet upload and download .....on all interfaces ( i don't know what the last part means).
is there any other software which does this and easy to install

---

### Post by Raineer on 2007-07-10
libreadline5 and libreadline5-dev, then run ./configure again and look for errors.

By the way, you don't need to run make and make install if your configure ends with an error.  Lastly, make install will require "sudo" in front of it since it's installing to your system.

edit: Also, you can search [http://packages.ubuntu.com/](http://packages.ubuntu.com/)  for packages, just use the name it gave you (readline, in this case)

---

### Post by rahul_bhise on 2007-07-10
yes i did it and it required some more (after looking at the end line).
then 
make  (this scrolled hundreds of lines)
sudo make install     (this to did something)
make clean    (as i read in [http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source))

now i think the software is installed.
[COLOR="Red"]but where is it installed[/COLOR]

---

### Post by sethmahoney on 2007-07-10
You can also try installing software from [http://www.getdeb.net/](http://www.getdeb.net/) which usually is a better option than installing from source.

---

### Post by eentonig on 2007-07-10
What software are you installing (name) and why. Maybe there is an equivalent in the repo's.

---

### Post by rahul_bhise on 2007-07-10
i am installing netmate-0.9.4.
my internet provider gives me only 1gb up/down load per month.
so i have to check now and then that whether i am above the limit.
in windows xp i used netmeter (from  [http://www.metal-machine.de/readerror/](http://www.metal-machine.de/readerror/) )

---

### Post by rahul_bhise on 2007-07-11
so i have done all needful but
[COLOR="Red"][SIZE="2"]where is the software install in my computer[/SIZE][/COLOR]

---

### Post by rahul_bhise on 2007-07-11
please anybody

---

### Post by iver2435 on 2007-07-11
I'll be honest, I just skimmed your post for the most part, so if you mentioned the name of the executable somewhere above, I didn't catch it.

There are a couple different places that it could have installed to, depending on what it is.

The easiest way to find it would be to use "whereis" in a terminal, like this:
```
whereis <program>
```

where <program> is the name of the program you're looking for.  This will give you the directory that the program is in, IF it's in a directory in your path ( which 99% of the time it will be ).

---

### Post by rahul_bhise on 2007-07-12
thanks it worked.
thou i have still more further problems will post these after trying to solve

---

