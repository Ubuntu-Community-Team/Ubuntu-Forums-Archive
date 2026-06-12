---
title: "Make not working! Help!"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by Ankher on 2007-05-04
Okay, while trying to install various programs involving svn or cvs. Sometimes (especially with svn) while typing stuff into the terminal, I'll get the code to put in, put it in and hit enter. Nothing happens. This really isn't my problem, but help with it would be nice

Usually I'll find one that works for me except for one crucial part: the make part. I'll get to the part where it tells me to type this:```
make
``` so I do and I get this:```
make: *** No targets specified and no makefile found.  Stop.
```

what's wrong? I installed Cinelerra from source a while ago (maybe before I upgraded to Feisty, not sure) and have probably installed other stuff from source, so why won't this (movieconvert, but actually glib) install? Also, why don't I have glib in the first place? I have GIMP, etc.

:confused:

---

### Post by daviescr on 2007-05-04
I think you should include a little more details in your posts. It is kind of hard to help but I would guess there is a typo you don't see. 

Its always easier to see someone else' s mistake.

---

### Post by Ankher on 2007-05-04
Okay, whenever I type anything involving make, I get the error above. I'm trying to compile glib which I should have already (I think?) but w/e. okay. This is what I get when I follow the instructions in the gz file (with my comments)```
robbie@Ubuntu:~$ cd ./Desktop # the file is on my desktop, this isn't in the instructions
robbie@Ubuntu:~/Desktop$ gzip -cd gtk+-2.10.9.tar.gz | tar xvf -
gtk+-2.10.9/gdk/gdkrgb.h # actually there are a ton more of these, but I deleted them  because there's nothing interesting going on at all
gtk+-2.10.9/INSTALL
gtk+-2.10.9/config.guess
gtk+-2.10.9/gtk-doc.make
robbie@Ubuntu:~/Desktop$ cd gtk+-2.10.9
robbie@Ubuntu:~/Desktop/gtk+-2.10.9$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for native Win32... no
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
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for f95... no
checking for fort... no
checking for xlf95... no
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
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
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
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for _LARGE_FILES value needed for large files... no
checking for nm... /usr/bin/nm -B
checking whether to enable maintainer-specific portions of Makefiles... no
checking for some Win32 platform... no
checking whether build environment is sane... yes
checking for library containing strerror... none required
checking for gcc option to accept ANSI C... none needed
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... (cached) yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for BASE_DEPENDENCIES... configure: error: Package requirements (glib-2.0 >= 2.12.0    atk >= 1.9.0    pango >= 1.12.0    cairo >= 1.2.0) were not met:

No package 'glib-2.0' found
No package 'atk' found
No package 'pango' found
No package 'cairo' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BASE_DEPENDENCIES_CFLAGS
and BASE_DEPENDENCIES_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

robbie@Ubuntu:~/Desktop/gtk+-2.10.9$ make
make: *** No targets specified and no makefile found.  Stop.
robbie@Ubuntu:~/Desktop/gtk+-2.10.9$ 

```

So yeah. I read somewhere else here that it won't make a makefile if it returns errors, if this is true, how do I fix these errors?

---

### Post by zvacet on 2007-05-05
Install depencencies wich it was unable to found (glib-2.0 >= 2.12.0    atk >= 1.9.0    pango >= 1.12.0    cairo >= 1.2.0)

---

### Post by Ankher on 2007-05-05
All of those are already installed (I just checked Synaptic)

--EDIT--

never mind. I have gtk installed, am gonna install movieconvert now sorry!

---

### Post by Ankher on 2007-05-05
Never mind. I already have the library installed and mediaconvert is pre-alpha and I can't get the cvs checkout to work anyway :)

---

### Post by ramjet_1953 on 2007-05-05
Do you have [COLOR="Blue"]build-essentials[/COLOR] installed?

Are you running things in the correct sequence? ie

[COLOR="Red"]./configure

make

sudo make install[/COLOR]

Regards,
Roger :cool:

---

### Post by Happy_Man on 2007-05-05
Oh god, I hate compiling stuff for EXACTLY this reason. D'you see at the bottom of the ./configure where it says you don't have such and such files installed? You have to install those before the compiling (eg make) will work. This is why .debs are a gift from the Linux god. Hope this helps!

---

### Post by dpzektor on 2007-05-05
> **Happy_Man said:**
> Oh god, I hate compiling stuff for EXACTLY this reason. D'you see at the bottom of the ./configure where it says you don't have such and such files installed? You have to install those before the compiling (eg make) will work. This is why .debs are a gift from the Linux god. Hope this helps!

Agreed. I am relatively new to the Linux scene, but I am a pretty well versed computer guy. I know how to compile apps from source, but it is EXTREMELY annoying to get errors related to a certain app or lib that is dependant on the source to compile. I went through this today with a  certain app and finally gave up after installing a dependant file, getting a little farther (then error!), installing another, farther and then error again....you get the idea. Deb packages just rock.

---

### Post by Ankher on 2007-05-05
I totally agree! Thanks for the suggestions, the next time I have to compile stuff, I'll do that :)
> **ramjet_1953 said:**
> Do you have [COLOR="Blue"]build-essentials[/COLOR] installed?
umm... no? What is that?

---

### Post by ramjet_1953 on 2007-05-06
If you want to "roll your own", you have to have a build environment, with all of the necessary programs and libraries installed first.

In a terminal, copy and paste the following command:

[COLOR="Red"]sudo apt-get install build-essential[/COLOR]

That is a starting point.

I suggest that you do a bit more reseach on compiling your own binaries from source first and understand the challenges that you can face, especially dependencies.

Regards,
Roger 8)

---

