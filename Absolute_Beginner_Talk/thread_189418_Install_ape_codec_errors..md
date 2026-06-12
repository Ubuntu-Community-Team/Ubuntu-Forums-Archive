---
title: "Install ape codec errors."
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by someusernoob on 2006-06-05
I download Monkey's Audio codec (mac-port 3.99 update 4 build 5 released) here ([http://sourceforge.net/projects/mac-port](http://sourceforge.net/projects/mac-port))

I followed the instructions in the install file, but im getting some errors and i really do not have any idea what i am doing nor how to solve it.

This is what the output in the terminal says:

```
owner@PC1:~$ 1/configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
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
checking whether make sets $(MAKE)... (cached) yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for ANSI C header files... (cached) yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking for memory.h... (cached) yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for unistd.h... (cached) yes
checking for an ANSI C-conforming const... yes
checking for size_t... yes
checking for inline... inline
checking for working memcmp... yes
checking whether lstat dereferences a symlink specified with a trailing slash... yes
checking whether stat accepts an empty string... no
checking whether byte ordering is bigendian... no
checking for wcscasecmp... yes
checking for nanosleep... yes
checking for assembly enabled... yes
checking for yasm... /usr/bin/yasm
checking for some Win32 platform... no
"enable_assembly = yes"
checking for int *... yes
checking size of int *... 4
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating src/Console/Makefile
config.status: creating src/Shared/Makefile
config.status: creating src/MACLib/Makefile
config.status: creating src/MACLib/Assembly/Makefile
config.status: creating src/Examples/Makefile
config.status: creating src/Examples/Analyze/Makefile
config.status: creating src/Examples/Analyze/Sample1/Makefile
config.status: creating src/Shared/config.h
config.status: src/Shared/config.h is unchanged
config.status: executing depfiles commands

Build options:
  mac                 3.99-u4-b5
  archtecture              X86
  Win                      no
  enable-assembly          yes


  Yasm                     /usr/bin/yasm
  YASM_ARCH                -m x86
  YASM_FORMAT              -f elf



```

That seems OK to me I guess, problems are starting here:

```

owner@PC1:~$ make
Making all in src
make[1]: Entering directory `/home/owner/src'
Making all in Shared
make[2]: Entering directory `/home/owner/src/Shared'
make  all-am
make[3]: Entering directory `/home/owner/src/Shared'
make[3]: Leaving directory `/home/owner/src/Shared'
make[2]: Leaving directory `/home/owner/src/Shared'
Making all in MACLib
make[2]: Entering directory `/home/owner/src/MACLib'
Making all in Assembly
make[3]: Entering directory `/home/owner/src/MACLib/Assembly'
if /bin/sh ../../../libtool --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I../../../1/src/MACLib/Assembly -I../../../src/Shared     -O3 -Wall -pedantic -Wno-long-long -MT common.lo -MD -MP -MF ".deps/common.Tpo" -c -o common.lo ../../../1/src/MACLib/Assembly/common.cpp; \
        then mv -f ".deps/common.Tpo" ".deps/common.Plo"; else rm -f ".deps/common.Tpo"; exit 1; fi
 g++ -DHAVE_CONFIG_H -I. -I../../../1/src/MACLib/Assembly -I../../../src/Shared -O3 -Wall -pedantic -Wno-long-long -MT common.lo -MD -MP -MF .deps/common.Tpo -c ../../../1/src/MACLib/Assembly/common.cpp  -fPIC -DPIC -o .libs/common.o
../../../1/src/MACLib/Assembly/common.cpp:1:17: error: All.h: No such file or directory
../../../1/src/MACLib/Assembly/common.cpp: In function 'void Adapt_c(short int*, const short int*, int, int)':
../../../1/src/MACLib/Assembly/common.cpp:47: error: expected `)' before ';' token
../../../1/src/MACLib/Assembly/common.cpp:47: error: expected primary-expression before ')' token
../../../1/src/MACLib/Assembly/common.cpp:47: error: expected `;' before ')' token
../../../1/src/MACLib/Assembly/common.cpp:54: error: expected `)' before ';' token
../../../1/src/MACLib/Assembly/common.cpp:54: error: expected primary-expression before ')' token
../../../1/src/MACLib/Assembly/common.cpp:54: error: expected `;' before ')' token
../../../1/src/MACLib/Assembly/common.cpp: In function 'int CalculateDotProduct_c(const short int*, const short int*, int)':
../../../1/src/MACLib/Assembly/common.cpp:66: error: expected `)' before ';' token
../../../1/src/MACLib/Assembly/common.cpp:66: error: expected primary-expression before ')' token
../../../1/src/MACLib/Assembly/common.cpp:66: error: expected `;' before ')' token
make[3]: *** [common.lo] Error 1
make[3]: Leaving directory `/home/owner/src/MACLib/Assembly'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/owner/src/MACLib'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/owner/src'
make: *** [all-recursive] Error 1


```

and this is where i'm lost. 

The install file says this:

```

Requirement
-------------------

YASM - for compiling the asm source (Currently only needed in x86 and AMD64 platforms), 
       if you don't have it, the corresponding C++ code will be used and ASM codes will not build 
       even the assembly option is enabled.


-------------------
Compile
-------------------
$ ./configure
$ make

--enable-assembly to compile with ASM support (The default is yes)

-------------------
Install
-------------------
$ make install 
(need to be root)


then the lib will be installed to the default usr lib of your system (/usr/lib) 
named libmac.so*, the console frontend (now it is statically linked) to /usr/bin named 
mac, and some header files to /usr/include/mac.

There is also a sample analyzing program, located in src/Examples/Analyzer/Sample1,
which displays some information of the specified file. It is not installed.

Enjoy It!

```

And I did install YASM.

Can someone help me out, this all is really alientalk to me right now.

---

### Post by Nikusan on 2006-06-05
You need to be root (administrator). Try sudo make install instead of make install.

---

### Post by someusernoob on 2006-06-05
I logged in as root, and did the ./configure thing, but it still goes wrong when i do "make".

```

root@PC1:~# make
Making all in src
make[1]: Entering directory `/root/src'
Making all in Shared
make[2]: Entering directory `/root/src/Shared'
make  all-am
make[3]: Entering directory `/root/src/Shared'
if /bin/sh ../../libtool --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I../../1/src/Shared -I.     -O3 -Wall -pedantic -Wno-long-long -MT GlobalFunctions.lo -MD -MP -MF ".deps/GlobalFunctions.Tpo" -c -o GlobalFunctions.lo ../../1/src/Shared/GlobalFunctions.cpp; \
        then mv -f ".deps/GlobalFunctions.Tpo" ".deps/GlobalFunctions.Plo"; else rm -f ".deps/GlobalFunctions.Tpo"; exit 1; fi
mkdir .libs
 g++ -DHAVE_CONFIG_H -I. -I../../1/src/Shared -I. -O3 -Wall -pedantic -Wno-long-long -MT GlobalFunctions.lo -MD -MP -MF .deps/GlobalFunctions.Tpo -c ../../1/src/Shared/GlobalFunctions.cpp  -fPIC -DPIC -o .libs/GlobalFunctions.o
 g++ -DHAVE_CONFIG_H -I. -I../../1/src/Shared -I. -O3 -Wall -pedantic -Wno-long-long -MT GlobalFunctions.lo -MD -MP -MF .deps/GlobalFunctions.Tpo -c ../../1/src/Shared/GlobalFunctions.cpp -o GlobalFunctions.o >/dev/null 2>&1
if /bin/sh ../../libtool --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I../../1/src/Shared -I.     -O3 -Wall -pedantic -Wno-long-long -MT StdLibFileIO.lo -MD -MP -MF ".deps/StdLibFileIO.Tpo" -c -o StdLibFileIO.lo ../../1/src/Shared/StdLibFileIO.cpp; \
        then mv -f ".deps/StdLibFileIO.Tpo" ".deps/StdLibFileIO.Plo"; else rm -f ".deps/StdLibFileIO.Tpo"; exit 1; fi
 g++ -DHAVE_CONFIG_H -I. -I../../1/src/Shared -I. -O3 -Wall -pedantic -Wno-long-long -MT StdLibFileIO.lo -MD -MP -MF .deps/StdLibFileIO.Tpo -c ../../1/src/Shared/StdLibFileIO.cpp  -fPIC -DPIC -o .libs/StdLibFileIO.o
 g++ -DHAVE_CONFIG_H -I. -I../../1/src/Shared -I. -O3 -Wall -pedantic -Wno-long-long -MT StdLibFileIO.lo -MD -MP -MF .deps/StdLibFileIO.Tpo -c ../../1/src/Shared/StdLibFileIO.cpp -o StdLibFileIO.o >/dev/null 2>&1
if /bin/sh ../../libtool --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I../../1/src/Shared -I.     -O3 -Wall -pedantic -Wno-long-long -MT CharacterHelper.lo -MD -MP -MF ".deps/CharacterHelper.Tpo" -c -o CharacterHelper.lo ../../1/src/Shared/CharacterHelper.cpp; \
        then mv -f ".deps/CharacterHelper.Tpo" ".deps/CharacterHelper.Plo"; else rm -f ".deps/CharacterHelper.Tpo"; exit 1; fi
 g++ -DHAVE_CONFIG_H -I. -I../../1/src/Shared -I. -O3 -Wall -pedantic -Wno-long-long -MT CharacterHelper.lo -MD -MP -MF .deps/CharacterHelper.Tpo -c ../../1/src/Shared/CharacterHelper.cpp  -fPIC -DPIC -o .libs/CharacterHelper.o
 g++ -DHAVE_CONFIG_H -I. -I../../1/src/Shared -I. -O3 -Wall -pedantic -Wno-long-long -MT CharacterHelper.lo -MD -MP -MF .deps/CharacterHelper.Tpo -c ../../1/src/Shared/CharacterHelper.cpp -o CharacterHelper.o >/dev/null 2>&1
if /bin/sh ../../libtool --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I../../1/src/Shared -I.     -O3 -Wall -pedantic -Wno-long-long -MT CircleBuffer.lo -MD -MP -MF ".deps/CircleBuffer.Tpo" -c -o CircleBuffer.lo ../../1/src/Shared/CircleBuffer.cpp; \
        then mv -f ".deps/CircleBuffer.Tpo" ".deps/CircleBuffer.Plo"; else rm -f ".deps/CircleBuffer.Tpo"; exit 1; fi
 g++ -DHAVE_CONFIG_H -I. -I../../1/src/Shared -I. -O3 -Wall -pedantic -Wno-long-long -MT CircleBuffer.lo -MD -MP -MF .deps/CircleBuffer.Tpo -c ../../1/src/Shared/CircleBuffer.cpp  -fPIC -DPIC -o .libs/CircleBuffer.o
 g++ -DHAVE_CONFIG_H -I. -I../../1/src/Shared -I. -O3 -Wall -pedantic -Wno-long-long -MT CircleBuffer.lo -MD -MP -MF .deps/CircleBuffer.Tpo -c ../../1/src/Shared/CircleBuffer.cpp -o CircleBuffer.o >/dev/null 2>&1
if /bin/sh ../../libtool --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I../../1/src/Shared -I.     -O3 -Wall -pedantic -Wno-long-long -MT MACUtils.lo -MD -MP -MF ".deps/MACUtils.Tpo" -c -o MACUtils.lo ../../1/src/Shared/MACUtils.cpp; \
        then mv -f ".deps/MACUtils.Tpo" ".deps/MACUtils.Plo"; else rm -f ".deps/MACUtils.Tpo"; exit 1; fi
 g++ -DHAVE_CONFIG_H -I. -I../../1/src/Shared -I. -O3 -Wall -pedantic -Wno-long-long -MT MACUtils.lo -MD -MP -MF .deps/MACUtils.Tpo -c ../../1/src/Shared/MACUtils.cpp  -fPIC -DPIC -o .libs/MACUtils.o
 g++ -DHAVE_CONFIG_H -I. -I../../1/src/Shared -I. -O3 -Wall -pedantic -Wno-long-long -MT MACUtils.lo -MD -MP -MF .deps/MACUtils.Tpo -c ../../1/src/Shared/MACUtils.cpp -o MACUtils.o >/dev/null 2>&1
/bin/sh ../../libtool --tag=CXX --mode=link g++  -O3 -Wall -pedantic -Wno-long-long   -o libmacshared.la   GlobalFunctions.lo StdLibFileIO.lo CharacterHelper.lo CircleBuffer.lo MACUtils.lo
ar cru .libs/libmacshared.a .libs/GlobalFunctions.o .libs/StdLibFileIO.o .libs/CharacterHelper.o .libs/CircleBuffer.o .libs/MACUtils.o
ranlib .libs/libmacshared.a
creating libmacshared.la
(cd .libs && rm -f libmacshared.la && ln -s ../libmacshared.la libmacshared.la)
make[3]: Leaving directory `/root/src/Shared'
make[2]: Leaving directory `/root/src/Shared'
Making all in MACLib
make[2]: Entering directory `/root/src/MACLib'
Making all in Assembly
make[3]: Entering directory `/root/src/MACLib/Assembly'
if /bin/sh ../../../libtool --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I../../../1/src/MACLib/Assembly -I../../../src/Shared     -O3 -Wall -pedantic -Wno-long-long -MT common.lo -MD -MP -MF ".deps/common.Tpo" -c -o common.lo ../../../1/src/MACLib/Assembly/common.cpp; \
        then mv -f ".deps/common.Tpo" ".deps/common.Plo"; else rm -f ".deps/common.Tpo"; exit 1; fi
mkdir .libs
 g++ -DHAVE_CONFIG_H -I. -I../../../1/src/MACLib/Assembly -I../../../src/Shared -O3 -Wall -pedantic -Wno-long-long -MT common.lo -MD -MP -MF .deps/common.Tpo -c ../../../1/src/MACLib/Assembly/common.cpp  -fPIC -DPIC -o .libs/common.o
../../../1/src/MACLib/Assembly/common.cpp:1:17: error: All.h: No such file or directory
../../../1/src/MACLib/Assembly/common.cpp: In function 'void Adapt_c(short int*, const short int*, int, int)':
../../../1/src/MACLib/Assembly/common.cpp:47: error: expected `)' before ';' token
../../../1/src/MACLib/Assembly/common.cpp:47: error: expected primary-expression before ')' token
../../../1/src/MACLib/Assembly/common.cpp:47: error: expected `;' before ')' token
../../../1/src/MACLib/Assembly/common.cpp:54: error: expected `)' before ';' token
../../../1/src/MACLib/Assembly/common.cpp:54: error: expected primary-expression before ')' token
../../../1/src/MACLib/Assembly/common.cpp:54: error: expected `;' before ')' token
../../../1/src/MACLib/Assembly/common.cpp: In function 'int CalculateDotProduct_c(const short int*, const short int*, int)':
../../../1/src/MACLib/Assembly/common.cpp:66: error: expected `)' before ';' token
../../../1/src/MACLib/Assembly/common.cpp:66: error: expected primary-expression before ')' token
../../../1/src/MACLib/Assembly/common.cpp:66: error: expected `;' before ')' token
make[3]: *** [common.lo] Error 1
make[3]: Leaving directory `/root/src/MACLib/Assembly'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/root/src/MACLib'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/root/src'
make: *** [all-recursive] Error 1
root@PC1:~#

```

(PS, the first time i copy/pasted the wrong piece of my terminal output in my post, make install instead of make, so it allready goes wrong at make, and the file doesnt say you should be root there.)

---

### Post by richbarna on 2006-06-05
Have you got "build-essential" ?
If not, :-
> sudo apt-get update
> sudo apt-get install build-essential

This usually gives you all you need for ./configure , make, sudo make install.

---

### Post by someusernoob on 2006-06-05
Yes, i allready have that.

```

owner@PC1:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by richbarna on 2006-06-05
Ok, back to basics.
What system are you on ?
And, why the Monkey Audio codec ?
Maybe there is something else you could use to get the same results ?

---

### Post by someusernoob on 2006-06-05
- Dapper 6.06

- Because i have loads of .ape files, and actually i want to play them, but thats gonna be hard i noticed, so then the next step would be to convert them. but every thing i find is about these codecs, so i thought, give it a try and install them.

And for playing I rather dont use xmms or beep coz they are ugly. I found Quod Libet, it can play my .mp3's my .flac's and my .wv's.

---

### Post by someusernoob on 2006-06-05
Well, nevermind after all i guess. I found a codec on this site: [http://morgoth.free.fr/ubports/](http://morgoth.free.fr/ubports/) 

And just a minute ago converted an .ape file back to .wav.

Again one step further away from Windows =D>

---

