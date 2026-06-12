---
title: "magic installation problem"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by skrr on 2008-02-16
hi 

i am new user of ubuntu and i want to install magic in my laptop and i found that error pls help me in step by step with complete command.

thanks

root@syed-laptop:/home/syed/cad/magic-7.5.119/magic# ./configure
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
checking sys/mman.h usability... yes
checking sys/mman.h presence... yes
checking for sys/mman.h... yes
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
checking for X... no
checking for XOpenDevice in -lXi... no
checking for tclConfig.sh... /usr/local/lib/tclConfig.sh
checking for tkConfig.sh... 
can't find Tk configuration script "tkConfig.sh"
Reverting to non-Tcl compilation
checking for rl_pre_input_hook in -lreadline... no
checking for rl_username_completion_function in -lreadline... no
checking for rl_filename_completion_function in -lreadline... no
checking for rl_attempted_completion_over in -lreadline... no
checking for tgetent in -ltermcap... no
checking for tgetent in -lncurses... no
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

Tcl/Tk:       no

  Without Tcl/Tk, you cannot run the enhanced version of magic
  with the toolbar and menus, and a number of other functions
  are disabled.  If you did not specifically disable Tcl/Tk on
  the configure command line, then getting this message means
  that you do not have Tcl/Tk headers and or libraries installed,
  or they are not in a standard path.  Try using configure options
  --with-tcl=<DIR> and --with-tk=<DIR>.

-----------------------------------------------------------

Use 'make' to compile and 'make install' to install.

Errors may not be printed to stdout:  see files 'make.log' 
  and 'install.log' for complete error summary.

-----------------------------------------------------------

---

### Post by lswest on 2008-02-16
have you tried running ```
sudo make
``` and ```
sudo make install
``` ?  does that give you more errors?

---

