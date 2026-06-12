---
title: "'make' Problem"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by jideuu on 2007-11-10
When I try to compile something using 'make' I get this:
```
make: *** No targets specified and no makefile found. Stop.
```

'./configure' returns:
```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
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
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... no
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... msgfmt
checking for msgmerge... msgmerge
checking for xgettext... xgettext
checking for uuid_generate in -luuid... no
configure: error: *** uuid library (libuuid) not found
```

Does anyone know whats wrong?

---

### Post by matthewcraig on 2007-11-10
I would not recommend trying to compile programs to an "Absolute Beginner".  Ubuntu seems to be a Linux distribution that allows you to use your computer without requiring you to know how to compile programs.  Other distros give you more control over that funcitonality, and they lend themselves to making such things easier for a new user.

---

### Post by FuturePilot on 2007-11-10
You probably need to install the build-essential package.
```
sudo apt-get install build-essential
```
But what are you trying to compile? It could already be in the repos.

---

### Post by jideuu on 2007-11-10
I'm trying to compile/install Avant Window Navigator (the ./configure output is from gparted, but i got it from the repos.). I already have build-essentials also.

@matthewcraig: I'm not exactly a master but it'd be nice to figure this out now to avoid problems in the future, should I ever need it. ;)

---

### Post by matthewcraig on 2007-11-10
I hope you get my meaning: You're using the wrong distro if you plan on compiling your own code.

---

### Post by jideuu on 2007-11-10
I could spend all day debating whether or not I need to compile anything. I'd like to have the option. I used it a lot in feisty, I'd just like to get it working here.

---

### Post by matthewcraig on 2007-11-10
Sounds like you have had some experience here.  Sorry for my misunderstanding, in that I thought you were an Absolute Beginner.

---

### Post by Paul820 on 2007-11-10
> **matthewcraig said:**
> I hope you get my meaning: You're using the wrong distro if you plan on compiling your own code.
Why do you say that? I compile code all the time as the repos do not always have the latest version of the packages. I actually enjoy compiling code, it's a challenge sometimes.

---

### Post by matthewcraig on 2007-11-10
Paul820: You are not a beginner by any stretch of the word.  Compile away.

---

### Post by dfreer on 2007-11-10
Just looking at the bottom of your ./configure output:
> checking for uuid_generate in -luuid... no
configure: error: *** uuid library (libuuid) not found

Try this:
```
sudo apt-get install libuuid1 uuid-dev
```

And the whole "Ubuntu is a beginner's distro, and so it's harder to compile programs on" idea is just insulting :(
What distro would you recommend using that it is easier to compile on?

---

### Post by jideuu on 2007-11-10
> And the whole "Ubuntu is a beginner's distro, and so it's harder to compile programs on" idea is just insulting
Yeah! As an advanced Windows user, I've had a very hard time getting Ubuntu to work! :P
Nah, since I started using Ubuntu last month it's been great, the community especially. You guys are really patient! :)

Anyway, I tried "sudo apt-get install libuuid1 uuid-dev" and got this:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libuuidl

```

---

### Post by Paul820 on 2007-11-10
> **jideuu said:**
> Yeah! As an advanced Windows user, I've had a very hard time getting Ubuntu to work! :P
Nah, since I started using Ubuntu last month it's been great, the community especially. You guys are really patient! :)

Anyway, I tried "sudo apt-get install libuuid1 uuid-dev" and got this:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libuuidl

```

It's not lubuuidl it's libuuid1, a one on the end not an 'ell'

---

### Post by matthewcraig on 2007-11-10
Never said it was a beginner's distro, but this is a beginner's forum...  I hope you were not insulted I assumed people were beginners who posted in "Absolute Beginner Talk".

Gee!

---

### Post by dfreer on 2007-11-10
> **matthewcraig said:**
> Never said it was a beginner's distro, but this is a beginner's forum...  I hope you were not insulted I assumed people were beginners who posted in "Absolute Beginner Talk".

Gee!

I understand what you mean here, that you think this thread isn't in the appropriate section. Although I'd like to think of the "Absolute Beginner's Talk" forum shouldn't be limited as to what topics should be discussed, so much as the approach needed in resolving the problem. That's why I gave the OP the exact command to install the package, instead of just saying "Install the libuuid developer's package".

Remember, a user who is compiling code for the first time is a beginner at that :D

However, this is what I was referring to when I made my comment:

> **matthewcraig said:**
> I hope you get my meaning: **You're using the wrong distro** if you plan on compiling your own code.

Just because Ubuntu is geared towards an easier to use UI and install than other distros, does not mean it isn't as full featured like Windows Vista Basic vs. Windows Vista Ultimate. It's largely based off Debian, for crying out loud ;)

---

