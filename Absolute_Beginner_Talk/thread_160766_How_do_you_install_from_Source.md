---
title: "How do you install from Source?"
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by Dusk2k2 on 2006-04-15
I want to install the latest version of Banshee music player.  I try to follow the directions, but I don't know how to get to the source directory from the terminal. 

How exactly do I go about installing from source?  

[http://banshee-project.org/Distributions/Ubuntu](http://banshee-project.org/Distributions/Ubuntu)

Above is the banshee website w/ the directions on how to install from source.  

It says I have to install the build depends w/ this command
sudo apt-get build-dep banshee

Whenever I do that, I get an error message that says I must put URI "sources" in the sources.list

Anyway, could anyone help walk me through this install?

---

### Post by John.Michael.Kane on 2006-04-15
[http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html)

---

### Post by taurus on 2006-04-15
Okay, I am assuming you download banshee-0.10.9.tar.gz.  Open a terminal (Applications -> Accessories -> Terminal) and type
```

cd ~/Desktop <-- assuming you've saved it to your Desktop directory!!!
tar xvzf banshee-0.10.9.tar.gz
cd banshee-0.10.9
sudo apt-get install build-essential checkinstall
./configure
make 
sudo make install
-or
sudo make checkinstall

```

---

### Post by John.Michael.Kane on 2006-04-15
The link i posted told the samething

---

### Post by taurus on 2006-04-15
[QUOTE=SD-Plissken]The link i posted told the samething[/QUOTE]
Yes, it did but I didn't see your post when I tried to reply to it...  ;)

---

### Post by Dusk2k2 on 2006-04-15
When I get to make, it says no make file found.  What do I do?

---

### Post by John.Michael.Kane on 2006-04-15
Have you read over this [http://banshee-project.org/Banshee_Source](http://banshee-project.org/Banshee_Source)

---

### Post by Dusk2k2 on 2006-04-15
I did do that.  All the dependencies are installed.  However, when I get to the part where I have to make and make install, it says no make file found.  Any help?

---

### Post by kh4nh on 2006-04-15
I am guessing the reason there is no make file because ./configure process did not get through.

Can you post the messege after you do ./configure

---

### Post by aysiu on 2006-04-15
Can you wait a month and a half for the latest version? Dapper has the latest version in the repositories.

If you're really a cutting edge person, you may want to consider just plain old using Dapper now...

---

### Post by Dusk2k2 on 2006-04-15
Below is what is says after I do ./configure




dusk2k2@KevinLaptop:~/Desktop/banshee-0.10.9$ ./configure
checking build system type... i686-pc-linux
checking host system type... i686-pc-linux
checking target system type... i686-pc-linux
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for intltool >= 0.21... 0.34.1 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... msgfmt
checking for msgmerge... msgmerge
checking for xgettext... xgettext
checking for a BSD-compatible install... /usr/bin/install -c
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
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
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking whether we are using the GNU C++ compiler... (cached) yes
checking whether g++ accepts -g... (cached) yes
checking dependency style of g++... (cached) gcc3
checking for ANSI C header files... (cached) yes
checking what warning flags to pass to the C compiler... -Wall -Wmissing-prototypes
checking what language compliance flags to pass to the C compiler...
checking for pkg-config... /usr/bin/pkg-config
checking for GLIB - version >= 2.0.0... yes (version 2.8.3)
checking pkg-config is at least version 0.9.0... yes
checking for HELIX_REMOTE... configure: error: Package requirements (helix-dbus-server >= 0.2) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the HELIX_REMOTE_CFLAGS and HELIX_REMOTE_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.

---

### Post by kh4nh on 2006-04-15
checking for HELIX_REMOTE... configure: error: Package requirements (helix-dbus-server >= 0.2) were not met.

install helix-dblus-server with synaptic or apt-get and go from there, good luck

---

### Post by Bloch on 2006-04-15
I know nothing about compiling in C, but I have a general IT knowledge and I've written python scripts for text processing.

I have to say that I have almost never successfully compiled anything on linux. Ubuntu does not come supplied with all the required developer files to begin with. You need a lot of background to understand the oputput of the ./configure script, and even where it seems to return YES at every step, make usually does not complete the job.
I am sure that if you have the knowledge you are only one command away from a successful compilation. 
But I think it's fair to warn a beginner that compiling blindly using the default options rarely succeeds - I know there are people who say it always works for them, but I'm sure they have some, even a minimal, knowledge of C.

Go ahead and give it a try, but just remember not to get too frustrated if it doesn't work out. Now if you install something from "Add Applications" and it doesn't work - then get frustrated.
Good Luck

---

