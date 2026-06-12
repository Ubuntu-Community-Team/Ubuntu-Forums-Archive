---
title: "Help Installing Kino 1.1.1"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by cheeba on 2007-08-11
First off, this is my first post, Id love to say its been an absolute pleasure using Linux so far, but honestly...I've been struggling.  Ive been a die hard Windows user since 3.1 and actual command line computing is over my head.  I've been watchin you Linux guys for a while now and with the latest Ubuntu release I decided it was time to have a go at it.  I've been reading a lot the past months to try and get my hands around it and I'm determined to stick with it.  This is the first time I haven't been able to find anything out there that I needed help on, so on that note, thanks to all out there doing what they do to make nubs like me think its not too late to ween off of the MS teet. 

Ok now that thats out of the way....I have been trying to use Kino from Synaptic, however as Im sure all of you know its version 9.2.  Ive read a lot that you shouldnt install out of Synaptic unless you can help it.  Well 9.2 was giving me choppy video and audio while editing, not tolerable, and Im hoping 1.1.1 fixes it.   I removed 9.2 along with DVgrab (version 1. somthing) and DLed the new Kino 1.1.1 and DVGrab 3.0. 

I extracted them to my home directory no problems so far...I read somewhere that this needs to be compiled and to go to terminal, do ./configure then make install..that didnt to it for me.  Oh and Im trying to install Kino first.  I didnt think it would matter.  

If someone could take the time to walk me through an install that involves compiling Id greatly appreciate it, and it would be a learning experience for me.  I have a child comming into this world and the camcorder is going to be going full time.  If I cant get a decent movie editor to work I will reluctantly go back to XP.  Dont let me do it!!  Thansk in advance, sorry its so long but its my first one and i had a lot to say.

---

### Post by cheeba on 2007-08-11
Ok I have an update, I got Build Essentials, didnt have that, but same errors... here is terminal log...

nardelmj@michaels:~/kino-1.1.1$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
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
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
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
checking how to recognize dependent libraries... pass_all
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
checking the maximum length of command line arguments... 98304
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
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... msgfmt
checking for msgmerge... msgmerge
checking for xgettext... xgettext
checking for library containing strerror... none required
checking for ANSI C header files... (cached) yes
checking whether byte ordering is bigendian... no
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for LIBDV... configure: error: Package requirements (libdv >= 0.103) were not met:

No package 'libdv' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LIBDV_CFLAGS
and LIBDV_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

nardelmj@michaels:~/kino-1.1.1$ make
make: *** No targets specified and no makefile found.  Stop.
nardelmj@michaels:~/kino-1.1.1$ sudo make
Password:
make: *** No targets specified and no makefile found.  Stop.
nardelmj@michaels:~/kino-1.1.1$ sudo make install
make: *** No rule to make target `install'.  Stop.
nardelmj@michaels:~/kino-1.1.1$ 


Now it says I dont have libdv installed, I checked I have libdv4 installed..is that the same?  There is no libdv, there is a libdv-bin?

---

### Post by Amazona aestiva on 2007-08-15
Try this:
[http://www.getdeb.net/download.php?release=871&fpos=0]("http://www.getdeb.net/download.php?release=871&fpos=0")
Perhaps not 1.1.1 but better than 0.9.2 in Synaptic.;)

---

### Post by cheeba on 2007-08-16
Ok, that seemed to help.  Now Im at the point where I can burn to a disk.

I selected output, chose MPEG, DVD, Create DVD-Video (dvdauthor), it spit out an xml and an MPEG file, what am I suppose to do with those?  I was looking for an img or iso or video_TS or something...anyone help?

---

### Post by Amazona aestiva on 2007-08-17
Install DeVeDe. It converts mpeg to "video_ts", ISO or BIN/CUE images.;)
DeVeDe 3.01:
[http://www.getdeb.net/download.php?release=1106&fpos=0]("http://www.getdeb.net/download.php?release=1106&fpos=0")

In Feisty might need this:

[http://www.rastersoft.com/descargas/..._fixed.tar.bz2]("http://www.rastersoft.com/descargas/..._fixed.tar.bz2")
Install steps:
1.Unpack it
2.Open terminal
3.type cd (directory where you extracted) Example: cd '/home/nandor/Desktop/mplayer_fixed'
4.```
sudo ./install.sh
```

5.Enter your password

Good luck!

---

### Post by cheeba on 2007-08-19
Thanks for the help, 
I actually found the VIDEO TS folder  before I read your post.  didnt notice it at first.  I burned it but it wont play in my DVD player.  Only on my computer.  Im thinking its default setting to burn is in PAL, I need NTSC, anyone know how to change DVD AUTHOR FORMAT FROM PAL TO NSTC or check to see what format DVDAUTHOR is outputting to?

---

### Post by cheeba on 2007-08-19
I cant get the second link you provided to work.

---

### Post by Amazona aestiva on 2007-08-19
Sorry for mistake, here it is:
[http://www.rastersoft.com/descargas/mplayer_fixed.tar.bz2]("http://www.rastersoft.com/descargas/mplayer_fixed.tar.bz2")
Note don't use this if DeVeDe's output(when converting video from .mpg) is all right!
You need this if output sound is horrible!

---

### Post by Amazona aestiva on 2007-08-20
Must see what I wrote about there things:
[http://ubuntuforums.org/showthread.php?t=529759]("http://ubuntuforums.org/showthread.php?t=529759")

---

### Post by cheeba on 2007-08-20
> **Amazona aestiva said:**
> Sorry for mistake, here it is:
[http://www.rastersoft.com/descargas/mplayer_fixed.tar.bz2]("http://www.rastersoft.com/descargas/mplayer_fixed.tar.bz2")
Note don't use this if DeVeDe's output(when converting video from .mpg) is all right!
You need this if output sound is horrible!

Ok when I burned the mpeg to a DVD and played it on my TV it sounded awful, so Im assuming that thats what this fix is for?  

Also, where is a good place to learn about all those options in KINO, ffmpg, single/dual pass etc and all the other options on the mpeg menu.  How do you know when to use those?  I think my video could use some tweaking, it doesn't look very good at all , I can see horizontal lines on my TV when it play, and on the computer as well.  I tried the deinterlacing options and that helped a llittle.  By the way, thanks for the help so far!

Mike

---

### Post by Amazona aestiva on 2007-08-21
So You installed the fix, it said:
> 
Done. MPlayer and Mencoder downgraded. 

and the sound still awful?????

---

### Post by cheeba on 2007-09-06
Yeah It did sound terrible...sorry for the wait, I've been outta town.  good to be back!

---

### Post by Amazona aestiva on 2007-09-07
Welcome back, but I can't understand...
This should make the sound fine!!!!!!!! (it works for me)

What do You use? (Feisty, Edgy, Dapper)

Hmmm...
I advise to uninstall devede, mencoder, mplayer...
```
sudo apt-get remove mplayer mencoder devede
```

...and see the first link in my signature!

---

