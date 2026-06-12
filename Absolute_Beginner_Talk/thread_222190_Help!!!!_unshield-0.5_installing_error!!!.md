---
title: "Help!!!! unshield-0.5 installing error!!!"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by cc500 on 2006-07-24
I was trying to install unshield-0.5 using /.configure which worked fine, but then I tried to make it and it gave me some errors and was wondering if anyone else has experienced problems like this. Here's the log:

chris@chris-desktop:~/Desktop/unshield-0.5$ sudo make
Password:
Making all in lib
make[1]: Entering directory `/home/chris/Desktop/unshield-0.5/lib'
make all-recursive
make[2]: Entering directory `/home/chris/Desktop/unshield-0.5/lib'
Making all in md5
make[3]: Entering directory `/home/chris/Desktop/unshield-0.5/lib/md5'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/chris/Desktop/unshield-0.5/lib/md5'
Making all in .
make[3]: Entering directory `/home/chris/Desktop/unshield-0.5/lib'
if /bin/sh ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I. -g -ansi -Wall -Wsign-compare -Wno-long-long -Werror -g -O2 -I.. -g -O2 -MT file.lo -MD -MP -MF ".deps/file.Tpo" \
-c -o file.lo `test -f 'file.c' || echo './'`file.c; \
then mv -f ".deps/file.Tpo" ".deps/file.Plo"; \
else rm -f ".deps/file.Tpo"; exit 1; \
fi
gcc -DHAVE_CONFIG_H -I. -I. -I. -g -ansi -Wall -Wsign-compare -Wno-long-long -Werror -g -O2 -I.. -g -O2 -MT file.lo -MD -MP -MF .deps/file.Tpo -c file.c -fPIC -DPIC -o .libs/file.o
file.c:11:18: error: zlib.h: No such file or directory
file.c:209: error: syntax error before '*' token
file.c: In function 'unshield_uncompress':
file.c:211: error: 'z_stream' undeclared (first use in this function)
file.c:211: error: (Each undeclared identifier is reported only once
file.c:211: error: for each function it appears in.)
file.c:211: error: syntax error before 'stream'
file.c:214: error: 'stream' undeclared (first use in this function)
file.c:214: error: 'source' undeclared (first use in this function)
file.c:215: error: 'uInt' undeclared (first use in this function)
file.c:215: error: syntax error before 'sourceLen'
file.c:217: error: 'dest' undeclared (first use in this function)
file.c:218: error: 'destLen' undeclared (first use in this function)
file.c:220: error: 'alloc_func' undeclared (first use in this function)
file.c:220: error: syntax error before numeric constant
file.c:221: error: 'free_func' undeclared (first use in this function)
file.c:221: error: syntax error before numeric constant
cc1: warnings being treated as errors
file.c:224: warning: implicit declaration of function 'inflateInit2'
file.c:224: error: 'MAX_WBITS' undeclared (first use in this function)
file.c:225: error: 'Z_OK' undeclared (first use in this function)
file.c:227: warning: implicit declaration of function 'inflate'
file.c:227: error: 'Z_FINISH' undeclared (first use in this function)
file.c:228: error: 'Z_STREAM_END' undeclared (first use in this function)
file.c:229: warning: implicit declaration of function 'inflateEnd'
file.c: In function 'unshield_file_save':
file.c:565: error: 'uLong' undeclared (first use in this function)
file.c:565: error: syntax error before 'total_written'
file.c:625: error: syntax error before 'bytes_to_write'
file.c:653: error: 'bytes_to_write' undeclared (first use in this function)
file.c:655: error: 'Z_OK' undeclared (first use in this function)
file.c:692: error: 'total_written' undeclared (first use in this function)
make[3]: *** [file.lo] Error 1
make[3]: Leaving directory `/home/chris/Desktop/unshield-0.5/lib'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/chris/Desktop/unshield-0.5/lib'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/chris/Desktop/unshield-0.5/lib'
make: *** [all-recursive] Error

---

### Post by Jagot on 2006-07-24
Never tried to install it myself, but just thought I'd add that are you aware it's in the repositories?

[http://packages.ubuntu.com/dapper/utils/unshield](http://packages.ubuntu.com/dapper/utils/unshield)

Enable the universe repo then:

```
sudo aptitude update && sudo aptitude install unshield
```

---

### Post by cc500 on 2006-07-24
I actually didn't realize that it was repository. Other thing, I can't update because I don't have my wireless working(using unshield to use windows drivers for my viewsonic 802.11g pci card).

---

### Post by punx45 on 2006-07-24
i was working on this yesterday, and if i recall correctly unshield needs zlib to install correctly.   i am at work at the moment so i cant get specific.   basically find and install zlib,(will try to provide link later if i can) then in the unshield directory 
```
./configure --with-zlib=*path/to/zlib.h*
```(not 100% certain of the exactness of the command line, but zlib has instructions somwhere..)   then just make and install unshield as usual.

may or may not help.

---

### Post by punx45 on 2006-07-24
also, try using unzip to unpack the .exe driver first, because that worked for me, but only after i spent an hour getting unshield to work ](*,)

---

### Post by cc500 on 2006-07-24
Thanks, that's what looks like is wrong when I run the ./configure command. A link to someplace where I can get zlib would be great.

Thanks again for all your help,
cc

---

### Post by cc500 on 2006-07-24
I'm sorry, I don't quite understand your last comment, unzipping an .exe file doesn't make sense to me. :confused: Please correct my thinking on this. Or correct what I'm thinking you said.

---

### Post by cc500 on 2006-07-24
I installed zlib and ran the ./configure again and this time it looks like it worked! 
chris@chris-desktop:~/Desktop/unshield-0.5$ ./configure --with-zlib=/path/to/zlib.h
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gawk... (cached) mawk
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
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
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
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
appending configuration tag "F77" to libtool
checking whether make sets $(MAKE)... (cached) yes
checking for ld used by GCC... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking for shared library run path origin... done
checking for an ANSI C-conforming const... yes
checking whether byte ordering is bigendian... no
checking for inttypes.h... (cached) yes
checking for stdint.h... (cached) yes
checking stdbool.h usability... yes
checking stdbool.h presence... yes
checking for stdbool.h... yes
checking for printf format string that works with size_t values... zi
checking if zlib is wanted... yes
checking for inflateEnd in -lz... yes
checking zlib.h usability... yes
checking zlib.h presence... yes
checking for zlib.h... yes
checking for inflateEnd in -lz... (cached) yes
checking zlib in /path/to/zlib.h... ok
configure: creating ./config.status
config.status: creating Makefile
config.status: creating lib/md5/Makefile
config.status: creating lib/Makefile
config.status: creating src/Makefile
config.status: creating lib/unshield_config.h
config.status: lib/unshield_config.h is unchanged
config.status: executing depfiles commands

Until I tried to install it again:

chris@chris-desktop:~/Desktop/unshield-0.5$ sudo make install Password:
Making install in lib
make[1]: Entering directory `/home/chris/Desktop/unshield-0.5/lib'
Making install in md5
make[2]: Entering directory `/home/chris/Desktop/unshield-0.5/lib/md5'
make[3]: Entering directory `/home/chris/Desktop/unshield-0.5/lib/md5'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/chris/Desktop/unshield-0.5/lib/md5'
make[2]: Leaving directory `/home/chris/Desktop/unshield-0.5/lib/md5'
Making install in .
make[2]: Entering directory `/home/chris/Desktop/unshield-0.5/lib'
/bin/sh ../libtool --mode=link gcc -g -ansi -Wall -Wsign-compare -Wno-long-long -Werror -g -O2  -I.. -g -O2  -L/path/to/zlib.h/lib -o libunshield.la -rpath /usr/local/lib -no-undefined -version-info 0:0:0 bswap.lo component.lo directory.lo file.lo file_group.lo helper.lo libunshield.lo log.lo md5/libmd5.la -lz
gcc -shared  .libs/bswap.o .libs/component.o .libs/directory.o .libs/file.o .libs/file_group.o .libs/helper.o .libs/libunshield.o .libs/log.o -Wl,--whole-archive md5/.libs/libmd5.a -Wl,--no-whole-archive  -L/path/to/zlib.h/lib -lz  -Wl,-soname -Wl,libunshield.so.0 -o .libs/libunshield.so.0.0.0
/usr/bin/ld: /usr/local/lib/libz.a(inflate.o): relocation R_X86_64_32S against `zcalloc' can not be used when making a shared object; recompile with -fPIC
/usr/local/lib/libz.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[2]: *** [libunshield.la] Error 1
make[2]: Leaving directory `/home/chris/Desktop/unshield-0.5/lib'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/chris/Desktop/unshield-0.5/lib'
make: *** [install-recursive] Error 1

---

### Post by cc500 on 2006-07-25
Bump

---

### Post by punx45 on 2006-07-25
sorry the *path/to/zlib* was in italics to indicate that it was not literal.   there you want to put the path to the actual zlib.h file wherever it was installed to.   find the search for file feature that is in the accessories or administration tab (cant remember which, not at the dapper computer) use that to search for zlib.h and insert that complete path where */path/to/zlib.h* was.

---

### Post by cc500 on 2006-07-26
I'm having some trouble finding it..... Could you tell me around where yours was located?

---

### Post by punx45 on 2006-07-26
if i get around to booting up ubuntu tonight ill find it and post.

also will attempt to get terminal server functioning so i can ssh in from work.

---

### Post by cc500 on 2006-07-26
Thanks you so much..........

---

### Post by cc500 on 2006-07-28
I got unshield installed after changing dist to knoppix 5.0, but I still can't figure out how to use it. :???:

---

### Post by punx45 on 2006-07-29
try reading the documentation that came in the unshiled package which should end in tar.gz if you downloaded it yourself.   there should be a README or similar such file that will give basic instructions, otherwise check the unshield website for documentation.   i dont think i could explain it without referring to documentation myself, so try that or see if someone else comes to answer.

---

