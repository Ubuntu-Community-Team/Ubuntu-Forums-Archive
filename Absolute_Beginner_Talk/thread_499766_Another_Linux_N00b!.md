---
title: "Another Linux N00b!"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by slayer666metallica on 2007-07-13
Hey Guys; 

   I just installed Ubuntu today and am pretty much a n00b at everything to deal with it. 


Although; two things in particular are reallly kind of p***ng me off because no matter what I try I can't get it to work.


FYI: I'm using Ubuntu Feisty Fawn [Latest] 32-bit version.

Problem 1: I don't know why; but it seems every few minutes or so I'll get a mssg. in the corner of the screen saying my wired connection has been disconnected. But then; in like 2 seconds it will automatically working again. AkA> I'm getting some of the worst dropouts in Ubuntu and I don't know why. 

Problem 2: For some reason everytime I try to do ANYTHING in the command line; I'll get a totally random error. For example--If I want to install a program that I've downloaded source code for; I'll go into the terminal and follow the instructions according to what just about every manual on the internet tells you to on how to install source; but I never am able to come out with a finished successful installation; could anyone guide through on how to do that?


Thanks In Advance; I love linux so far; but these are some realllly bad aggravations lol

--slayer666metallica

---

### Post by Ek0nomik on 2007-07-13
> **slayer666metallica said:**
> Hey Guys; 

   I just installed Ubuntu today and am pretty much a n00b at everything to deal with it. 


Although; two things in particular are reallly kind of p***ng me off because no matter what I try I can't get it to work.


FYI: I'm using Ubuntu Feisty Fawn [Latest] 32-bit version.

Problem 1: I don't know why; but it seems every few minutes or so I'll get a mssg. in the corner of the screen saying my wired connection has been disconnected. But then; in like 2 seconds it will automatically working again. AkA> I'm getting some of the worst dropouts in Ubuntu and I don't know why. 

Problem 2: For some reason everytime I try to do ANYTHING in the command line; I'll get a totally random error. For example--If I want to install a program that I've downloaded source code for; I'll go into the terminal and follow the instructions according to what just about every manual on the internet tells you to on how to install source; but I never am able to come out with a finished successful installation; could anyone guide through on how to do that?


Thanks In Advance; I love linux so far; but these are some realllly bad aggravations lol

--slayer666metallica

Could you copy and paste your terminal output into a Code box from when you tried to compile the software?  Seeing the actual errors is beneficial.

---

### Post by Nythain on 2007-07-13
on the network problem... sorry cant help there

on the other question... try making sure you have installed build-essential
```

sudo apt-get install build-essential

```
that is a package that will install the basic necessary apps to manually compile software from scratch

then you basically have to pay attention to errors it gives you along the way... most common problem is not having necessary dependencies (often times certain libraries or the -dev version of certain libraries)

then, if you still encounter any problems, you should post what you are trying to install, how you are trying to install it, and any output (including the errors) on here and more than likely someone can help

---

### Post by misfitpierce on 2007-07-13
For connection if you are on router try DMZ'ing your IP to allow ports through... It may be blocking something from router... Possibly router malfunction and perhaps try resetting router and modem?

---

### Post by slayer666metallica on 2007-07-13
I'll try what you guys mentioned; and I'll keep ya posted;) Thanks!

---

### Post by Warren Watts on 2007-07-13
> **slayer666metallica said:**
> For some reason everytime I try to do ANYTHING in the command line; I'll get a totally random error. For example--If I want to install a program that I've downloaded source code for; I'll go into the terminal and follow the instructions according to what just about every manual on the internet tells you to on how to install source; but I never am able to come out with a finished successful installation; could anyone guide through on how to do that?
--slayer666metallica

Unlike a lot of Linux distributions, Ubuntu doesn't allow you to access the root user account.  

So the su command won't work.  Instead, Ubuntu uses the sudo command, which you insert before any command you would normally have to be the root user to run.

So any installations whose instructions say you need to run a command as root, you need to preface it with "**sudo**".

An example:

Software you are trying to install says you have to execute the command "**make install**" as root.

Preface that with "**sudo**": "**sudo make instal**l"

You might already know this, but if you don't, it may be the source of some of your frustrations...

Warren Watts

---

### Post by Nythain on 2007-07-13
hehe... totally forgot to throw that part in there... i was thinkin it, just forgot to type it... thanks for that addition

---

### Post by slayer666metallica on 2007-07-13
ahhh; that very well might be at least one of the reasons why I'm getting so many uncooperative occurences with the command line. ;) 

..but as for the networking problem; I power cycled my dsl modem and my linksys router; and so far no luck at all; I'm still getting dropouts after restarting the modem, router, and the computer itself. So I'm still at a loss with the internet dropout fiasco.

..but for the few minutes that I've rebooted the computer after updating I'm DL'ing the VLC source code right now to attempt at having a successful install of compiled source code; so i'll see how that works too after having a few pointers from the experts! [That is; if I can finish the DL w/ out the internet dropping out on me :D]


Thank You All; The Linux Community is simply amazing with the amount of help on these forums--I love it! Thank you very very much!


p.s. Also I must say that this forum has THE FASTEST replies to threads out of any other I've been on; so I must acknowledge

---

### Post by Nythain on 2007-07-13
i have no life... my girlfriend hates it... i like the community here so much i will spend hours reading through posts and trying to help as many people as possible while watch tv or listening to music

---

### Post by Ek0nomik on 2007-07-13
You may want to keep an eye on this:

[https://answers.launchpad.net/ubuntu/+question/9400](https://answers.launchpad.net/ubuntu/+question/9400)

The dropping seems to be a bug, but maybe yours isn't the same situation.  I don't really know to be honest, but here is a thread with some discussion on it

[http://ubuntuforums.org/showthread.php?t=463588](http://ubuntuforums.org/showthread.php?t=463588)

Other reads that maybe apply to you, but worth looking at regardless:

[http://ubuntuforums.org/showthread.php?t=463758](http://ubuntuforums.org/showthread.php?t=463758)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/109629](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/109629)

---

### Post by slayer666metallica on 2007-07-13
UPDATE: Okay; after getting as far as extracting the tar.gz folder and then navigating to the VLC folder in the terminal; I've run into an error.

What I did was type "sudo ./configure"...

..and then a bunch of random lines of text flashed as usual like normal in the terminal; but then I got my first error which said:

**configure: error: Could not find libmad on your system: you may get it from [http://www.underbit.com/products/mad/](http://www.underbit.com/products/mad/). Alternatively you can use --disable-mad to disable the mad plugin.**

---

### Post by Warren Watts on 2007-07-13
> **slayer666metallica said:**
>  I'm DL'ing the VLC source code right now to attempt at having a successful install of compiled source code; so i'll see how that works too after having a few pointers from the experts! [That is; if I can finish the DL w/ out the internet dropping out on me :D]

Thank You All; The Linux Community is simply amazing with the amount of help on these forums--I love it! Thank you very very much!

p.s. Also I must say that this forum has THE FASTEST replies to threads out of any other I've been on; so I must acknowledge

You know VLC is in the repositories, right?  There is no need to compile it from source.  

You can open the Synaptic Package Manager, click on Search, and type in VLC

It has been my experience so far with Ubuntu that unless the software you are looking for is unusual or obscure, it's usually available in the repositories, ready for your easy installation and already configured for Ubuntu.

As far as pointers from the "experts", I am hardly an expert....I have only had Ubuntu installed for about  six weeks now, and I still have a lot to learn!  

But I will agree that the Ubuntu Forum is a ***WONDERFUL*** resource, filled with lots of helpful people who are more than happy to try and help any and all with problems they may experience installing or using Ubuntu.

I am jjust now at the point where I feel like now and again I can actually post something that might help someone.

Good luck, and welcome to the Community!

---

### Post by Nythain on 2007-07-13
welcome to the wonderfull world of source compilation dependency hell

that woudl be a dep problem, its saying "hi you need mad but you dont have it... get it here or use ./configure with this option to not include mad support"

as a side note, i wouldnt run ./configure with sudo, usually just the make install part needs sudo... 

another side note, if the software is in the repos but you want to compile a more current version, you could try sudo apt-get build-dep packagename
that will attempt to get all the dependencies for the version in the repo (wich shouldnt be any different really than the more current version) so you dont find yourself in dep hell

sudo apt-get build-dep vlc

should get you all the dependencies for the version of vlc in the repos, and after that you can continue the source install

---

### Post by slayer666metallica on 2007-07-13
> **Warren Watts said:**
> You know VLC is in the repositories, right?  There is no need to compile it from source.  

You can open the Synaptic Package Manager, click on Search, and type in VLC

It has been my experience so far with Ubuntu that unless the software you are looking for is unusual or obscure, it's usually available in the repositories, ready for your easy installation and already configured for Ubuntu.

As far as pointers from the "experts", I am hardly an expert....I have only had Ubuntu installed for about  six weeks now, and I still have a lot to learn!  

But I will agree that the Ubuntu Forum is a ***WONDERFUL*** resource, filled with lots of helpful people who are more than happy to try and help any and all with problems they may experience installing or using Ubuntu.

I am jjust now at the point where I feel like now and again I can actually post something that might help someone.

Good luck, and welcome to the Community!


Well I am happy to accept the welcome :)

..but; I did in fact know that you can just get vlc through snyaptic; but like I said before; I'd still like to know how to install from source just for the simple fact that when I *DO* find unusual/obscure programs that might help me; I'll know how to install from source in advance and not have to come here for help and look like a n00b all over again;

...so I guess you could say installing VLC from source code is my 'test drive' of figuring out how to install from source code; 

...but yes; Synaptic/ Add/Remove are GREAT additions to this OS; which is definitely a point that sets itself even more superior to oh....let's say......the crappy windows vista =p


p.s. in fact...that's why I'm figuring out ubuntu right now....--so I don't have to upgrade to Vista....because all I hear are horrible things about it; so I figured now is a better time than ever to install Linux and experience the superiority of it :D


Thanks!

---

### Post by Warren Watts on 2007-07-13
After reading my post, it sort of sounds like I am being rude; I didn't intend to sound so snappy....  

Sometimes jumping in with both feet is the best way to learn things, and compiling from source is definitely one way to learn!  

I recently spent over an hour installing from source  an obscure avatar chat application my 12 year old daughter insisted she had to have...  I would resolve one dependency, only to discover that the library I didn't have installed required two others......  ARRGG!!!  

I did eventually get it compiled from source and installed though, and I did indeed learn a lot.

So compile away, and most of all, **HAVE FUN!!!**

---

### Post by slayer666metallica on 2007-07-13
> **Warren Watts said:**
> After reading my post, it sort of sounds like I am being rude; I didn't intend to sound so snappy....  

Sometimes jumping in with both feet is the best way to learn things, and compiling from source is definitely one way to learn!  

I recently spent over an hour installing from source  an obscure avatar chat application my 12 year old daughter insisted she had to have...  I would resolve one dependency, only to discover that the library I didn't have installed required two others......  ARRGG!!!  

I did eventually get it compiled from source and installed though, and I did indeed learn a lot.

So compile away, and most of all, **HAVE FUN!!!**
hahahahah yes....that's what I'm doing right now :D

but don't worry; you didn't come off as rude--you came off as nothing but helpful :D


..but anyways; i'm kind of in a situation like you described right now...
...because now VLC says I need this one dependency; so I went and downloaded that dependency and now I'm trying to compile **that** from source just so I can get to compiling VLC!


...but I'm now stuck on compiling this depency!! argg!!

..but the only thing is; it's giving me more errors in the terminal when I'm only following the instructions as said in the text file given with the tar.gz archive.....


here's a copy/paste of my actions in Terminal:


[B]jake@Jake:~/Desktop/MAD$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
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
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
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
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
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
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
appending configuration tag "F77" to libtool
checking for ANSI C header files... (cached) yes
checking assert.h usability... yes
checking assert.h presence... yes
checking for assert.h... yes
checking for unistd.h... (cached) yes
checking zlib.h usability... no
checking zlib.h presence... no
checking for zlib.h... no
configure: error: zlib.h was not found
*** You must first install zlib (libz) before you can build this package.
*** If zlib is already installed, you may need to use the CPPFLAGS
*** environment variable to specify its installed location, e.g. -I<dir>.
jake@Jake:~/Desktop/MAD$ sudo make
make: *** No targets specified and no makefile found.  Stop.
jake@Jake:~/Desktop/MAD$ 
[/B]



...as you can see; I got as far as the '**./configure**' step; but after typing in '**sudo make**' as the install instructions said; it gives the error
**"make: *** No targets specified and no makefile found.  Stop."**



...so now I'm once again stuck.

---

### Post by Warren Watts on 2007-07-13
A good portion of the time, you don't need to compile the dependencies themselves, you can simply use the package manager to install the development files.  

Take zlib for example:  If you open Synaptic Package Manager, search for zlib, locate the listing for "zlib1g-dev", right click it and select properties then click on the installed files tab, you will see "zlib.h" listed as being in the package.  

Install the "dev" package instead of compiling the zlib runtime , and voila!  You will have the necessary file installed!!!  (then you can move onto the NEXT dependency.....LOL)

Hope this helps!

Warren

---

### Post by slayer666metallica on 2007-07-13
UGH...NOW I know why they include Synap/Add/Remove...and stuff like that...


after installing all these diff. packages it tells me I don't have [yet still need LOL] 


I was able to get a little farther but now it's telling me this:

**"configure: error: Missing header file ffmpeg/avcodec.h."**



...and as a whole here's a copy/paste of the terminal when I hit the ./configure command after getting all those dependencies....

[B]jake@Jake:~/Desktop/VLC$ sudo ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... yes
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
checking whether gcc and cc understand -c and -o together... yes
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking whether make sets $(MAKE)... (cached) yes
checking for a BSD-compatible install... /usr/bin/install -c
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for an Objective-C compiler... checking dependency style of g++... gcc3
not implemented yet
checking for ranlib... ranlib
checking for strip... strip
checking for ar... ar
checking for ld... ld
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... ld
checking if the linker (ld) is GNU ld... yes
checking for ld option to reload object files... -r
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
checking for ar... (cached) ar
checking for ranlib... (cached) ranlib
checking for strip... (cached) strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (ld) supports shared libraries... yes
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
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... ld
checking if the linker (ld) is GNU ld... yes
checking whether the g++ linker (ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (ld) supports shared libraries... yes
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for libs in extras/contrib... no
configure: WARNING:  not using the libs in extras/contrib as it is not the same host
checking for msgfmt... no
checking for gmsgfmt... :
checking for xgettext... no
checking for msgmerge... no
checking for ranlib... (cached) ranlib
checking for strerror in -lcposix... no
checking for off_t... yes
checking for size_t... yes
checking for working alloca.h... yes
checking for alloca... yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for getpagesize... yes
checking for working mmap... yes
checking whether we are using the GNU C Library 2.1 or newer... yes
checking whether integer division by zero raises SIGFPE... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unsigned long long... yes
checking for inttypes.h... yes
checking whether the inttypes.h PRIxNN macros are broken... no
checking for ld used by GCC... ld
checking if the linker (ld) is GNU ld... yes
checking for shared library run path origin... done
checking argz.h usability... yes
checking argz.h presence... yes
checking for argz.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking nl_types.h usability... yes
checking nl_types.h presence... yes
checking for nl_types.h... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking stddef.h usability... yes
checking stddef.h presence... yes
checking for stddef.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking for feof_unlocked... yes
checking for fgets_unlocked... yes
checking for getc_unlocked... yes
checking for getcwd... yes
checking for getegid... yes
checking for geteuid... yes
checking for getgid... yes
checking for getuid... yes
checking for mempcpy... yes
checking for munmap... yes
checking for putenv... yes
checking for setenv... yes
checking for setlocale... yes
checking for stpcpy... yes
checking for strcasecmp... yes
checking for strdup... yes
checking for strtoul... yes
checking for tsearch... yes
checking for __argz_count... yes
checking for __argz_stringify... yes
checking for __argz_next... yes
checking for iconv... yes
checking for iconv declaration... 
         extern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);
checking for nl_langinfo and CODESET... yes
checking for LC_MESSAGES... yes
checking for bison... no
checking whether NLS is requested... yes
checking whether included gettext is requested... no
checking for GNU gettext in libc... yes
checking for shared objects suffix... .so
checking for prefix to exported symbols... 
checking for gettimeofday... yes
checking for strtod... yes
checking for strtol... yes
checking for strtof... yes
checking for strtoll... yes
checking for strtoull... yes
checking for strsep... yes
checking for isatty... yes
checking for vasprintf... yes
checking for asprintf... yes
checking for swab... yes
checking for sigrelse... yes
checking for getpwuid... yes
checking for memalign... yes
checking for posix_memalign... yes
checking for if_nametoindex... yes
checking for atoll... yes
checking for getenv... yes
checking for putenv... (cached) yes
checking for setenv... (cached) yes
checking for gmtime_r... yes
checking for ctime_r... yes
checking for localtime_r... yes
checking for lrintf... no
checking for daemon... yes
checking for scandir... yes
checking for fork... yes
checking for bsearch... yes
checking for lstat... yes
checking for strlcpy... no
checking for strdup... (cached) yes
checking for strndup... yes
checking for atof... yes
checking for strcasecmp... (cached) yes
checking for strncasecmp... yes
checking for strcasestr... yes
checking for setlocale... (cached) yes
checking langinfo.h usability... yes
checking langinfo.h presence... yes
checking for langinfo.h... yes
checking for nl_langinfo... yes
checking for nl_langinfo and CODESET... yes
checking for connect... yes
checking for send... yes
checking for gethostbyname... yes
checking for socklen_t... yes
checking for struct sockaddr_storage... yes
checking for library containing getaddrinfo... none required
checking for getnameinfo... yes
checking for gai_strerror... yes
checking for struct addrinfo... yes
checking for va_copy... yes
checking for __va_copy... yes
checking for inet_aton... yes
checking for getopt_long... yes
checking return type of signal handlers... void
checking for cos in -lm... yes
checking for pow in -lm... yes
checking for sqrt in -lm... yes
checking for ceil in -lm... yes
checking for sqrtf in -lmx... no
checking mach-o/dyld.h usability... no
checking mach-o/dyld.h presence... no
checking for mach-o/dyld.h... no
checking dl.h usability... no
checking dl.h presence... no
checking for dl.h... no
checking for shl_load... (cached) no
checking for dld_link in -ldld... no
checking image.h usability... no
checking image.h presence... no
checking for image.h... no
checking for load_add_on... no
checking for dlfcn.h... (cached) yes
checking sys/dl.h usability... no
checking sys/dl.h presence... no
checking for sys/dl.h... no
checking for dlopen... (cached) no
checking for dlopen in -ldl... (cached) yes
checking for main in -lpthread... yes
checking for cthread_fork in -lthreads... no
checking for sem_init in -lrt... yes
checking for nanosleep... yes
checking for pthread_cond_t in pthread.h... yes
checking for pthread_once in pthread.h... yes
checking for strncasecmp in strings.h... yes
checking signal.h usability... yes
checking signal.h presence... yes
checking for signal.h... yes
checking time.h usability... yes
checking time.h presence... yes
checking for time.h... yes
checking errno.h usability... yes
checking errno.h presence... yes
checking for errno.h... yes
checking for stdint.h... (cached) yes
checking stdbool.h usability... yes
checking stdbool.h presence... yes
checking for stdbool.h... yes
checking getopt.h usability... yes
checking getopt.h presence... yes
checking for getopt.h... yes
checking for strings.h... (cached) yes
checking for inttypes.h... (cached) yes
checking sys/int_types.h usability... no
checking sys/int_types.h presence... no
checking for sys/int_types.h... no
checking wchar.h usability... yes
checking wchar.h presence... yes
checking for wchar.h... yes
checking sys/sockio.h usability... no
checking sys/sockio.h presence... no
checking for sys/sockio.h... no
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking for sys/types.h... (cached) yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking sys/times.h usability... yes
checking sys/times.h presence... yes
checking for sys/times.h... yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking for sys/stat.h... (cached) yes
checking arpa/inet.h usability... yes
checking arpa/inet.h presence... yes
checking for arpa/inet.h... yes
checking net/if.h usability... yes
checking net/if.h presence... yes
checking for net/if.h... yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking machine/param.h usability... no
checking machine/param.h presence... no
checking for machine/param.h... no
checking sys/shm.h usability... yes
checking sys/shm.h presence... yes
checking for sys/shm.h... yes
checking linux/version.h usability... yes
checking linux/version.h presence... yes
checking for linux/version.h... yes
checking syslog.h usability... yes
checking syslog.h presence... yes
checking for syslog.h... yes
checking whether time.h and sys/time.h may both be included... yes
checking dirent.h usability... yes
checking dirent.h presence... yes
checking for dirent.h... yes
checking for nanosleep in time.h... yes
checking for timespec in sys/time.h... yes
checking cthreads.h usability... no
checking cthreads.h presence... no
checking for cthreads.h... no
checking pthread.h usability... yes
checking pthread.h presence... yes
checking for pthread.h... yes
checking kernel/scheduler.h usability... no
checking kernel/scheduler.h presence... no
checking for kernel/scheduler.h... no
checking kernel/OS.h usability... no
checking kernel/OS.h presence... no
checking for kernel/OS.h... no
checking for X... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for HAL... no
checking for HAL... no
configure: WARNING: HAL library not found
checking for ntohl in sys/param.h... no
checking if $CC accepts -Wall... yes
checking if $CC accepts -Wconversion... yes
checking if $CC accepts -Wunreachable-code... yes
checking if $CC accepts -Wsign-compare... yes
checking if $CC accepts -pipe... yes
checking if $CC accepts -Os... yes
checking if $CC accepts -O3... yes
checking if $CC accepts -O2... yes
checking if $CC accepts -ffast-math... yes
checking if $CC accepts -funroll-loops... yes
checking if $CC accepts -fomit-frame-pointer... yes
checking if $CC accepts -mdynamic-no-pic... no
checking if $CC accepts -bundle -undefined error... no
checking if $CC accepts -shared... yes
checking for variadic cpp macros... yes
checking __attribute__ ((aligned ())) support... 64
checking __attribute__ ((format ())) support with function pointers... yes
checking for __attribute__((packed))... yes
checking if $CC groks MMX inline assembly... yes
checking if $CC groks MMX intrinsics... yes
checking if $CC groks MMX EXT inline assembly... yes
checking if $CC groks 3D Now! inline assembly... yes
checking if $CC groks SSE inline assembly... yes
checking if $CC groks AltiVec inline assembly... no
checking if $CC groks AltiVec C extensions... no
checking altivec.h usability... no
checking altivec.h presence... no
checking for altivec.h... no
checking if linker needs -framework vecLib... no
checking whether gcc accepts -mtune=pentium2... yes
checking for NOTIFY... no
checking dvdread/dvd_reader.h usability... no
checking dvdread/dvd_reader.h presence... no
checking for dvdread/dvd_reader.h... no
checking for dvdnav-config... no
checking libsmbclient.h usability... no
checking libsmbclient.h presence... no
checking for libsmbclient.h... no
checking for struct _SMBCCTX.close_fn... no
checking for dvbpsi/dr.h... no
configure: WARNING: cannot find libdvbpsi headers
checking for dvbpsi_GenSDTSections in -ldvbpsi... no
checking for GNOMEVFS... no
configure: WARNING: GnomeVFS support disabled because GnomeVFS development headers not found
checking for LIBCDIO... no
configure: WARNING: CD Reading and information library not found
checking for VCDINFO... no
configure: WARNING: VCD information library not found
checking for cdrom_msf0 in linux/cdrom.h... yes
checking for scsireq in sys/scsiio.h... no
checking for ioc_toc_header in sys/cdio.h... no
checking for LIBCDDB... no
configure: WARNING: new enough libcddb not found. CDDB access disabled
checking X11/Xlib.h usability... no
checking X11/Xlib.h presence... no
checking for X11/Xlib.h... no
checking for inet_pton... yes
checking for sockaddr_in6 in netinet/in.h... yes
checking ogg/ogg.h usability... no
checking ogg/ogg.h presence... no
checking for ogg/ogg.h... no
checking ebml/EbmlVersion.h usability... no
checking ebml/EbmlVersion.h presence... no
checking for ebml/EbmlVersion.h... no
checking libmodplug/modplug.h usability... no
checking libmodplug/modplug.h presence... no
checking for libmodplug/modplug.h... no
checking mpcdec/mpcdec.h usability... no
checking mpcdec/mpcdec.h presence... no
checking for mpcdec/mpcdec.h... no
checking mad.h usability... yes
checking mad.h presence... yes
checking for mad.h... yes
checking for mad_bit_init in -lmad... yes
checking id3tag.h usability... yes
checking id3tag.h presence... yes
checking for id3tag.h... yes
checking zlib.h usability... yes
checking zlib.h presence... yes
checking for zlib.h... yes
checking for ffmpeg-config... no
checking for FFMPEG... no
checking ffmpeg/avcodec.h usability... no
checking ffmpeg/avcodec.h presence... no
checking for ffmpeg/avcodec.h... no
configure: error: Missing header file ffmpeg/avcodec.h.
[/B]



..and as you can see the configure process stops with the error that I told you about earlier...

...now I'm not really sure what to do.

---

### Post by Paul_world10 on 2007-07-13
wow that rt2500 is a smoker with dapper bummer darn wpa wireless. This is fast paced yale huh

---

### Post by slayer666metallica on 2007-07-13
@Paul_World10

uh...I don't mean to sound stupid...but may I ask what you're talking about? lol

[I'm lost]

---

### Post by Paul_world10 on 2007-07-13
I just dont have the knowledge to run my terminal on that filthy ndiswrapper with no chipset support in my OS. Wrap a windows based driver? Can you wrap my pc on the net also? You guys have a blast and so will I.

---

### Post by slayer666metallica on 2007-07-13
> **Paul_world10 said:**
> I just dont have the knowledge to run my terminal on that filthy ndiswrapper with no chipset support in my OS. Wrap a windows based driver? Can you wrap my pc on the net also? You guys have a blast and so will I.
Your words are like a foreign language to me right now. O_O

[I've only had Ubuntu for a day]

---

### Post by Paul_world10 on 2007-07-13
Can you actually take an ndiswrapper solution and try to make it possible with wpa support? Or are we trying to compile some other OS on an Ubuntu beginer forum website? Can you run Tor yet, or are you building these wrappers?

---

### Post by Warren Watts on 2007-07-13
> **slayer666metallica said:**
> UGH...NOW I know why they include Synap/Add/Remove...and stuff like that...


after installing all these diff. packages it tells me I don't have [yet still need LOL] 

......
checking for ffmpeg-config... no
checking for FFMPEG... no
checking ffmpeg/avcodec.h usability... no
checking ffmpeg/avcodec.h presence... no
checking for ffmpeg/avcodec.h... no
configure: error: Missing header file ffmpeg/avcodec.h.
[/B]



..and as you can see the configure process stops with the error that I told you about earlier...

...now I'm not really sure what to do.

It looks like you need to install ffmpeg and  libavcodec-dev

you *might* get away with just installing  libavcodec-dev , but you may have to install ffmpeg as well.

You sure picked a monster of an application for the first one you wanted to compile from source!!!

---

### Post by slayer666metallica on 2007-07-13
okay! I think I'm *beginning* to get the hang of the terminal more now...

...but DAMN! there is sooooo many extra dependencies that this thing needs just to compile it's UNBELIEVABLE! I don't see how ppl. were able to do this back when synap wasn't around!! *sheesh!*....

..but so far; I'm not having probs; I'll still keep ya posted though;)

---

### Post by slayer666metallica on 2007-07-13
UPDATE: Okay; I think I've got the ./configure part all right now; so now I'm on to the 'make' command and I've got yet ANOTHER error! Here's a copy/paste of all the jargon from the Terminal:

[B]"jake@Jake:~/Desktop/VLC$ sudo make
export MACOSX_DEPLOYMENT_TARGET=
make  all-recursive
make[1]: Entering directory `/home/jake/Desktop/VLC'
Making all in intl
make[2]: Entering directory `/home/jake/Desktop/VLC/intl'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/jake/Desktop/VLC/intl'
Making all in loader
make[2]: Entering directory `/home/jake/Desktop/VLC/loader'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/jake/Desktop/VLC/loader'
Making all in src
make[2]: Entering directory `/home/jake/Desktop/VLC/src'
srcdir=.. builddir=.. ../toolbox --update-version
make  all-recursive
make[3]: Entering directory `/home/jake/Desktop/VLC/src'
make[4]: Entering directory `/home/jake/Desktop/VLC/src'
srcdir=.. builddir=.. ../toolbox --update-version
make[4]: Leaving directory `/home/jake/Desktop/VLC/src'
make[3]: Leaving directory `/home/jake/Desktop/VLC/src'
make[2]: Leaving directory `/home/jake/Desktop/VLC/src'
Making all in modules
make[2]: Entering directory `/home/jake/Desktop/VLC/modules'
Making all in access
make[3]: Entering directory `/home/jake/Desktop/VLC/modules/access'
make[4]: Entering directory `/home/jake/Desktop/VLC/modules/access'
make[4]: `libaccess_file_plugin.so' is up to date.
make[4]: `libaccess_directory_plugin.so' is up to date.
make[4]: `libaccess_udp_plugin.so' is up to date.
make[4]: `libaccess_tcp_plugin.so' is up to date.
make[4]: `libaccess_http_plugin.so' is up to date.
make[4]: `libaccess_ftp_plugin.so' is up to date.
make[4]: `libaccess_fake_plugin.so' is up to date.
make[4]: `libcdda_plugin.so' is up to date.
make[4]: Leaving directory `/home/jake/Desktop/VLC/modules/access'
make  all-recursive
make[4]: Entering directory `/home/jake/Desktop/VLC/modules/access'
Making all in dshow
make[5]: Entering directory `/home/jake/Desktop/VLC/modules/access/dshow'
make  all-recursive
make[6]: Entering directory `/home/jake/Desktop/VLC/modules/access/dshow'
make[7]: Entering directory `/home/jake/Desktop/VLC/modules/access/dshow'
make[7]: Nothing to be done for `all-am'.
make[7]: Leaving directory `/home/jake/Desktop/VLC/modules/access/dshow'
make[6]: Leaving directory `/home/jake/Desktop/VLC/modules/access/dshow'
make[5]: Leaving directory `/home/jake/Desktop/VLC/modules/access/dshow'
Making all in dvb
make[5]: Entering directory `/home/jake/Desktop/VLC/modules/access/dvb'
make  all-recursive
make[6]: Entering directory `/home/jake/Desktop/VLC/modules/access/dvb'
make[7]: Entering directory `/home/jake/Desktop/VLC/modules/access/dvb'
make[7]: Nothing to be done for `all-am'.
make[7]: Leaving directory `/home/jake/Desktop/VLC/modules/access/dvb'
make[6]: Leaving directory `/home/jake/Desktop/VLC/modules/access/dvb'
make[5]: Leaving directory `/home/jake/Desktop/VLC/modules/access/dvb'
Making all in mms
make[5]: Entering directory `/home/jake/Desktop/VLC/modules/access/mms'
make[6]: Entering directory `/home/jake/Desktop/VLC/modules/access/mms'
make[6]: `libaccess_mms_plugin.so' is up to date.
make[6]: Leaving directory `/home/jake/Desktop/VLC/modules/access/mms'
make  all-recursive
make[6]: Entering directory `/home/jake/Desktop/VLC/modules/access/mms'
make[7]: Entering directory `/home/jake/Desktop/VLC/modules/access/mms'
make[7]: Nothing to be done for `all-am'.
make[7]: Leaving directory `/home/jake/Desktop/VLC/modules/access/mms'
make[6]: Leaving directory `/home/jake/Desktop/VLC/modules/access/mms'
make[5]: Leaving directory `/home/jake/Desktop/VLC/modules/access/mms'
Making all in v4l
make[5]: Entering directory `/home/jake/Desktop/VLC/modules/access/v4l'
make  all-recursive
make[6]: Entering directory `/home/jake/Desktop/VLC/modules/access/v4l'
make[7]: Entering directory `/home/jake/Desktop/VLC/modules/access/v4l'
make[7]: Nothing to be done for `all-am'.
make[7]: Leaving directory `/home/jake/Desktop/VLC/modules/access/v4l'
make[6]: Leaving directory `/home/jake/Desktop/VLC/modules/access/v4l'
make[5]: Leaving directory `/home/jake/Desktop/VLC/modules/access/v4l'
Making all in cdda
make[5]: Entering directory `/home/jake/Desktop/VLC/modules/access/cdda'
make  all-recursive
make[6]: Entering directory `/home/jake/Desktop/VLC/modules/access/cdda'
make[7]: Entering directory `/home/jake/Desktop/VLC/modules/access/cdda'
make[7]: Nothing to be done for `all-am'.
make[7]: Leaving directory `/home/jake/Desktop/VLC/modules/access/cdda'
make[6]: Leaving directory `/home/jake/Desktop/VLC/modules/access/cdda'
make[5]: Leaving directory `/home/jake/Desktop/VLC/modules/access/cdda'
Making all in rtsp
make[5]: Entering directory `/home/jake/Desktop/VLC/modules/access/rtsp'
make  all-recursive
make[6]: Entering directory `/home/jake/Desktop/VLC/modules/access/rtsp'
make[7]: Entering directory `/home/jake/Desktop/VLC/modules/access/rtsp'
make[7]: Nothing to be done for `all-am'.
make[7]: Leaving directory `/home/jake/Desktop/VLC/modules/access/rtsp'
make[6]: Leaving directory `/home/jake/Desktop/VLC/modules/access/rtsp'
make[5]: Leaving directory `/home/jake/Desktop/VLC/modules/access/rtsp'
Making all in vcd
make[5]: Entering directory `/home/jake/Desktop/VLC/modules/access/vcd'
make[6]: Entering directory `/home/jake/Desktop/VLC/modules/access/vcd'
make[6]: `libvcd_plugin.so' is up to date.
make[6]: Leaving directory `/home/jake/Desktop/VLC/modules/access/vcd'
make  all-recursive
make[6]: Entering directory `/home/jake/Desktop/VLC/modules/access/vcd'
make[7]: Entering directory `/home/jake/Desktop/VLC/modules/access/vcd'
make[7]: Nothing to be done for `all-am'.
make[7]: Leaving directory `/home/jake/Desktop/VLC/modules/access/vcd'
make[6]: Leaving directory `/home/jake/Desktop/VLC/modules/access/vcd'
make[5]: Leaving directory `/home/jake/Desktop/VLC/modules/access/vcd'
Making all in vcdx
make[5]: Entering directory `/home/jake/Desktop/VLC/modules/access/vcdx'
make  all-recursive
make[6]: Entering directory `/home/jake/Desktop/VLC/modules/access/vcdx'
make[7]: Entering directory `/home/jake/Desktop/VLC/modules/access/vcdx'
make[7]: Nothing to be done for `all-am'.
make[7]: Leaving directory `/home/jake/Desktop/VLC/modules/access/vcdx'
make[6]: Leaving directory `/home/jake/Desktop/VLC/modules/access/vcdx'
make[5]: Leaving directory `/home/jake/Desktop/VLC/modules/access/vcdx'
Making all in screen
make[5]: Entering directory `/home/jake/Desktop/VLC/modules/access/screen'
make  all-recursive
make[6]: Entering directory `/home/jake/Desktop/VLC/modules/access/screen'
make[7]: Entering directory `/home/jake/Desktop/VLC/modules/access/screen'
make[7]: Nothing to be done for `all-am'.
make[7]: Leaving directory `/home/jake/Desktop/VLC/modules/access/screen'
make[6]: Leaving directory `/home/jake/Desktop/VLC/modules/access/screen'
make[5]: Leaving directory `/home/jake/Desktop/VLC/modules/access/screen'
make[5]: Entering directory `/home/jake/Desktop/VLC/modules/access'
make[5]: Nothing to be done for `all-am'.
make[5]: Leaving directory `/home/jake/Desktop/VLC/modules/access'
make[4]: Leaving directory `/home/jake/Desktop/VLC/modules/access'
make[3]: Leaving directory `/home/jake/Desktop/VLC/modules/access'
Making all in access_filter
make[3]: Entering directory `/home/jake/Desktop/VLC/modules/access_filter'
make[4]: Entering directory `/home/jake/Desktop/VLC/modules/access_filter'
make[4]: `libaccess_filter_timeshift_plugin.so' is up to date.
make[4]: `libaccess_filter_record_plugin.so' is up to date.
make[4]: `libaccess_filter_dump_plugin.so' is up to date.
make[4]: Leaving directory `/home/jake/Desktop/VLC/modules/access_filter'
make  all-recursive
make[4]: Entering directory `/home/jake/Desktop/VLC/modules/access_filter'
make[5]: Entering directory `/home/jake/Desktop/VLC/modules/access_filter'
make[5]: Nothing to be done for `all-am'.
make[5]: Leaving directory `/home/jake/Desktop/VLC/modules/access_filter'
make[4]: Leaving directory `/home/jake/Desktop/VLC/modules/access_filter'
make[3]: Leaving directory `/home/jake/Desktop/VLC/modules/access_filter'
Making all in access_output
make[3]: Entering directory `/home/jake/Desktop/VLC/modules/access_output'
make[4]: Entering directory `/home/jake/Desktop/VLC/modules/access_output'
make[4]: `libaccess_output_dummy_plugin.so' is up to date.
make[4]: `libaccess_output_file_plugin.so' is up to date.
make[4]: `libaccess_output_udp_plugin.so' is up to date.
make[4]: `libaccess_output_http_plugin.so' is up to date.
make[4]: Leaving directory `/home/jake/Desktop/VLC/modules/access_output'
make  all-recursive
make[4]: Entering directory `/home/jake/Desktop/VLC/modules/access_output'
make[5]: Entering directory `/home/jake/Desktop/VLC/modules/access_output'
make[5]: Nothing to be done for `all-am'.
make[5]: Leaving directory `/home/jake/Desktop/VLC/modules/access_output'
make[4]: Leaving directory `/home/jake/Desktop/VLC/modules/access_output'
make[3]: Leaving directory `/home/jake/Desktop/VLC/modules/access_output'
Making all in audio_filter
make[3]: Entering directory `/home/jake/Desktop/VLC/modules/audio_filter'
make[4]: Entering directory `/home/jake/Desktop/VLC/modules/audio_filter'
make[4]: `libequalizer_plugin.so' is up to date.
make[4]: `libnormvol_plugin.so' is up to date.
make[4]: `libaudio_format_plugin.so' is up to date.
make[4]: `libparam_eq_plugin.so' is up to date.
make[4]: Leaving directory `/home/jake/Desktop/VLC/modules/audio_filter'
make  all-recursive
make[4]: Entering directory `/home/jake/Desktop/VLC/modules/audio_filter'
Making all in channel_mixer
make[5]: Entering directory `/home/jake/Desktop/VLC/modules/audio_filter/channel_mixer'
make[6]: Entering directory `/home/jake/Desktop/VLC/modules/audio_filter/channel_mixer'
make[6]: `libtrivial_channel_mixer_plugin.so' is up to date.
make[6]: `libsimple_channel_mixer_plugin.so' is up to date.
make[6]: `libheadphone_channel_mixer_plugin.so' is up to date.
make[6]: `libdolby_surround_decoder_plugin.so' is up to date.
make[6]: Leaving directory `/home/jake/Desktop/VLC/modules/audio_filter/channel_mixer'
make  all-recursive
make[6]: Entering directory `/home/jake/Desktop/VLC/modules/audio_filter/channel_mixer'
make[7]: Entering directory `/home/jake/Desktop/VLC/modules/audio_filter/channel_mixer'
make[7]: Nothing to be done for `all-am'.
make[7]: Leaving directory `/home/jake/Desktop/VLC/modules/audio_filter/channel_mixer'
make[6]: Leaving directory `/home/jake/Desktop/VLC/modules/audio_filter/channel_mixer'
make[5]: Leaving directory `/home/jake/Desktop/VLC/modules/audio_filter/channel_mixer'
Making all in converter
make[5]: Entering directory `/home/jake/Desktop/VLC/modules/audio_filter/converter'
make[6]: Entering directory `/home/jake/Desktop/VLC/modules/audio_filter/converter'
make[6]: `libfloat32tos16_plugin.so' is up to date.
make[6]: `libfloat32tos8_plugin.so' is up to date.
make[6]: `libfloat32tou16_plugin.so' is up to date.
make[6]: `libfloat32tou8_plugin.so' is up to date.
make[6]: `liba52tospdif_plugin.so' is up to date.
make[6]: `liba52tofloat32_plugin.so' is up to date.
make[6]: `libdtstospdif_plugin.so' is up to date.
make[6]: `libdtstofloat32_plugin.so' is up to date.
make[6]: `libfixed32tos16_plugin.so' is up to date.
make[6]: `libs16tofixed32_plugin.so' is up to date.
make[6]: `libfixed32tofloat32_plugin.so' is up to date.
make[6]: `libs16tofloat32_plugin.so' is up to date.
make[6]: `libs16tofloat32swab_plugin.so' is up to date.
make[6]: `libs8tofloat32_plugin.so' is up to date.
make[6]: `libu8tofixed32_plugin.so' is up to date.
make[6]: `libu8tofloat32_plugin.so' is up to date.
make[6]: `libmpgatofixed32_plugin.so' is up to date.
make[6]: Leaving directory `/home/jake/Desktop/VLC/modules/audio_filter/converter'
make  all-recursive
make[6]: Entering directory `/home/jake/Desktop/VLC/modules/audio_filter/converter'
make[7]: Entering directory `/home/jake/Desktop/VLC/modules/audio_filter/converter'
make[7]: Nothing to be done for `all-am'.
make[7]: Leaving directory `/home/jake/Desktop/VLC/modules/audio_filter/converter'
make[6]: Leaving directory `/home/jake/Desktop/VLC/modules/audio_filter/converter'
make[5]: Leaving directory `/home/jake/Desktop/VLC/modules/audio_filter/converter'
Making all in resampler
make[5]: Entering directory `/home/jake/Desktop/VLC/modules/audio_filter/resampler'
make[6]: Entering directory `/home/jake/Desktop/VLC/modules/audio_filter/resampler'
make[6]: `libtrivial_resampler_plugin.so' is up to date.
make[6]: `libugly_resampler_plugin.so' is up to date.
make[6]: `liblinear_resampler_plugin.so' is up to date.
make[6]: `libbandlimited_resampler_plugin.so' is up to date.
make[6]: Leaving directory `/home/jake/Desktop/VLC/modules/audio_filter/resampler'
make  all-recursive
make[6]: Entering directory `/home/jake/Desktop/VLC/modules/audio_filter/resampler'
make[7]: Entering directory `/home/jake/Desktop/VLC/modules/audio_filter/resampler'
make[7]: Nothing to be done for `all-am'.
make[7]: Leaving directory `/home/jake/Desktop/VLC/modules/audio_filter/resampler'
make[6]: Leaving directory `/home/jake/Desktop/VLC/modules/audio_filter/resampler'
make[5]: Leaving directory `/home/jake/Desktop/VLC/modules/audio_filter/resampler'
make[5]: Entering directory `/home/jake/Desktop/VLC/modules/audio_filter'
make[5]: Nothing to be done for `all-am'.
make[5]: Leaving directory `/home/jake/Desktop/VLC/modules/audio_filter'
make[4]: Leaving directory `/home/jake/Desktop/VLC/modules/audio_filter'
make[3]: Leaving directory `/home/jake/Desktop/VLC/modules/audio_filter'
Making all in audio_mixer
make[3]: Entering directory `/home/jake/Desktop/VLC/modules/audio_mixer'
make[4]: Entering directory `/home/jake/Desktop/VLC/modules/audio_mixer'
make[4]: `libtrivial_mixer_plugin.so' is up to date.
make[4]: `libfloat32_mixer_plugin.so' is up to date.
make[4]: `libspdif_mixer_plugin.so' is up to date.
make[4]: Leaving directory `/home/jake/Desktop/VLC/modules/audio_mixer'
make  all-recursive
make[4]: Entering directory `/home/jake/Desktop/VLC/modules/audio_mixer'
make[5]: Entering directory `/home/jake/Desktop/VLC/modules/audio_mixer'
make[5]: Nothing to be done for `all-am'.
make[5]: Leaving directory `/home/jake/Desktop/VLC/modules/audio_mixer'
make[4]: Leaving directory `/home/jake/Desktop/VLC/modules/audio_mixer'
make[3]: Leaving directory `/home/jake/Desktop/VLC/modules/audio_mixer'
Making all in audio_output
make[3]: Entering directory `/home/jake/Desktop/VLC/modules/audio_output'
make[4]: Entering directory `/home/jake/Desktop/VLC/modules/audio_output'
make[4]: `libaout_file_plugin.so' is up to date.
make[4]: `liboss_plugin.so' is up to date.
make[4]: Leaving directory `/home/jake/Desktop/VLC/modules/audio_output'
make  all-recursive
make[4]: Entering directory `/home/jake/Desktop/VLC/modules/audio_output'
make[5]: Entering directory `/home/jake/Desktop/VLC/modules/audio_output'
make[5]: Nothing to be done for `all-am'.
make[5]: Leaving directory `/home/jake/Desktop/VLC/modules/audio_output'
make[4]: Leaving directory `/home/jake/Desktop/VLC/modules/audio_output'
make[3]: Leaving directory `/home/jake/Desktop/VLC/modules/audio_output'
Making all in codec
make[3]: Entering directory `/home/jake/Desktop/VLC/modules/codec'
make[4]: Entering directory `/home/jake/Desktop/VLC/modules/codec'
make[4]: `liba52_plugin.so' is up to date.
make[4]: `libcinepak_plugin.so' is up to date.
make[4]: `libdts_plugin.so' is up to date.
make[4]: `libflacdec_plugin.so' is up to date.
make[4]: `liblpcm_plugin.so' is up to date.
make[4]: `libaraw_plugin.so' is up to date.
make[4]: `libvorbis_plugin.so' is up to date.
make[4]: `libadpcm_plugin.so' is up to date.
make[4]: `libmpeg_audio_plugin.so' is up to date.
make[4]: `liblibmpeg2_plugin.so' is up to date.
make[4]: `librawvideo_plugin.so' is up to date.
make[4]: `libsubsdec_plugin.so' is up to date.
make[4]: `libdvbsub_plugin.so' is up to date.
make[4]: `libtelx_plugin.so' is up to date.
make[4]: `libsvcdsub_plugin.so' is up to date.
make[4]: `libcvdsub_plugin.so' is up to date.
make[4]: `libfake_plugin.so' is up to date.
make[4]: Leaving directory `/home/jake/Desktop/VLC/modules/codec'
make  all-recursive
make[4]: Entering directory `/home/jake/Desktop/VLC/modules/codec'
Making all in cmml
make[5]: Entering directory `/home/jake/Desktop/VLC/modules/codec/cmml'
make[6]: Entering directory `/home/jake/Desktop/VLC/modules/codec/cmml'
make[6]: `libcmml_plugin.so' is up to date.
make[6]: Leaving directory `/home/jake/Desktop/VLC/modules/codec/cmml'
make  all-recursive
make[6]: Entering directory `/home/jake/Desktop/VLC/modules/codec/cmml'
make[7]: Entering directory `/home/jake/Desktop/VLC/modules/codec/cmml'
make[7]: Nothing to be done for `all-am'.
make[7]: Leaving directory `/home/jake/Desktop/VLC/modules/codec/cmml'
make[6]: Leaving directory `/home/jake/Desktop/VLC/modules/codec/cmml'
make[5]: Leaving directory `/home/jake/Desktop/VLC/modules/codec/cmml'
Making all in dmo
make[5]: Entering directory `/home/jake/Desktop/VLC/modules/codec/dmo'
make  all-recursive
make[6]: Entering directory `/home/jake/Desktop/VLC/modules/codec/dmo'
make[7]: Entering directory `/home/jake/Desktop/VLC/modules/codec/dmo'
make[7]: Nothing to be done for `all-am'.
make[7]: Leaving directory `/home/jake/Desktop/VLC/modules/codec/dmo'
make[6]: Leaving directory `/home/jake/Desktop/VLC/modules/codec/dmo'
make[5]: Leaving directory `/home/jake/Desktop/VLC/modules/codec/dmo'
Making all in ffmpeg
make[5]: Entering directory `/home/jake/Desktop/VLC/modules/codec/ffmpeg'
make[6]: Entering directory `/home/jake/Desktop/VLC/modules/codec/ffmpeg'
if gcc -DHAVE_CONFIG_H -I. -I. -I../../..   -DSYS_LINUX -I../../../include `top_builddir="../../.." ../../../vlc-config --cflags plugin ffmpeg` -Wsign-compare -Wall  -pipe -MT libffmpeg_plugin_a-demux.o -MD -MP -MF ".deps/libffmpeg_plugin_a-demux.Tpo" \
          -c -o libffmpeg_plugin_a-demux.o `test -f 'demux.c' || echo './'`demux.c; \
        then mv -f ".deps/libffmpeg_plugin_a-demux.Tpo" ".deps/libffmpeg_plugin_a-demux.Po"; \
        else rm -f ".deps/libffmpeg_plugin_a-demux.Tpo"; exit 1; \
        fi
demux.c:38:25: error: avformat.h: No such file or directory
In file included from demux.c:41:
ffmpeg.h:44: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;AVCodecContext&#8217;
ffmpeg.h:44: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;AVCodec&#8217;
ffmpeg.h:50: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;AVCodecContext&#8217;
ffmpeg.h:50: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;AVCodec&#8217;
ffmpeg.h:85: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;AVFrame&#8217;
make[6]: *** [libffmpeg_plugin_a-demux.o] Error 1
make[6]: Leaving directory `/home/jake/Desktop/VLC/modules/codec/ffmpeg'
make[5]: *** [all-modules] Error 1
make[5]: Leaving directory `/home/jake/Desktop/VLC/modules/codec/ffmpeg'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/jake/Desktop/VLC/modules/codec'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/jake/Desktop/VLC/modules/codec'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/jake/Desktop/VLC/modules'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/jake/Desktop/VLC'
make: *** [all] Error 2
jake@Jake:~/Desktop/VLC$ 

"[/B]








Okay; so yet ANOTHER error after typing in the 'sudo make' part of the compile process; but now it gives me THIS error at the end:

[B]demux.c:38:25: error: avformat.h: No such file or directory
In file included from demux.c:41:
ffmpeg.h:44: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;AVCodecContext&#8217;
ffmpeg.h:44: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;AVCodec&#8217;
ffmpeg.h:50: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;AVCodecContext&#8217;
ffmpeg.h:50: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;AVCodec&#8217;
ffmpeg.h:85: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;AVFrame&#8217;
make[6]: *** [libffmpeg_plugin_a-demux.o] Error 1
make[6]: Leaving directory `/home/jake/Desktop/VLC/modules/codec/ffmpeg'
make[5]: *** [all-modules] Error 1
make[5]: Leaving directory `/home/jake/Desktop/VLC/modules/codec/ffmpeg'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/jake/Desktop/VLC/modules/codec'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/jake/Desktop/VLC/modules/codec'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/jake/Desktop/VLC/modules'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/jake/Desktop/VLC'
make: *** [all] Error 2[/B]


Lost and stumped once again about how to fix this. :/....got any ideas? lol

---

### Post by Warren Watts on 2007-07-13
> **slayer666metallica said:**
> okay! I think I'm *beginning* to get the hang of the terminal more now...

...but DAMN! there is sooooo many extra dependencies that this thing needs just to compile it's UNBELIEVABLE! I don't see how ppl. were able to do this back when synap wasn't around!! *sheesh!*....

..but so far; I'm not having probs; I'll still keep ya posted though;)

I have to admire your dedication... =D>  

Just remember that it doesn't have to be this hard; 99.9% of the time, the binary (already compiled app) available in the repositories for any given application you want to use is quite often the latest and greatest release anyway.

Unless there is a newer release that adds some new feature you *have* to have, or fixes a bug in the version that is in the repository, there generally isn't any need to compile from source.  Just install from the repository and have at it!

As a learning exercise, what you are trying to do is worthwhile, maybe you should have chosen a simpler application to try and compile from source.... ](*,)

Good luck!

---

### Post by slayer666metallica on 2007-07-13
ahhh...well warren....I must say that i'm throwing in the towel....:confused:

....you're right--VLC is a VERY complex source code to start and try to compile for such a linux n00b like me when there's a much faster way to get it....

...so...I still wanna learn to compile source....but next time it'll be on a LOT smaller scale LOL;;

...I'm at a loss...but thank god for Synaptic Package Manager :D

AWESOME! 

Well; thanks for the help though; since you're the only one that stuck it out with me and stayed for help; I appreciate it; ...
..now I'm off to install VLC...the EASY WAY! LOL


Thanks!

---

### Post by Warren Watts on 2007-07-13
> **slayer666metallica said:**
> UPDATE: Okay; I think I've got the ./configure part all right now; so now I'm on to the 'make' command and I've got yet ANOTHER error! Here's a copy/paste of all the jargon from the Terminal:

. . . . . . . .
demux.c:38:25: error: avformat.h: No such file or directory
In file included from demux.c:41:
. . . . . . . . 

Lost and stumped once again about how to fix this. :/....got any ideas? lol

Try installing the libavformat-dev package

And didyou end up installing ffmpeg as well?

---

### Post by Warren Watts on 2007-07-13
Don't let your failure discourage you though......

Sometimes compiling from source is the only way, and at least you got your feet wet.  

It's kinda fun being able to stick your fingers in and fiddle with things, isn't it?  

All hail Open Source Software, GNU in general, and the millions of hours dedicated folks around the world have put in to make Ubuntu and Linux what it is today!

---

### Post by slayer666metallica on 2007-07-13
aye to that!

---

### Post by Ek0nomik on 2007-07-13
> **slayer666metallica said:**
> aye to that!

Did you run:

```
sudo apt-get build-dep vlc
```

This will probably get near all the dependencies you need.

---

### Post by slayer666metallica on 2007-07-13
> **Ek0nomik said:**
> Did you run:

```
sudo apt-get build-dep vlc
```

This will probably get near all the dependencies you need.



lol; nope; I actuallly didn't! But; I want to thank you for the helpful code;


p.s. even though that specific code is only for building vlc dep.'s; would it be applicable to future programs if I just switched its name out with the 'vlc' part in the code?

thanks;

---

### Post by metallicamaster3 on 2007-07-13
AFAIK, vlc is the command for just dependancies no?

---

### Post by slayer666metallica on 2007-07-13
> **metallicamaster3 said:**
> AFAIK, vlc is the command for just dependancies no?
yeah; that code Ek0nomik has itself is just for dependencies...

---

### Post by Ek0nomik on 2007-07-13
> **slayer666metallica said:**
> lol; nope; I actuallly didn't! But; I want to thank you for the helpful code;


p.s. even though that specific code is only for building vlc dep.'s; would it be applicable to future programs if I just switched its name out with the 'vlc' part in the code?

thanks;

Yes.  For an example, you could run that command, and replace 'vlc' with 'mozilla-thunderbird' or something, and it will get the dependencies for the version of the software you specified that is in the repository.

The command is, as far as I am concerned, nearly useless.  If the program is in the repository, most people just download it from there.  But, in your case it could actually prove to be useful.  Maybe you wanted a lot of dependencies to compile VLC because a new "awesome" version came out, and there is only an older version in the Ubuntu repository.  It could potentially save you time in this situation, but I don't see it helping in many.

By any chance did you check the README file for a list of all the dependencies you would need?  I would think a widely used piece of software such as VLC would have good documentation for it.

---

### Post by slayer666metallica on 2007-07-13
> **Ek0nomik said:**
> Yes.  For an example, you could run that command, and replace 'vlc' with 'mozilla-thunderbird' or something, and it will get the dependencies for the version of the software you specified that is in the repository.

The command is, as far as I am concerned, nearly useless.  If the program is in the repository, most people just download it from there.  But, in your case it could actually prove to be useful.  Maybe you wanted a lot of dependencies to compile VLC because a new "awesome" version came out, and there is only an older version in the Ubuntu repository.  It could potentially save you time in this situation, but I don't see it helping in many.

By any chance did you check the README file for a list of all the dependencies you would need?  I would think a widely used piece of software such as VLC would have good documentation for it.
Well; I looked in the readme and install files; but it doesn't really talk about dependencies;...

..but it's not to worry about now; I just said "forget it" and decided to install vlc through the soft. repositories....

..so it's all good now;) 

thanks for all the advice though guys; it did at least let me learn a few more things about this great OS.

---

