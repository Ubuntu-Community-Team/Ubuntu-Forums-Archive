---
title: "MAGIC layout installation problem.... pls help"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by ajan on 2008-01-21
i tried installing MAGIC layout tool... it got configured successfully but then the make and make install commands ended up only in errors... pls help me...

i hav pasted the entire installation comments here... anyone plz help...


ajan@ajan:~/Desktop/magic-7.4.54$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking for cpp... cpp
checking for library containing strerror... none required
checking for a BSD-compatible install... /usr/bin/install -c
checking for ranlib... ranlib
checking for gm4... no
checking for gnum4... no
checking for m4... /usr/bin/m4
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
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
checking for void *... yes
checking size of void *... 4
checking for unsigned int... yes
checking size of unsigned int... 4
checking for unsigned long... yes
checking size of unsigned long... 4
checking for unsigned long long... yes
checking size of unsigned long long... 8
checking whether byte ordering is bigendian... no
checking for ANSI C header files... (cached) yes
checking for setenv... yes
checking for putenv... yes
checking for vfork... yes
checking dirent.h usability... yes
checking dirent.h presence... yes
checking for dirent.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking param.h usability... no
checking param.h presence... no
checking for param.h... no
checking paths.h usability... yes
checking paths.h presence... yes
checking for paths.h... yes
checking for va_copy... yes
checking for __va_copy... yes
checking for built-in roundf... yes
checking for built-in round... yes
checking for gcore... /usr/bin/gcore
checking for csh... no
checking for X... libraries /usr/X11R6/lib, headers
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for XOpenDevice in -lXi... yes
checking for tclConfig.sh... /usr/lib/tcl8.4/tclConfig.sh
checking for tkConfig.sh... /usr/lib/tk8.4/tkConfig.sh
checking for wish executable... /usr/bin/wish
checking for tclsh executable... /usr/bin/tclsh
checking GL/gl.h usability... no
checking GL/gl.h presence... no
checking for GL/gl.h... no
GL header files not found, disabling OpenGL
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
configure: creating ./config.status
config.status: creating defs.mak

-----------------------------------------------------------
Configuration Summary (principle requirements):

X11:          yes
OpenGL:       no

  OpenGL graphics are considerably better than the standard 8-bit
  and 24-bit X11 graphics, provided that you have a video card and
  driver supporting accelerated OpenGL graphics.  If you get this
  message, you may need to download OpenGL libraries and header
  files, which are usually available from the video card manufacturer.
  Magic with un-accelerated OpenGL, such as using Mesa GL without
  a supported graphics card, is usually a very bad combination.

Tcl/Tk:       yes
BLT:          yes
-----------------------------------------------------------

Use 'make' to compile and 'make install' to install.

Errors may not be printed to stdout:  see files 'make.log'
  and 'install.log' for complete error summary.

ajan@ajan:~/Desktop/magic-7.4.54$ make
--- errors and warnings logged in file make.log
--- making header file database/database.h

ajan@ajan:~/Desktop/magic-7.4.54$ make install
--- installing executable to /usr/local/bin
--- installing runtime files to /usr/local/lib
rm: cannot remove `windows7.glyphs': Permission denied
cp: cannot create regular file `/usr/local/lib/magic/sys/windows7.glyphs': Permission denied
rm: cannot remove `windows11.glyphs': Permission denied
cp: cannot create regular file `/usr/local/lib/magic/sys/windows11.glyphs': Permission denied
rm: cannot remove `windows14.glyphs': Permission denied
cp: cannot create regular file `/usr/local/lib/magic/sys/windows14.glyphs': Permission denied
rm: cannot remove `windows22.glyphs': Permission denied
cp: cannot create regular file `/usr/local/lib/magic/sys/windows22.glyphs': Permission denied
make[2]: *** [install-tcl] Error 1
cp: cannot create regular file `/usr/local/lib/magic/doc/tut1.ps': Permission denied
make[3]: *** [/usr/local/lib/magic/doc/tut1.ps] Error 1
make[2]: *** [install-tcl] Error 2
cp: cannot create regular file `/usr/local/lib/magic/sys/mos.7bit.dstyle': Permission denied
cp: cannot create regular file `/usr/local/lib/magic/sys/mos.7bit.std.cmap': Permission denied
cp: cannot create regular file `/usr/local/lib/magic/sys/mos.24bit.dstyle': Permission denied
cp: cannot create regular file `/usr/local/lib/magic/sys/mos.24bit.std.cmap': Permission denied
cp: cannot create regular file `/usr/local/lib/magic/sys/mos.7bit.mraster_dstyle': Permission denied
cp: cannot create regular file `/usr/local/lib/magic/sys/mos.7bit.mraster.cmap': Permission denied
cp: cannot create regular file `/usr/local/lib/magic/sys/mos.OpenGL.dstyle': Permission denied
cp: cannot create regular file `/usr/local/lib/magic/sys/mos.OpenGL.std.cmap': Permission denied
cp: cannot create regular file `/usr/local/lib/magic/sys/minimum.tech': Permission denied
cp: cannot create regular file `/usr/local/lib/magic/sys/gdsquery.tech': Permission denied
cp: cannot create regular file `/usr/local/lib/magic/sys/scmos.tech': Permission denied
cp: cannot create regular file `/usr/local/lib/magic/sys/scmos-tm.tech': Permission denied
cp: cannot create regular file `/usr/local/lib/magic/sys/scmos-sub.tech': Permission denied
cp: cannot create regular file `/usr/local/lib/magic/sys/scmosWR.tech': Permission denied
make[2]: *** [install-tcl] Error 1
rm: cannot remove `/usr/local/bin/magic': Permission denied
make[2]: *** [/usr/local/bin/magic.sh] Error 1
make[2]: *** No rule to make target `../cmwind/libcmwind.o', needed by `tclmagic.so'.  Stop.
ext2sim.c:32:31: error: database/database.h: No such file or directory
In file included from ext2sim.c:35:
../dbwind/dbwind.h:26:31: error: database/database.h: No such file or directory
In file included from ext2sim.c:35:
../dbwind/dbwind.h:45: error: syntax error before ‘CellDef’
../dbwind/dbwind.h:45: warning: no semicolon at end of struct or union
../dbwind/dbwind.h:58: error: syntax error before ‘dbw_visibleLayers’
../dbwind/dbwind.h:58: warning: data definition has no type or storage class
../dbwind/dbwind.h:88: error: syntax error before ‘}’ token
../dbwind/dbwind.h:88: warning: data definition has no type or storage class
In file included from ext2sim.c:36:
../commands/commands.h:27:31: error: database/database.h: No such file or directory
In file included from ext2sim.c:36:
../commands/commands.h:47: error: syntax error before ‘CmdYMCell’
../commands/commands.h:47: warning: data definition has no type or storage class
../commands/commands.h:48: error: syntax error before ‘CmdYMLabel’
../commands/commands.h:48: warning: data definition has no type or storage class
../commands/commands.h:49: error: syntax error before ‘CmdYMAllButSpace’
../commands/commands.h:49: warning: data definition has no type or storage class
../commands/commands.h:61: error: syntax error before ‘*’ token
../commands/commands.h:61: warning: data definition has no type or storage class
ext2sim.c: In function ‘CmdExtToSim’:
ext2sim.c:487: error: ‘CellUse’ undeclared (first use in this function)
ext2sim.c:487: error: (Each undeclared identifier is reported only once
ext2sim.c:487: error: for each function it appears in.)
ext2sim.c:487: error: syntax error before ‘)’ token
make[2]: *** [simwrap.o] Error 1
ext2spice.c:33:31: error: database/database.h: No such file or directory
In file included from ext2spice.c:36:
../dbwind/dbwind.h:26:31: error: database/database.h: No such file or directory
In file included from ext2spice.c:36:
../dbwind/dbwind.h:45: error: syntax error before ‘CellDef’
../dbwind/dbwind.h:45: warning: no semicolon at end of struct or union
../dbwind/dbwind.h:58: error: syntax error before ‘dbw_visibleLayers’
../dbwind/dbwind.h:58: warning: data definition has no type or storage class
../dbwind/dbwind.h:88: error: syntax error before ‘}’ token
../dbwind/dbwind.h:88: warning: data definition has no type or storage class
In file included from ext2spice.c:37:
../commands/commands.h:27:31: error: database/database.h: No such file or directory
In file included from ext2spice.c:37:
../commands/commands.h:47: error: syntax error before ‘CmdYMCell’
../commands/commands.h:47: warning: data definition has no type or storage class
../commands/commands.h:48: error: syntax error before ‘CmdYMLabel’
../commands/commands.h:48: warning: data definition has no type or storage class
../commands/commands.h:49: error: syntax error before ‘CmdYMAllButSpace’
../commands/commands.h:49: warning: data definition has no type or storage class
../commands/commands.h:61: error: syntax error before ‘*’ token
../commands/commands.h:61: warning: data definition has no type or storage class
ext2spice.c: In function ‘CmdExtToSpice’:
ext2spice.c:628: error: ‘CellUse’ undeclared (first use in this function)
ext2spice.c:628: error: (Each undeclared identifier is reported only once
ext2spice.c:628: error: for each function it appears in.)
ext2spice.c:628: error: syntax error before ‘)’ token
make[2]: *** [spicewrap.o] Error 1
rm: cannot remove `/usr/local/bin/magic': Permission denied
make[2]: *** [/usr/local/bin/magic.sh] Error 1
make[1]: *** [install-tcl-real] Error 2
make: *** [install-tcl] Error 2

i even tried sudo make install

it resulted in the following errors

ajan@ajan:~/Desktop/magic-7.4.54$ sudo make install
--- installing executable to /usr/local/bin
--- installing runtime files to /usr/local/lib
make[2]: *** No rule to make target `../cmwind/libcmwind.o', needed by `tclmagic.so'.  Stop.
ext2sim.c:32:31: error: database/database.h: No such file or directory
In file included from ext2sim.c:35:
../dbwind/dbwind.h:26:31: error: database/database.h: No such file or directory
In file included from ext2sim.c:35:
../dbwind/dbwind.h:45: error: syntax error before ‘CellDef’
../dbwind/dbwind.h:45: warning: no semicolon at end of struct or union
../dbwind/dbwind.h:58: error: syntax error before ‘dbw_visibleLayers’
../dbwind/dbwind.h:58: warning: data definition has no type or storage class
../dbwind/dbwind.h:88: error: syntax error before ‘}’ token
../dbwind/dbwind.h:88: warning: data definition has no type or storage class
In file included from ext2sim.c:36:
../commands/commands.h:27:31: error: database/database.h: No such file or directory
In file included from ext2sim.c:36:
../commands/commands.h:47: error: syntax error before ‘CmdYMCell’
../commands/commands.h:47: warning: data definition has no type or storage class
../commands/commands.h:48: error: syntax error before ‘CmdYMLabel’
../commands/commands.h:48: warning: data definition has no type or storage class
../commands/commands.h:49: error: syntax error before ‘CmdYMAllButSpace’
../commands/commands.h:49: warning: data definition has no type or storage class
../commands/commands.h:61: error: syntax error before ‘*’ token
../commands/commands.h:61: warning: data definition has no type or storage class
ext2sim.c: In function ‘CmdExtToSim’:
ext2sim.c:487: error: ‘CellUse’ undeclared (first use in this function)
ext2sim.c:487: error: (Each undeclared identifier is reported only once
ext2sim.c:487: error: for each function it appears in.)
ext2sim.c:487: error: syntax error before ‘)’ token
make[2]: *** [simwrap.o] Error 1
ext2spice.c:33:31: error: database/database.h: No such file or directory
In file included from ext2spice.c:36:
../dbwind/dbwind.h:26:31: error: database/database.h: No such file or directory
In file included from ext2spice.c:36:
../dbwind/dbwind.h:45: error: syntax error before ‘CellDef’
../dbwind/dbwind.h:45: warning: no semicolon at end of struct or union
../dbwind/dbwind.h:58: error: syntax error before ‘dbw_visibleLayers’
../dbwind/dbwind.h:58: warning: data definition has no type or storage class
../dbwind/dbwind.h:88: error: syntax error before ‘}’ token
../dbwind/dbwind.h:88: warning: data definition has no type or storage class
In file included from ext2spice.c:37:
../commands/commands.h:27:31: error: database/database.h: No such file or directory
In file included from ext2spice.c:37:
../commands/commands.h:47: error: syntax error before ‘CmdYMCell’
../commands/commands.h:47: warning: data definition has no type or storage class
../commands/commands.h:48: error: syntax error before ‘CmdYMLabel’
../commands/commands.h:48: warning: data definition has no type or storage class
../commands/commands.h:49: error: syntax error before ‘CmdYMAllButSpace’
../commands/commands.h:49: warning: data definition has no type or storage class
../commands/commands.h:61: error: syntax error before ‘*’ token
../commands/commands.h:61: warning: data definition has no type or storage class
ext2spice.c: In function ‘CmdExtToSpice’:
ext2spice.c:628: error: ‘CellUse’ undeclared (first use in this function)
ext2spice.c:628: error: (Each undeclared identifier is reported only once
ext2spice.c:628: error: for each function it appears in.)
ext2spice.c:628: error: syntax error before ‘)’ token
make[2]: *** [spicewrap.o] Error 1

---

### Post by Cypher on 2008-01-21
Take a step back...ONLY do "make install" once you confirmed that the "make" actally worked. In this case, all of the output was sent to the file "make.log", so you want to check on that first..do
```

less make.log

```
and you might see errors in that file, tell us what is and let's see if we can fix that before you try installing the application..

---

### Post by ajan on 2008-01-24
thanks for tat.. i went through the errors in make.log

those errors are

make[1]: Entering directory `/home/ajan/Desktop/magic-7.4.54'
--- making header file database/database.h
./scripts/makedbh database/database.h.in database/database.h
/bin/bash: ./scripts/makedbh: /bin/csh: bad interpreter: No such file or directory
make[1]: *** [database/database.h] Error 126
make[1]: Leaving directory `/home/ajan/Desktop/magic-7.4.54'
make[1]: Entering directory `/home/ajan/Desktop/magic-7.4.54'
--- making header file database/database.h
./scripts/makedbh database/database.h.in database/database.h
/bin/bash: ./scripts/makedbh: /bin/csh: bad interpreter: No such file or directory
make[1]: *** [database/database.h] Error 126
make[1]: Leaving directory `/home/ajan/Desktop/magic-7.4.54'

---

