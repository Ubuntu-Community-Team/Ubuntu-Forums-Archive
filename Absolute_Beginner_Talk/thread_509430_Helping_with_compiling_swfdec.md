---
title: "Helping with compiling swfdec"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by startgame412 on 2007-07-25
Hi I'm a newbie and am trying to compile the latest version of swfdec to play content on flash sites. When trying to compile swfdec version 0.5.0, I get an error saying configure: error: Couldn't find ffmpeg. You might need to install the libavcodec-dev and libswscale-dev packages. The first package that I need is installed according to symnatic  The second package cannot be found in symnatic. Has anyone had any success in building the latest version of swfdec and it's plugin for mozilla? Thanks.

---

### Post by startgame412 on 2007-07-25
DOes anyone know? I'm not trying to be a pian but the threads in these forums move really fast.

---

### Post by sad_iq on 2007-07-25
Have you installed all the necessary dependencies??? ```
sudo aptitude install autoconf automake gcc g++ libglib2.0-dev libgtk2.0-dev libasound2-dev liboil0.3-dev libmad0-dev libavcodec-dev firefox-dev libpango1.0-dev build-essential libtool libgstreamer0.10-dev libgnome-vfs-dev libgnomevfs2-dev liblame-dev libxvidcore4-dev libx264-dev libfaac-dev libfaad2-dev
```

---

### Post by startgame412 on 2007-07-25
Hi thanks for replying. Unfortunately, i still get the error saying that I need ffmpeg to install libavcodec-dev and libswscale-dev. I have libavcodec-dev installed already but libswscale-dev is not in my package manager. What do I do? Thanks.

---

### Post by doomster on 2007-07-25
correct me if iam wrong but shouldnt this fix the build dep problems? 
```
sudo apt-get build-dep swfdec
```

---

### Post by startgame412 on 2007-07-25
Hi unfortunately the command did not help. I get the message saying unable to find a source package for swfdec. Thanks for trying to help.

---

### Post by doomster on 2007-07-26
make sure you have all the essential files to build a program in ubuntu (most of them are not installed in the main distro , by using this :
```
~$ sudo apt-get install build-essential 

```

---

### Post by sad_iq on 2007-07-26
If not try compiling again and post the output here!!!

---

### Post by startgame412 on 2007-07-26
Hi, thanks for your replies. Here is the output



startgame412@startgame412-ppc:~$ cd swfdec/swfdec-0.5.0
startgame412@startgame412-ppc:~/swfdec/swfdec-0.5.0$ ./configure --prefix=/usr
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking to see if compiler understands -Wall... yes
checking to see if compiler understands -Wextra -Wno-missing-field-initializers -Wno-unused-parameter... yes
checking build system type... powerpc64-unknown-linux-gnu
checking host system type... powerpc64-unknown-linux-gnu
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
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld -m elf32ppclinux) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld -m elf32ppclinux
checking if the linker (/usr/bin/ld -m elf32ppclinux) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf32ppclinux) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld -m elf32ppclinux) supports shared libraries... yes
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking whether gcc and cc understand -c and -o together... yes
checking for ANSI C header files... (cached) yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GLIB... yes
checking for GTHREAD... yes
checking for PANGO... yes
checking for GTK... yes
checking for ALSA... yes
configure: audio backend: alsa
checking for LIBOIL... yes
checking for CAIRO... yes
checking for mad_decoder_finish in -lmad... yes
checking for FFMPEG... no
configure: error: Couldn't find ffmpeg. You might need to install the libavcodec-dev and libswscale-dev packages.
startgame412@startgame412-ppc:~/swfdec/swfdec-0.5.0$

---

### Post by RomeReactor on 2007-07-26
Hi. The **libswscale-dev** package does not show up in [Ubuntu's repositories]("http://packages.ubuntu.com/"), though you can find it in [Debian's]("http://packages.debian.org/unstable/libdevel/libswscale-dev")

Is there any reason you don't want to install the flashplayer package from Adobe?

---

### Post by startgame412 on 2007-07-27
Hi, I can't use the Adobe package becaue I am running on PowerPC linux.   The packages won't install becaue they require another package libc6 and whe nI attempt to install it it says that it will remove essentail ubuntu programs and it may break the system so I won't install it. Thanks for your help.  Anyone have latest version of swfdec compiled and installed? if so how did you do it. Thanks for your reples.

---

### Post by lambros on 2007-07-27
Can you install the libxine1-ffmpeg package?  If that doesn't help, you could maybe try installing the "gstreamer0.10-ffmpeg" package as well.

Lambros

---

### Post by lambros on 2007-07-27
I've just looked into this a little deeper - I think you need the libavcodec-dev package.
Edit: oops, I see you've already installed this! :-)

Lambros

---

### Post by startgame412 on 2007-07-27
Hi thanks for responding. I have the gstreamer0.10-ffmpeg package but I am not sure about the  libxine1-ffmpeg package. I am currently not at teh locatin of the computer with ubuntu ppc edition so I will post back in a few days when I get back to that computer and check to see if I have the  libxine1-ffmpeg package installed. Thanks.

---

### Post by RomeReactor on 2007-07-27
Have you tried [Gnash]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=gnash&searchon=names&subword=1&version=feisty&release=all")?

---

### Post by lambros on 2007-07-28
Sorry, my earlier posts are unlikely to be helpful.  I'm now trying to compile swfdec 0.5.0 and I'm running into exactly the same problem myself.  This is odd, because I got swfdec version 0.4.3 to compile without any problems.  I think the extra dependency of libswscale has recently been added - and that isn't in the Ubuntu repositories (at least, not for x86_64 which is what I'm using).

The libswscale package does appear to be in the Gutsy repositories though, so this might work if you were to upgrade to Gutsy.  But I recommend not to do this, unless you have a spare partition you can install Gutsy into.

I'll work on it and let you know if I find a solution.  It will probably involve downloading, compiling and installing libswscale, and then telling swfdec's configure script where to find it.  

Lambros

---

### Post by ubuntubrian on 2007-07-28
I'm having the same problem in trying to install gnash onto a dapper ppc system. I need to install, I think based on all my searching, the libswscale package which is not available for dapper ppc. I'll try the debianrepositories for a source package.

---

### Post by lambros on 2007-07-28
I'm afraid I still haven't got it to compile, but I have worked out how to fix the FFMPEG problem.  The easiest method seems to be to use the Gutsy sources.  For anybody who's interested, here's a way of doing it on a Fiesty system, without needing to upgrade to Gutsy.

Just for cleanliness, create a folder somewhere, called ffmpeg - doesn't matter where.  Go to [http://packages.ubuntu.com/gutsy/source/ffmpeg](http://packages.ubuntu.com/gutsy/source/ffmpeg) and download the two .gz files near the bottom.  These are the Gutsy FFMPEG sources and Ubuntu diffs.  Save these files to the ffmpeg folder.  This package contains what we need to build libswscale.

Open a command-shell, and 'cd' to your ffmpeg folder.  Unpack the source archive:
```
tar xf ffmpeg_0.cvs20070307.orig.tar.gz
```
I don't think this step is needed, but here's how to do it anyway, just in case.  Apply the Ubuntu diffs:
```
zcat ffmpeg_0.cvs20070307-5ubuntu4.diff.gz | patch -p0
```
Install everything needed to build FFMPEG:
```
sudo apt-get build-dep ffmpeg
```
Now prepare to build FFMPEG, which will include the libswscale library.  It should be possible to tweak this to avoid compiling stuff we don't need, but it's easiest just to do the whole lot:
```
cd ffmpeg-0.cvs20070307
./configure --enable-swscaler --enable-gpl --enable-shared

```

Now build and install it into /usr/local/
```
make
sudo make install

```

That's it!  Next time you try to build swfdec, that should get you past the FFMPEG problem.  But I ran into another issue that I don't know how to fix, so be warned!  It appears you need a later version of the ALSA libraries than what Feisty provides.  The problem I had was:

```
In file included from /usr/include/alsa/asoundlib.h:51,
                 from swfdec_playback.c:24:
/usr/include/alsa/timer.h:108: error: field 'tstamp' has incomplete type

```

I think you may need a later version of the libasound2-dev and libasound2 packages.
Or you might be able to get away with commenting out the offending line in the alsa/timer.h header file (I saw this suggestion on an ALSA forum somewhere).

Perhaps we're better off just waiting for Gutsy? :roll:

Lambros

---

### Post by startgame412 on 2007-08-02
Hi, thanks for hte replies everyone. It turns out that I did not have libxine1ffmpeg installed. I installed it but I have not tried to compile swfdec again. I will try to compile again and see what happens as well as follow the instructions given on here after my last post on this topic before this one to see what I get. I will post back when I try to compile it again and let you know how all goes. Thanks.

---

### Post by startgame412 on 2007-08-03
Hi I have tried to compile swfdec again and got past the ffmpeg error but it did not want to make it gave me an error. Unfortunately, I could not copy the entire make process but I think and hope that I got half to most of it. Around the end of hte process, I got an error message. Here is the make information whatever info I got from it anyway. 




ro -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I.. -I./jpeg/ -I/usr/include/liboil-0.3 -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/local/include -I/usr/local/include/ffmpeg -I/usr/local/include/swscale -DG_LOG_DOMAIN=\"Swfdec\" -g -O2 -MT libswfdec_0.5_la-swfdec_video.lo -MD -MP -MF .deps/libswfdec_0.5_la-swfdec_video.Tpo -c swfdec_video.c  -fPIC -DPIC -o .libs/libswfdec_0.5_la-swfdec_video.o
 gcc -DHAVE_CONFIG_H -I. -I.. -Wall -Wextra -Wno-missing-field-initializers -Wno-unused-parameter -std=c99 -I/usr/include/cairo -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I.. -I./jpeg/ -I/usr/include/liboil-0.3 -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/local/include -I/usr/local/include/ffmpeg -I/usr/local/include/swscale -DG_LOG_DOMAIN=\"Swfdec\" -g -O2 -MT libswfdec_0.5_la-swfdec_video.lo -MD -MP -MF .deps/libswfdec_0.5_la-swfdec_video.Tpo -c swfdec_video.c -o libswfdec_0.5_la-swfdec_video.o >/dev/null 2>&1
mv -f .deps/libswfdec_0.5_la-swfdec_video.Tpo .deps/libswfdec_0.5_la-swfdec_video.Plo
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..    -Wall -Wextra -Wno-missing-field-initializers -Wno-unused-parameter -std=c99 -I/usr/include/cairo -I/usr/include/freetype2 -I/usr/include/libpng12   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -I.. -I./jpeg/  -I/usr/include/liboil-0.3   -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2   -I/usr/local/include -I/usr/local/include/ffmpeg -I/usr/local/include/swscale    -DG_LOG_DOMAIN=\"Swfdec\" -g -O2 -MT libswfdec_0.5_la-swfdec_video_movie.lo -MD -MP -MF .deps/libswfdec_0.5_la-swfdec_video_movie.Tpo -c -o libswfdec_0.5_la-swfdec_video_movie.lo `test -f 'swfdec_video_movie.c' || echo './'`swfdec_video_movie.c
 gcc -DHAVE_CONFIG_H -I. -I.. -Wall -Wextra -Wno-missing-field-initializers -Wno-unused-parameter -std=c99 -I/usr/include/cairo -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I.. -I./jpeg/ -I/usr/include/liboil-0.3 -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/local/include -I/usr/local/include/ffmpeg -I/usr/local/include/swscale -DG_LOG_DOMAIN=\"Swfdec\" -g -O2 -MT libswfdec_0.5_la-swfdec_video_movie.lo -MD -MP -MF .deps/libswfdec_0.5_la-swfdec_video_movie.Tpo -c swfdec_video_movie.c  -fPIC -DPIC -o .libs/libswfdec_0.5_la-swfdec_video_movie.o
 gcc -DHAVE_CONFIG_H -I. -I.. -Wall -Wextra -Wno-missing-field-initializers -Wno-unused-parameter -std=c99 -I/usr/include/cairo -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I.. -I./jpeg/ -I/usr/include/liboil-0.3 -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/local/include -I/usr/local/include/ffmpeg -I/usr/local/include/swscale -DG_LOG_DOMAIN=\"Swfdec\" -g -O2 -MT libswfdec_0.5_la-swfdec_video_movie.lo -MD -MP -MF .deps/libswfdec_0.5_la-swfdec_video_movie.Tpo -c swfdec_video_movie.c -o libswfdec_0.5_la-swfdec_video_movie.o >/dev/null 2>&1
mv -f .deps/libswfdec_0.5_la-swfdec_video_movie.Tpo .deps/libswfdec_0.5_la-swfdec_video_movie.Plo
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..    -Wall -Wextra -Wno-missing-field-initializers -Wno-unused-parameter -std=c99 -I/usr/include/cairo -I/usr/include/freetype2 -I/usr/include/libpng12   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -I.. -I./jpeg/  -I/usr/include/liboil-0.3   -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2   -I/usr/local/include -I/usr/local/include/ffmpeg -I/usr/local/include/swscale    -DG_LOG_DOMAIN=\"Swfdec\" -g -O2 -MT libswfdec_0.5_la-swfdec_video_movie_as.lo -MD -MP -MF .deps/libswfdec_0.5_la-swfdec_video_movie_as.Tpo -c -o libswfdec_0.5_la-swfdec_video_movie_as.lo `test -f 'swfdec_video_movie_as.c' || echo './'`swfdec_video_movie_as.c
 gcc -DHAVE_CONFIG_H -I. -I.. -Wall -Wextra -Wno-missing-field-initializers -Wno-unused-parameter -std=c99 -I/usr/include/cairo -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I.. -I./jpeg/ -I/usr/include/liboil-0.3 -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/local/include -I/usr/local/include/ffmpeg -I/usr/local/include/swscale -DG_LOG_DOMAIN=\"Swfdec\" -g -O2 -MT libswfdec_0.5_la-swfdec_video_movie_as.lo -MD -MP -MF .deps/libswfdec_0.5_la-swfdec_video_movie_as.Tpo -c swfdec_video_movie_as.c  -fPIC -DPIC -o .libs/libswfdec_0.5_la-swfdec_video_movie_as.o
 gcc -DHAVE_CONFIG_H -I. -I.. -Wall -Wextra -Wno-missing-field-initializers -Wno-unused-parameter -std=c99 -I/usr/include/cairo -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I.. -I./jpeg/ -I/usr/include/liboil-0.3 -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/local/include -I/usr/local/include/ffmpeg -I/usr/local/include/swscale -DG_LOG_DOMAIN=\"Swfdec\" -g -O2 -MT libswfdec_0.5_la-swfdec_video_movie_as.lo -MD -MP -MF .deps/libswfdec_0.5_la-swfdec_video_movie_as.Tpo -c swfdec_video_movie_as.c -o libswfdec_0.5_la-swfdec_video_movie_as.o >/dev/null 2>&1
mv -f .deps/libswfdec_0.5_la-swfdec_video_movie_as.Tpo .deps/libswfdec_0.5_la-swfdec_video_movie_as.Plo
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..    -Wall -Wextra -Wno-missing-field-initializers -Wno-unused-parameter -std=c99 -I/usr/include/cairo -I/usr/include/freetype2 -I/usr/include/libpng12   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -I.. -I./jpeg/  -I/usr/include/liboil-0.3   -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2   -I/usr/local/include -I/usr/local/include/ffmpeg -I/usr/local/include/swscale    -DG_LOG_DOMAIN=\"Swfdec\" -g -O2 -MT libswfdec_0.5_la-swfdec_xml.lo -MD -MP -MF .deps/libswfdec_0.5_la-swfdec_xml.Tpo -c -o libswfdec_0.5_la-swfdec_xml.lo `test -f 'swfdec_xml.c' || echo './'`swfdec_xml.c
 gcc -DHAVE_CONFIG_H -I. -I.. -Wall -Wextra -Wno-missing-field-initializers -Wno-unused-parameter -std=c99 -I/usr/include/cairo -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I.. -I./jpeg/ -I/usr/include/liboil-0.3 -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/local/include -I/usr/local/include/ffmpeg -I/usr/local/include/swscale -DG_LOG_DOMAIN=\"Swfdec\" -g -O2 -MT libswfdec_0.5_la-swfdec_xml.lo -MD -MP -MF .deps/libswfdec_0.5_la-swfdec_xml.Tpo -c swfdec_xml.c  -fPIC -DPIC -o .libs/libswfdec_0.5_la-swfdec_xml.o
 gcc -DHAVE_CONFIG_H -I. -I.. -Wall -Wextra -Wno-missing-field-initializers -Wno-unused-parameter -std=c99 -I/usr/include/cairo -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I.. -I./jpeg/ -I/usr/include/liboil-0.3 -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/local/include -I/usr/local/include/ffmpeg -I/usr/local/include/swscale -DG_LOG_DOMAIN=\"Swfdec\" -g -O2 -MT libswfdec_0.5_la-swfdec_xml.lo -MD -MP -MF .deps/libswfdec_0.5_la-swfdec_xml.Tpo -c swfdec_xml.c -o libswfdec_0.5_la-swfdec_xml.o >/dev/null 2>&1
mv -f .deps/libswfdec_0.5_la-swfdec_xml.Tpo .deps/libswfdec_0.5_la-swfdec_xml.Plo
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..    -Wall -Wextra -Wno-missing-field-initializers -Wno-unused-parameter -std=c99 -I/usr/include/cairo -I/usr/include/freetype2 -I/usr/include/libpng12   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -I.. -I./jpeg/  -I/usr/include/liboil-0.3   -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2   -I/usr/local/include -I/usr/local/include/ffmpeg -I/usr/local/include/swscale    -DG_LOG_DOMAIN=\"Swfdec\" -g -O2 -MT libswfdec_0.5_la-swfdec_xml_as.lo -MD -MP -MF .deps/libswfdec_0.5_la-swfdec_xml_as.Tpo -c -o libswfdec_0.5_la-swfdec_xml_as.lo `test -f 'swfdec_xml_as.c' || echo './'`swfdec_xml_as.c
 gcc -DHAVE_CONFIG_H -I. -I.. -Wall -Wextra -Wno-missing-field-initializers -Wno-unused-parameter -std=c99 -I/usr/include/cairo -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I.. -I./jpeg/ -I/usr/include/liboil-0.3 -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/local/include -I/usr/local/include/ffmpeg -I/usr/local/include/swscale -DG_LOG_DOMAIN=\"Swfdec\" -g -O2 -MT libswfdec_0.5_la-swfdec_xml_as.lo -MD -MP -MF .deps/libswfdec_0.5_la-swfdec_xml_as.Tpo -c swfdec_xml_as.c  -fPIC -DPIC -o .libs/libswfdec_0.5_la-swfdec_xml_as.o
 gcc -DHAVE_CONFIG_H -I. -I.. -Wall -Wextra -Wno-missing-field-initializers -Wno-unused-parameter -std=c99 -I/usr/include/cairo -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I.. -I./jpeg/ -I/usr/include/liboil-0.3 -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/local/include -I/usr/local/include/ffmpeg -I/usr/local/include/swscale -DG_LOG_DOMAIN=\"Swfdec\" -g -O2 -MT libswfdec_0.5_la-swfdec_xml_as.lo -MD -MP -MF .deps/libswfdec_0.5_la-swfdec_xml_as.Tpo -c swfdec_xml_as.c -o libswfdec_0.5_la-swfdec_xml_as.o >/dev/null 2>&1
mv -f .deps/libswfdec_0.5_la-swfdec_xml_as.Tpo .deps/libswfdec_0.5_la-swfdec_xml_as.Plo
/bin/bash ../libtool --tag=CC   --mode=link gcc -Wall -Wextra -Wno-missing-field-initializers -Wno-unused-parameter -std=c99 -I/usr/include/cairo -I/usr/include/freetype2 -I/usr/include/libpng12   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -I.. -I./jpeg/  -I/usr/include/liboil-0.3   -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2   -I/usr/local/include -I/usr/local/include/ffmpeg -I/usr/local/include/swscale    -DG_LOG_DOMAIN=\"Swfdec\" -g -O2 -Wl,-Bsymbolic -version-info 0:0:0 -export-symbols-regex '^(swfdec_.*)' -lcairo   -lgobject-2.0 -lglib-2.0   -lpangocairo-1.0 -lpango-1.0 -lcairo -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   -loil-0.3 -lm   -lz -lmad -L/usr/local/lib -lavcodec -lm -lz -ldl -lswscale -lavutil   -pthread -lgstreamer-0.10 -lgobject-2.0 -lgmodule-2.0 -ldl -lgthread-2.0 -lrt -lxml2 -lglib-2.0    -o libswfdec-0.5.la -rpath /usr/lib libswfdec_0.5_la-swfdec_as_array.lo libswfdec_0.5_la-swfdec_as_boolean.lo libswfdec_0.5_la-swfdec_as_context.lo libswfdec_0.5_la-swfdec_as_frame.lo libswfdec_0.5_la-swfdec_as_function.lo libswfdec_0.5_la-swfdec_as_interpret.lo libswfdec_0.5_la-swfdec_as_math.lo libswfdec_0.5_la-swfdec_as_native_function.lo libswfdec_0.5_la-swfdec_as_number.lo libswfdec_0.5_la-swfdec_as_object.lo libswfdec_0.5_la-swfdec_as_scope.lo libswfdec_0.5_la-swfdec_as_script_function.lo libswfdec_0.5_la-swfdec_as_stack.lo libswfdec_0.5_la-swfdec_as_string.lo libswfdec_0.5_la-swfdec_as_strings.lo libswfdec_0.5_la-swfdec_as_super.lo libswfdec_0.5_la-swfdec_as_types.lo libswfdec_0.5_la-swfdec_as_with.lo libswfdec_0.5_la-swfdec_amf.lo libswfdec_0.5_la-swfdec_audio.lo libswfdec_0.5_la-swfdec_audio_event.lo libswfdec_0.5_la-swfdec_audio_flv.lo libswfdec_0.5_la-swfdec_audio_stream.lo libswfdec_0.5_la-swfdec_bits.lo libswfdec_0.5_la-swfdec_buffer.lo libswfdec_0.5_la-swfdec_button.lo libswfdec_0.5_la-swfdec_button_movie.lo libswfdec_0.5_la-swfdec_cache.lo libswfdec_0.5_la-swfdec_cached.lo libswfdec_0.5_la-swfdec_character.lo libswfdec_0.5_la-swfdec_codec_adpcm.lo libswfdec_0.5_la-swfdec_codec_audio.lo libswfdec_0.5_la-swfdec_codec_ffmpeg.lo libswfdec_0.5_la-swfdec_codec_gst.lo libswfdec_0.5_la-swfdec_codec_mad.lo libswfdec_0.5_la-swfdec_codec_screen.lo libswfdec_0.5_la-swfdec_codec_video.lo libswfdec_0.5_la-swfdec_color.lo libswfdec_0.5_la-swfdec_color_as.lo libswfdec_0.5_la-swfdec_debug.lo libswfdec_0.5_la-swfdec_debugger.lo libswfdec_0.5_la-swfdec_decoder.lo libswfdec_0.5_la-swfdec_edittext.lo libswfdec_0.5_la-swfdec_edittext_movie.lo libswfdec_0.5_la-swfdec_enums.lo libswfdec_0.5_la-swfdec_event.lo libswfdec_0.5_la-swfdec_flv_decoder.lo libswfdec_0.5_la-swfdec_font.lo libswfdec_0.5_la-swfdec_graphic.lo libswfdec_0.5_la-swfdec_graphic_movie.lo libswfdec_0.5_la-swfdec_html_parser.lo libswfdec_0.5_la-swfdec_image.lo libswfdec_0.5_la-swfdec_interval.lo libswfdec_0.5_la-swfdec_listener.lo libswfdec_0.5_la-swfdec_loader.lo libswfdec_0.5_la-swfdec_loadertarget.lo libswfdec_0.5_la-swfdec_marshal.lo libswfdec_0.5_la-swfdec_morph_movie.lo libswfdec_0.5_la-swfdec_morphshape.lo libswfdec_0.5_la-swfdec_mouse_as.lo libswfdec_0.5_la-swfdec_movie.lo libswfdec_0.5_la-swfdec_movie_asprops.lo libswfdec_0.5_la-swfdec_net_connection.lo libswfdec_0.5_la-swfdec_net_stream.lo libswfdec_0.5_la-swfdec_net_stream_as.lo libswfdec_0.5_la-swfdec_pattern.lo libswfdec_0.5_la-swfdec_player.lo libswfdec_0.5_la-swfdec_player_as.lo libswfdec_0.5_la-swfdec_rect.lo libswfdec_0.5_la-swfdec_ringbuffer.lo libswfdec_0.5_la-swfdec_script.lo libswfdec_0.5_la-swfdec_shape.lo libswfdec_0.5_la-swfdec_sound.lo libswfdec_0.5_la-swfdec_stroke.lo libswfdec_0.5_la-swfdec_sprite.lo libswfdec_0.5_la-swfdec_sprite_movie.lo libswfdec_0.5_la-swfdec_sprite_movie_as.lo libswfdec_0.5_la-swfdec_swf_decoder.lo libswfdec_0.5_la-swfdec_swf_instance.lo libswfdec_0.5_la-swfdec_tag.lo libswfdec_0.5_la-swfdec_text.lo libswfdec_0.5_la-swfdec_utils.lo libswfdec_0.5_la-swfdec_video.lo libswfdec_0.5_la-swfdec_video_movie.lo libswfdec_0.5_la-swfdec_video_movie_as.lo libswfdec_0.5_la-swfdec_xml.lo libswfdec_0.5_la-swfdec_xml_as.lo jpeg/libjpeg.la  
generating symbol list for `libswfdec-0.5.la'
/usr/bin/nm -B  .libs/libswfdec_0.5_la-swfdec_as_array.o .libs/libswfdec_0.5_la-swfdec_as_boolean.o .libs/libswfdec_0.5_la-swfdec_as_context.o .libs/libswfdec_0.5_la-swfdec_as_frame.o .libs/libswfdec_0.5_la-swfdec_as_function.o .libs/libswfdec_0.5_la-swfdec_as_interpret.o .libs/libswfdec_0.5_la-swfdec_as_math.o .libs/libswfdec_0.5_la-swfdec_as_native_function.o .libs/libswfdec_0.5_la-swfdec_as_number.o .libs/libswfdec_0.5_la-swfdec_as_object.o .libs/libswfdec_0.5_la-swfdec_as_scope.o .libs/libswfdec_0.5_la-swfdec_as_script_function.o .libs/libswfdec_0.5_la-swfdec_as_stack.o .libs/libswfdec_0.5_la-swfdec_as_string.o .libs/libswfdec_0.5_la-swfdec_as_strings.o .libs/libswfdec_0.5_la-swfdec_as_super.o .libs/libswfdec_0.5_la-swfdec_as_types.o .libs/libswfdec_0.5_la-swfdec_as_with.o .libs/libswfdec_0.5_la-swfdec_amf.o .libs/libswfdec_0.5_la-swfdec_audio.o .libs/libswfdec_0.5_la-swfdec_audio_event.o .libs/libswfdec_0.5_la-swfdec_audio_flv.o .libs/libswfdec_0.5_la-swfdec_audio_stream.o .libs/libswfdec_0.5_la-swfdec_bits.o .libs/libswfdec_0.5_la-swfdec_buffer.o .libs/libswfdec_0.5_la-swfdec_button.o .libs/libswfdec_0.5_la-swfdec_button_movie.o .libs/libswfdec_0.5_la-swfdec_cache.o .libs/libswfdec_0.5_la-swfdec_cached.o .libs/libswfdec_0.5_la-swfdec_character.o .libs/libswfdec_0.5_la-swfdec_codec_adpcm.o .libs/libswfdec_0.5_la-swfdec_codec_audio.o .libs/libswfdec_0.5_la-swfdec_codec_ffmpeg.o .libs/libswfdec_0.5_la-swfdec_codec_gst.o .libs/libswfdec_0.5_la-swfdec_codec_mad.o .libs/libswfdec_0.5_la-swfdec_codec_screen.o .libs/libswfdec_0.5_la-swfdec_codec_video.o .libs/libswfdec_0.5_la-swfdec_color.o .libs/libswfdec_0.5_la-swfdec_color_as.o .libs/libswfdec_0.5_la-swfdec_debug.o .libs/libswfdec_0.5_la-swfdec_debugger.o .libs/libswfdec_0.5_la-swfdec_decoder.o .libs/libswfdec_0.5_la-swfdec_edittext.o .libs/libswfdec_0.5_la-swfdec_edittext_movie.o .libs/libswfdec_0.5_la-swfdec_enums.o .libs/libswfdec_0.5_la-swfdec_event.o .libs/libswfdec_0.5_la-swfdec_flv_decoder.o .libs/libswfdec_0.5_la-swfdec_font.o .libs/libswfdec_0.5_la-swfdec_graphic.o .libs/libswfdec_0.5_la-swfdec_graphic_movie.o .libs/libswfdec_0.5_la-swfdec_html_parser.o .libs/libswfdec_0.5_la-swfdec_image.o .libs/libswfdec_0.5_la-swfdec_interval.o .libs/libswfdec_0.5_la-swfdec_listener.o .libs/libswfdec_0.5_la-swfdec_loader.o .libs/libswfdec_0.5_la-swfdec_loadertarget.o .libs/libswfdec_0.5_la-swfdec_marshal.o .libs/libswfdec_0.5_la-swfdec_morph_movie.o .libs/libswfdec_0.5_la-swfdec_morphshape.o .libs/libswfdec_0.5_la-swfdec_mouse_as.o .libs/libswfdec_0.5_la-swfdec_movie.o .libs/libswfdec_0.5_la-swfdec_movie_asprops.o .libs/libswfdec_0.5_la-swfdec_net_connection.o .libs/libswfdec_0.5_la-swfdec_net_stream.o .libs/libswfdec_0.5_la-swfdec_net_stream_as.o .libs/libswfdec_0.5_la-swfdec_pattern.o .libs/libswfdec_0.5_la-swfdec_player.o .libs/libswfdec_0.5_la-swfdec_player_as.o .libs/libswfdec_0.5_la-swfdec_rect.o .libs/libswfdec_0.5_la-swfdec_ringbuffer.o .libs/libswfdec_0.5_la-swfdec_script.o .libs/libswfdec_0.5_la-swfdec_shape.o .libs/libswfdec_0.5_la-swfdec_sound.o .libs/libswfdec_0.5_la-swfdec_stroke.o .libs/libswfdec_0.5_la-swfdec_sprite.o .libs/libswfdec_0.5_la-swfdec_sprite_movie.o .libs/libswfdec_0.5_la-swfdec_sprite_movie_as.o .libs/libswfdec_0.5_la-swfdec_swf_decoder.o .libs/libswfdec_0.5_la-swfdec_swf_instance.o .libs/libswfdec_0.5_la-swfdec_tag.o .libs/libswfdec_0.5_la-swfdec_text.o .libs/libswfdec_0.5_la-swfdec_utils.o .libs/libswfdec_0.5_la-swfdec_video.o .libs/libswfdec_0.5_la-swfdec_video_movie.o .libs/libswfdec_0.5_la-swfdec_video_movie_as.o .libs/libswfdec_0.5_la-swfdec_xml.o .libs/libswfdec_0.5_la-swfdec_xml_as.o  jpeg/.libs/libjpeg.a | sed -n -e 's/^.*[     ]\([ABCDGIRSTW][ABCDGIRSTW]*\)[         ][      ]*\([_A-Za-z][_A-Za-z0-9]*\)$/\1 \2 \2/p' | /bin/sed 's/.* //' | sort | uniq > .libs/libswfdec-0.5.exp
/bin/grep -E -e "^(swfdec_.*)" ".libs/libswfdec-0.5.exp" > ".libs/libswfdec-0.5.expT"
mv -f ".libs/libswfdec-0.5.expT" ".libs/libswfdec-0.5.exp"
echo "{ global:" > .libs/libswfdec-0.5.ver
 cat .libs/libswfdec-0.5.exp | sed -e "s/\(.*\)/\1;/" >> .libs/libswfdec-0.5.ver
 echo "local: *; };" >> .libs/libswfdec-0.5.ver
 gcc -shared  .libs/libswfdec_0.5_la-swfdec_as_array.o .libs/libswfdec_0.5_la-swfdec_as_boolean.o .libs/libswfdec_0.5_la-swfdec_as_context.o .libs/libswfdec_0.5_la-swfdec_as_frame.o .libs/libswfdec_0.5_la-swfdec_as_function.o .libs/libswfdec_0.5_la-swfdec_as_interpret.o .libs/libswfdec_0.5_la-swfdec_as_math.o .libs/libswfdec_0.5_la-swfdec_as_native_function.o .libs/libswfdec_0.5_la-swfdec_as_number.o .libs/libswfdec_0.5_la-swfdec_as_object.o .libs/libswfdec_0.5_la-swfdec_as_scope.o .libs/libswfdec_0.5_la-swfdec_as_script_function.o .libs/libswfdec_0.5_la-swfdec_as_stack.o .libs/libswfdec_0.5_la-swfdec_as_string.o .libs/libswfdec_0.5_la-swfdec_as_strings.o .libs/libswfdec_0.5_la-swfdec_as_super.o .libs/libswfdec_0.5_la-swfdec_as_types.o .libs/libswfdec_0.5_la-swfdec_as_with.o .libs/libswfdec_0.5_la-swfdec_amf.o .libs/libswfdec_0.5_la-swfdec_audio.o .libs/libswfdec_0.5_la-swfdec_audio_event.o .libs/libswfdec_0.5_la-swfdec_audio_flv.o .libs/libswfdec_0.5_la-swfdec_audio_stream.o .libs/libswfdec_0.5_la-swfdec_bits.o .libs/libswfdec_0.5_la-swfdec_buffer.o .libs/libswfdec_0.5_la-swfdec_button.o .libs/libswfdec_0.5_la-swfdec_button_movie.o .libs/libswfdec_0.5_la-swfdec_cache.o .libs/libswfdec_0.5_la-swfdec_cached.o .libs/libswfdec_0.5_la-swfdec_character.o .libs/libswfdec_0.5_la-swfdec_codec_adpcm.o .libs/libswfdec_0.5_la-swfdec_codec_audio.o .libs/libswfdec_0.5_la-swfdec_codec_ffmpeg.o .libs/libswfdec_0.5_la-swfdec_codec_gst.o .libs/libswfdec_0.5_la-swfdec_codec_mad.o .libs/libswfdec_0.5_la-swfdec_codec_screen.o .libs/libswfdec_0.5_la-swfdec_codec_video.o .libs/libswfdec_0.5_la-swfdec_color.o .libs/libswfdec_0.5_la-swfdec_color_as.o .libs/libswfdec_0.5_la-swfdec_debug.o .libs/libswfdec_0.5_la-swfdec_debugger.o .libs/libswfdec_0.5_la-swfdec_decoder.o .libs/libswfdec_0.5_la-swfdec_edittext.o .libs/libswfdec_0.5_la-swfdec_edittext_movie.o .libs/libswfdec_0.5_la-swfdec_enums.o .libs/libswfdec_0.5_la-swfdec_event.o .libs/libswfdec_0.5_la-swfdec_flv_decoder.o .libs/libswfdec_0.5_la-swfdec_font.o .libs/libswfdec_0.5_la-swfdec_graphic.o .libs/libswfdec_0.5_la-swfdec_graphic_movie.o .libs/libswfdec_0.5_la-swfdec_html_parser.o .libs/libswfdec_0.5_la-swfdec_image.o .libs/libswfdec_0.5_la-swfdec_interval.o .libs/libswfdec_0.5_la-swfdec_listener.o .libs/libswfdec_0.5_la-swfdec_loader.o .libs/libswfdec_0.5_la-swfdec_loadertarget.o .libs/libswfdec_0.5_la-swfdec_marshal.o .libs/libswfdec_0.5_la-swfdec_morph_movie.o .libs/libswfdec_0.5_la-swfdec_morphshape.o .libs/libswfdec_0.5_la-swfdec_mouse_as.o .libs/libswfdec_0.5_la-swfdec_movie.o .libs/libswfdec_0.5_la-swfdec_movie_asprops.o .libs/libswfdec_0.5_la-swfdec_net_connection.o .libs/libswfdec_0.5_la-swfdec_net_stream.o .libs/libswfdec_0.5_la-swfdec_net_stream_as.o .libs/libswfdec_0.5_la-swfdec_pattern.o .libs/libswfdec_0.5_la-swfdec_player.o .libs/libswfdec_0.5_la-swfdec_player_as.o .libs/libswfdec_0.5_la-swfdec_rect.o .libs/libswfdec_0.5_la-swfdec_ringbuffer.o .libs/libswfdec_0.5_la-swfdec_script.o .libs/libswfdec_0.5_la-swfdec_shape.o .libs/libswfdec_0.5_la-swfdec_sound.o .libs/libswfdec_0.5_la-swfdec_stroke.o .libs/libswfdec_0.5_la-swfdec_sprite.o .libs/libswfdec_0.5_la-swfdec_sprite_movie.o .libs/libswfdec_0.5_la-swfdec_sprite_movie_as.o .libs/libswfdec_0.5_la-swfdec_swf_decoder.o .libs/libswfdec_0.5_la-swfdec_swf_instance.o .libs/libswfdec_0.5_la-swfdec_tag.o .libs/libswfdec_0.5_la-swfdec_text.o .libs/libswfdec_0.5_la-swfdec_utils.o .libs/libswfdec_0.5_la-swfdec_video.o .libs/libswfdec_0.5_la-swfdec_video_movie.o .libs/libswfdec_0.5_la-swfdec_video_movie_as.o .libs/libswfdec_0.5_la-swfdec_xml.o .libs/libswfdec_0.5_la-swfdec_xml_as.o -Wl,--whole-archive jpeg/.libs/libjpeg.a -Wl,--no-whole-archive  /usr/lib/libpangocairo-1.0.so /usr/lib/libpango-1.0.so /usr/lib/libcairo.so -loil-0.3 /usr/lib/libmad.so -L/usr/local/lib -lavcodec -lm -lz -lswscale -lavutil /usr/lib/libgstreamer-0.10.so /usr/lib/libgobject-2.0.so /usr/lib/libgmodule-2.0.so -ldl /usr/lib/libgthread-2.0.so -lrt /usr/lib/libxml2.so /usr/lib/libglib-2.0.so  -pthread -Wl,-Bsymbolic -pthread -Wl,-soname -Wl,libswfdec-0.5.so.0 -Wl,-version-script -Wl,.libs/libswfdec-0.5.ver -o .libs/libswfdec-0.5.so.0.0.0
(cd .libs && rm -f libswfdec-0.5.so.0 && ln -s libswfdec-0.5.so.0.0.0 libswfdec-0.5.so.0)
(cd .libs && rm -f libswfdec-0.5.so && ln -s libswfdec-0.5.so.0.0.0 libswfdec-0.5.so)
rm -fr .libs/libswfdec-0.5.lax
mkdir .libs/libswfdec-0.5.lax
rm -fr .libs/libswfdec-0.5.lax/libjpeg.a
mkdir .libs/libswfdec-0.5.lax/libjpeg.a
(cd .libs/libswfdec-0.5.lax/libjpeg.a && ar x /home/startgame412/swfdec/swfdec-0.5.0/libswfdec/jpeg/.libs/libjpeg.a)
ar cru .libs/libswfdec-0.5.a  libswfdec_0.5_la-swfdec_as_array.o libswfdec_0.5_la-swfdec_as_boolean.o libswfdec_0.5_la-swfdec_as_context.o libswfdec_0.5_la-swfdec_as_frame.o libswfdec_0.5_la-swfdec_as_function.o libswfdec_0.5_la-swfdec_as_interpret.o libswfdec_0.5_la-swfdec_as_math.o libswfdec_0.5_la-swfdec_as_native_function.o libswfdec_0.5_la-swfdec_as_number.o libswfdec_0.5_la-swfdec_as_object.o libswfdec_0.5_la-swfdec_as_scope.o libswfdec_0.5_la-swfdec_as_script_function.o libswfdec_0.5_la-swfdec_as_stack.o libswfdec_0.5_la-swfdec_as_string.o libswfdec_0.5_la-swfdec_as_strings.o libswfdec_0.5_la-swfdec_as_super.o libswfdec_0.5_la-swfdec_as_types.o libswfdec_0.5_la-swfdec_as_with.o libswfdec_0.5_la-swfdec_amf.o libswfdec_0.5_la-swfdec_audio.o libswfdec_0.5_la-swfdec_audio_event.o libswfdec_0.5_la-swfdec_audio_flv.o libswfdec_0.5_la-swfdec_audio_stream.o libswfdec_0.5_la-swfdec_bits.o libswfdec_0.5_la-swfdec_buffer.o libswfdec_0.5_la-swfdec_button.o libswfdec_0.5_la-swfdec_button_movie.o libswfdec_0.5_la-swfdec_cache.o libswfdec_0.5_la-swfdec_cached.o libswfdec_0.5_la-swfdec_character.o libswfdec_0.5_la-swfdec_codec_adpcm.o libswfdec_0.5_la-swfdec_codec_audio.o libswfdec_0.5_la-swfdec_codec_ffmpeg.o libswfdec_0.5_la-swfdec_codec_gst.o libswfdec_0.5_la-swfdec_codec_mad.o libswfdec_0.5_la-swfdec_codec_screen.o libswfdec_0.5_la-swfdec_codec_video.o libswfdec_0.5_la-swfdec_color.o libswfdec_0.5_la-swfdec_color_as.o libswfdec_0.5_la-swfdec_debug.o libswfdec_0.5_la-swfdec_debugger.o libswfdec_0.5_la-swfdec_decoder.o libswfdec_0.5_la-swfdec_edittext.o libswfdec_0.5_la-swfdec_edittext_movie.o libswfdec_0.5_la-swfdec_enums.o libswfdec_0.5_la-swfdec_event.o libswfdec_0.5_la-swfdec_flv_decoder.o libswfdec_0.5_la-swfdec_font.o libswfdec_0.5_la-swfdec_graphic.o libswfdec_0.5_la-swfdec_graphic_movie.o libswfdec_0.5_la-swfdec_html_parser.o libswfdec_0.5_la-swfdec_image.o libswfdec_0.5_la-swfdec_interval.o libswfdec_0.5_la-swfdec_listener.o libswfdec_0.5_la-swfdec_loader.o libswfdec_0.5_la-swfdec_loadertarget.o libswfdec_0.5_la-swfdec_marshal.o libswfdec_0.5_la-swfdec_morph_movie.o libswfdec_0.5_la-swfdec_morphshape.o libswfdec_0.5_la-swfdec_mouse_as.o libswfdec_0.5_la-swfdec_movie.o libswfdec_0.5_la-swfdec_movie_asprops.o libswfdec_0.5_la-swfdec_net_connection.o libswfdec_0.5_la-swfdec_net_stream.o libswfdec_0.5_la-swfdec_net_stream_as.o libswfdec_0.5_la-swfdec_pattern.o libswfdec_0.5_la-swfdec_player.o libswfdec_0.5_la-swfdec_player_as.o libswfdec_0.5_la-swfdec_rect.o libswfdec_0.5_la-swfdec_ringbuffer.o libswfdec_0.5_la-swfdec_script.o libswfdec_0.5_la-swfdec_shape.o libswfdec_0.5_la-swfdec_sound.o libswfdec_0.5_la-swfdec_stroke.o libswfdec_0.5_la-swfdec_sprite.o libswfdec_0.5_la-swfdec_sprite_movie.o libswfdec_0.5_la-swfdec_sprite_movie_as.o libswfdec_0.5_la-swfdec_swf_decoder.o libswfdec_0.5_la-swfdec_swf_instance.o libswfdec_0.5_la-swfdec_tag.o libswfdec_0.5_la-swfdec_text.o libswfdec_0.5_la-swfdec_utils.o libswfdec_0.5_la-swfdec_video.o libswfdec_0.5_la-swfdec_video_movie.o libswfdec_0.5_la-swfdec_video_movie_as.o libswfdec_0.5_la-swfdec_xml.o libswfdec_0.5_la-swfdec_xml_as.o  .libs/libswfdec-0.5.lax/libjpeg.a/libjpeg_la-jpeg_tables.o .libs/libswfdec-0.5.lax/libjpeg.a/libjpeg_la-jpeg_rgb_decoder.o .libs/libswfdec-0.5.lax/libjpeg.a/libjpeg_la-jpeg.o .libs/libswfdec-0.5.lax/libjpeg.a/libjpeg_la-jpeg_bits.o .libs/libswfdec-0.5.lax/libjpeg.a/libjpeg_la-jpeg_huffman.o 
ranlib .libs/libswfdec-0.5.a
rm -fr .libs/libswfdec-0.5.lax
creating libswfdec-0.5.la
(cd .libs && rm -f libswfdec-0.5.la && ln -s ../libswfdec-0.5.la libswfdec-0.5.la)
make[4]: Leaving directory `/home/startgame412/swfdec/swfdec-0.5.0/libswfdec'
make[3]: Leaving directory `/home/startgame412/swfdec/swfdec-0.5.0/libswfdec'
make[2]: Leaving directory `/home/startgame412/swfdec/swfdec-0.5.0/libswfdec'
Making all in libswfdec-gtk
make[2]: Entering directory `/home/startgame412/swfdec/swfdec-0.5.0/libswfdec-gtk'
cmp -s ./swfdec_playback_alsa.c swfdec_playback.c \
        || cp ./swfdec_playback_alsa.c swfdec_playback.c
make  all-am
make[3]: Entering directory `/home/startgame412/swfdec/swfdec-0.5.0/libswfdec-gtk'
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..    -I.. -I./js/ -I../libswfdec/js -DXP_UNIX -DDEBUG -Wall -Wextra -Wno-missing-field-initializers -Wno-unused-parameter -std=c99 -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/cairo -I/usr/include/freetype2 -I/usr/include/libpng12   -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -I/usr/include/alsa   -pthread -DORBIT2=1 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/gconf/2 -I/usr/include/orbit-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DG_LOG_DOMAIN=\"Swfdec-Gtk\" -DXP_UNIX -g -O2 -MT libswfdec_gtk_0.5_la-swfdec_playback.lo -MD -MP -MF .deps/libswfdec_gtk_0.5_la-swfdec_playback.Tpo -c -o libswfdec_gtk_0.5_la-swfdec_playback.lo `test -f 'swfdec_playback.c' || echo './'`swfdec_playback.c
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I.. -I.. -I./js/ -I../libswfdec/js -DXP_UNIX -DDEBUG -Wall -Wextra -Wno-missing-field-initializers -Wno-unused-parameter -std=c99 -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/cairo -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/alsa -pthread -DORBIT2=1 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/gconf/2 -I/usr/include/orbit-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -DG_LOG_DOMAIN=\"Swfdec-Gtk\" -DXP_UNIX -g -O2 -MT libswfdec_gtk_0.5_la-swfdec_playback.lo -MD -MP -MF .deps/libswfdec_gtk_0.5_la-swfdec_playback.Tpo -c swfdec_playback.c  -fPIC -DPIC -o .libs/libswfdec_gtk_0.5_la-swfdec_playback.o
In file included from /usr/include/alsa/asoundlib.h:51,
                 from swfdec_playback.c:24:
/usr/include/alsa/timer.h:108: error: field 'tstamp' has incomplete type
make[3]: *** [libswfdec_gtk_0.5_la-swfdec_playback.lo] Error 1
make[3]: Leaving directory `/home/startgame412/swfdec/swfdec-0.5.0/libswfdec-gtk'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/startgame412/swfdec/swfdec-0.5.0/libswfdec-gtk'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/startgame412/swfdec/swfdec-0.5.0'
make: *** [all] Error 2
startgame412@startgame412-ppc:~/swfdec/swfdec-0.5.0$

---

### Post by lambros on 2007-08-03
So it isn't just me :-)  You've hit the exact same problem (have a look near the end of your output, just above the lines beginning "make..." - that's the same error I had).

I think the best plan is to build and install a newer version of libasound (either from upstream, or from Gutsy), and do a little more research into this bug - see if it's already known about.  If I get this working, I'll post instructions here.

Lambros

---

### Post by lambros on 2007-08-04
[Edit] **Warning:** not sure how I did it, but while I was experimenting I managed to break my system.  If the same thing happens to you as what happened to me, this command should fix it:
sudo aptitude reinstall libasound2
[/Edit]


Good news: Using Gutsy's version of libasound seems to cure this problem.  With this, I've managed to successfully compile and install swfdec.

Here are the instructions - very similar to before but some of the switches are slightly different:

Create a folder somewhere, called 'alsa' (doesn't really matter what you call it).  Go here: [http://packages.ubuntu.com/gutsy/source/alsa-lib](http://packages.ubuntu.com/gutsy/source/alsa-lib)
and grab the two .gz files from the bottom of the page.  Put them into the folder you created.

Open a command-shell and 'cd' into your 'alsa' folder.  Unpack the archive and apply the diffs (again, we probably don't need to apply the diffs because it appears to patch files we're not going to use).
```
tar xf alsa-lib_1.0.14.orig.tar.gz
zcat alsa-lib_1.0.14-1ubuntu6.diff.gz | patch -p0

```

Build and install it.  This package needs the /usr/local prefix, to keep the installation separate from the rest of Ubuntu:
[Edit]The reason is so we can uninstall it without breaking Ubuntu.  See my warning at the top.  Oops! :-) [/Edit]

```
cd alsa-lib-1.0.14
./configure --prefix=/usr/local --enable-static
make
sudo make install

```

Assuming all is well, you can now go back to your swfdec folder and try to compile swfdec, using ./configure, make etc.  This time, fingers crossed, it should work :-)

Well, it worked for me, except for the "sudo make install" part.  I got a linker error, where it was trying to link something against /usr/lib/libasound.a instead of /usr/local/lib/libasound.a .  Not sure why the linker was preferring the wrong file, but I cured this by moving Ubuntu's version out of the way:

```
sudo mv /usr/lib/libasound.a /usr/lib/libsound.a.moved

```

Sorry this is all getting a bit convoluted, but hopefully we'll get there in the end :-)

Lambros

---

### Post by startgame412 on 2007-08-04
Hi, thanks for replying. When compiling wfdec, should I do ./configure --prefix=usr or just .configure? I build the previous version v 0.43 using ./configure --prefix=/usr. Thanks.

---

### Post by startgame412 on 2007-08-04
Hi I went ahead and build swfdec from source using ./configure --prefix=/usr (don't know if I was supposed to do this or not but this is what I did when I built v0.43 from source) and everything seemed to go well. I could not find the error you found when doing sudo make install. Everything seems to be fine but when I go to sites like youtube, I get the message saying to install missing plugin in firefox. How can I fix this? Thanks.

---

### Post by lambros on 2007-08-04
> **startgame412 said:**
> Hi, thanks for replying. When compiling wfdec, should I do ./configure --prefix=usr or just .configure? I build the previous version v 0.43 using ./configure --prefix=/usr. Thanks.

Good question :-)  It will work either way.  It's just a matter of personal preference which you use.  I like to keep my own software installations separate from the Ubuntu distribution.  After all, that is the intended purpose of the "/usr/local" folder on a UNIX-style system.  Most software source packages do this by default.  If you don't specify a --prefix, it will typically default to /usr/local, which is where the software will get installed when you do a "sudo make install".

It has its pros and cons though.  If you install your stuff to /usr/local, you have the confidence of knowing that you won't overwrite any system-critical files with dodgy, bleeding-edge versions.

On the other hand, if you have stuff in /usr/local, it might accidentally get used in preference to the corresponding files in /usr .  For example, if you run this command:
```
echo $PATH
```
you'll notice that /usr/local/bin appears **before** /usr/bin .  This means, in 2 or 3 years' time, your own files are **still** being used in preference to the more-up-to-date stuff in the main distribution.

So, pick your poison, and welcome to "DLL Hell"! :-)

Lambros

---

### Post by startgame412 on 2007-08-04
Hi, thanks for replying. I have managed to install both the swfdec package and the swfdec mozilla plugin package from source. However, mozilla does not seem to see the plugin. How can I get this working? Thanks.

---

### Post by lambros on 2007-08-04
You need to start mozilla or firefox with a special command-line tweak, so that it "sees" plugins that are installed under /usr/local, and not just the plugins under /usr .

Open a command-shell, and run firefox like this:

```
MOZ_PLUGIN_PATH=/usr/local/lib/mozilla-firefox/plugins firefox

```

Hopefully that should do it (you might need to use 'mozilla' instead of 'mozilla-firefox' in the plugin path).  This information is in the README file in the swfdec-mozilla package:

```
 - If you install into /usr/local, your browser may have difficulty
   finding the plugin.  This can be solved for mozilla-based
   browsers by adding /usr/local/lib/mozilla/plugins to the
   MOZ_PLUGIN_PATH environment variable.

```

Lambros

---

### Post by startgame412 on 2007-08-04
Hi, thanks for replying. I'm not sure I understand.  when compiling the swfdec mozilla plugin from source, should i run ./configure --prefix=/usr/local/lib/mozilla/plugins? What about when installing wfdec itself? Should I also install swfdec using./configure --prefix=/usr/local/lib/mozilla/plugins? Thanks.

---

### Post by startgame412 on 2007-08-04
Hi here is what happens when I ran MOZ_PLUGIN_PATH=/usr/local/lib/mozilla-firefox/plugins firefox I get some message saying the following



 Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)

I still cannot get flash sites like youtube working. It still says to install mising plugins. What should I do. Thanks.

---

### Post by lambros on 2007-08-05
> **startgame412 said:**
> Hi, thanks for replying. I'm not sure I understand.  when compiling the swfdec mozilla plugin from source, should i run ./configure --prefix=/usr/local/lib/mozilla/plugins? What about when installing wfdec itself? Should I also install swfdec using./configure --prefix=/usr/local/lib/mozilla/plugins? Thanks.

No and no.  The --prefix option is merely a top-level prefix.  Things will get installed into subfolders relative to that prefix.  For example, if I used
--prefix=/usr
Binaries would go in /usr/bin
Shared libraries would go in /usr/lib
Plugins would go in /usr/lib/mozilla[-firefox]/plugins
etc.
But if I used --prefix=/usr/local (or left it out)
Binaries would go in /usr/local/bin
Shared libraries would go in /usr/local/lib
Plugins would go in /usr/local/lib/mozilla[-firefox]/plugins
etc.
If you did happen to want finer-grained control, there are individual switches you could use to override each of these choices.  You could learn about the detailed options by running
```
./configure --help
```

Hope that clears things up a bit.
Lambros

---

### Post by lambros on 2007-08-05
> **startgame412 said:**
> Hi here is what happens when I ran MOZ_PLUGIN_PATH=/usr/local/lib/mozilla-firefox/plugins firefox I get some message saying the following

 Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
etc...


I was going to try this out for myself, but I can't download the archive swfdec-mozilla-0.5.0.tar.gz from anywhere.  The swfdec.freedesktop.org site is down at the moment, and the file doesn't seem to be anywhere else, so I can't help you much without that file, sorry! :(

Here are some things you could try:

Have a look at the README and the INSTALL file in the swfdec-mozilla package.  Maybe the instructions for 0.5.0 are slightly different from 0.4.3 which is what I have?

Does the folder /usr/local/lib/mozilla-firefox/plugins actually contain any files that look like plugins?  These files would normally end in .so .  If not, try to find where they got installed:

sudo find /usr/local -name '*.so'

If you can't find anything, there's your problem, and we need to troubleshoot why the files aren't installed.  If you can find them, maybe they're in a different place and you need to change the MOZ_PLUGIN_PATH

Maybe the plugins are there, but the permissions are wrong (this is very unlikely).  Try to run something like:

cat /path/to/plugin.so

If you get "permission denied", there's your problem.  If it works, you'll get a load of binary nonsense on the terminal (you might have to run the 'reset' command to reset your terminal).

Also, when running firefox, you could type ```
about:plugins
``` into the address-bar.  That will show you a list of all the plugins that firefox can see.  If the plugin is installed, it should appear in this list as something like "swfdec".

Check the type of the plugin with something like
```
file /path/to/plugin.so

```

Make sure the architecture is correct (for example, a 32-bit plugin will not work in a 64-bit browser).

Lambros

---

### Post by startgame412 on 2007-08-05
Hi thanks for replying.  The swfdec web stie is back up and runing. I am compiling the latest version now 0.5.1 and everything is fine but firefox does not see the plugin. The file libswfdecmozilla.so is in /usr/local/lib/mozilla/plugins directory. I ran about:plugins in the mozilla address bar and it does not list swfdecmozilla. I typed file libswfdecmozilla.so and got the following message



libswfdecmozilla.so: ELF 32-bit MSB shared object, PowerPC or cisco 4500, version 1 (SYSV), not stripped


I don't know what this means. Thanks.

---

### Post by lambros on 2007-08-06
You wrote: The file libswfdecmozilla.so is in /usr/local/lib/**mozilla**/plugins directory.
You also wrote: here is what happens when I ran MOZ_PLUGIN_PATH=/usr/local/lib/**mozilla-firefox**/plugins firefox...

That could be your problem.  Sorry I gave you the wrong command before, but you'll need to run firefox like this:
```
MOZ_PLUGIN_PATH=/usr/local/lib/mozilla/plugins firefox
```

See if this helps.  If not, watch the console output while this is running.  Wait for the output to settle down, then type
```
about:plugins
```
into the address bar, and hit Enter.  Make sure you can see the console output whilst you do this.  Do any new error-messages appear?

I've now compiled and installed the 0.5.1 versions of both swfdec and swfdec-mozilla, and the plugin works fine for me on YouTube pages, so I think we're very close now :-)

You could try running this command:
```
ldd /usr/local/lib/mozilla/plugins/libswfdecmozilla.so
```

The output should look something like this:

```

        libswfdec-gtk-0.5.so.0 => /usr/local/lib/libswfdec-gtk-0.5.so.0 (0x00002aef1ec1f000)
        libswfdec-0.5.so.0 => /usr/local/lib/libswfdec-0.5.so.0 (0x00002aef1ee29000)
        libgtk-x11-2.0.so.0 => /usr/lib/libgtk-x11-2.0.so.0 (0x00002aef1f0cd000)
        liboil-0.3.so.0 => /usr/lib/liboil-0.3.so.0 (0x00002aef1f668000)
        ...

```

Each line **must** have a valid entry on the right.  If there is just a single "not found" entry, it will fail.  You can check this automatically, with this command:

```
ldd /usr/local/lib/mozilla/plugins/libswfdecmozilla.so | grep "not found"
```

There must be no output from running this command.

Lambros

---

### Post by startgame412 on 2007-08-06
Hi thanks for replying. Running the MOZ_PLUGIN_PATH=/usr/local/lib/mozilla/plugins firefox command with firefox open returns no output. Running the command with firefox closed returns nothing either When I visit web sites I get the same output as before 



** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)


However, typing about:plugins in firefox with terminal window open causes the plugin to show up in about:plugins screen. If I close firefox,  When I went to youtube web site, firefox crashed. Should I type sudo MOZ_PLUGIN_PATH=/usr/local/lib/mozilla/plugins firefox? After this I ran ldd /usr/local/lib/mozilla/plugins/libswfdecmozilla.so and I did not get a single not found entry. I then ran ldd /usr/local/lib/mozilla/plugins/libswfdecmozilla.so | grep "not found" which gave me no output. I agree I am almost tere to get swfdec working. Just when I close firefox the plugin seems toe dissapear. Weird. Thanks.

---

### Post by lambros on 2007-08-07
> **startgame412 said:**
> Should I type sudo MOZ_PLUGIN_PATH=/usr/local/lib/mozilla/plugins firefox?

No.  Never use 'sudo' to start graphical programs.  Always use 'gksudo' in ubuntu, or 'kdesu' in kubuntu.  In any case, you shouldn't need to run firefox as root to solve this problem.

Instead, I recommend you create a new user account, log on as that user and try to run firefox there (with the same command-line as what you just used).

Sorry I can't post any more now, I'll be back later - gotta go to work! :-)

Lambros

---

### Post by startgame412 on 2007-08-07
HI , thanks for the suggestion. Unfortuneately running the command uner a different user after creating one did not work. Same thing hapens as with first username on the pc. It shouldn't be really hard to fix as teh plugin does show up in about plugins when I run the MOZ_PLUGIN_PATH=/usr/local/lib/mozilla/plugins firefox with he firefox browser closed If I go to a web site like youtube and try to play the video, the broswer will either freeze or  crash. Then when I open it back up, and go to about plugins, the plugin will not show up. Weird. Thanks.

---

### Post by lambros on 2007-08-07
I'm sorry to hear that.  You are now definitely running the correct command - the plugin shows up in the browser's list, so you've basically done everything correctly.  I would expect that:
When you run the browser with that special command, the plugin shows in the list.
When you run the browser "normally", the plugin does not appear in the list.
Am I correct?

At this stage, it **should** have worked.  If not, maybe this is because it's incompatible with the PowerPC architecture?  Maybe you're the first person to try it on PowerPC?  :-)  I think the next thing to try is: getting the standalone Flash player to work.  From your "swfdec-0.5.1" folder, run this command:

```
player/swfplay test/image/image-jpeg-alpha.swf
```

On my machine, that shows a tiny window with a coloured image (I have to resize the window to see it properly).  Try this command with other .swf files on your PC.  This command might help you find some examples:

```
slocate .swf
```

I'm not sure what else you can do from here.  You said you compiled swfdec0.4.3 using --prefix=/usr .  It's possible you might have overwritten some Ubuntu files, and it's possible these are still getting linked against.  That would certainly cause problems if true.  Also, you might be linking against the wrong libraries (/usr/lib/something.so instead of /usr/local/lib/something.so)

If you want, you could try starting from a completely clean slate, like this:

Reinstall any Ubuntu packages you might have accidentally damaged:
```
sudo aptitude reinstall ffmpeg libasound2 libasound2-dev libavcodec0d libavcodec-dev libavformat0d

```
(those are the only ones I can think of - you might have some others as well)

Remove everything from /usr/local (assuming you haven't installed any non-Ubuntu software you want to keep in there - you'll have to use your best judgement).  In a default Ubuntu installation, the /usr/local folder will be completely empty.

Delete all your source folders, and recreate them from the *.gz packages you downloaded.

Rebuild everything, following my instructions.  Make sure everything gets installed underneath /usr/local, and nothing goes in /usr/anywhere-else .

That might improve the situation.  Failing that, you might have to contact the swfdec developers somehow (read their website for guidelines on how to do this).  If you need to, you can refer them to this thread.

Lambros

---

### Post by startgame412 on 2007-08-08
Hi, thanks for replying. Yes you are correct.  When I run the browser normally the plugin does not apear.  Do you know if there is someway I can save this topic for future reference?  Like you said I might have screwed things up by installed swfdec 0.4.x in /usr/lib  I did hte command that you indicated and yes indded the standalone flash player works. I'm am not sure if this is related but I have a weird problem. I folder that is in my called libswfdec will not delete from the trash  When I try to delete it, I get a message saying /home/start...ingbuffer.o" cannot be deleted because you do not have permissions to modify its parent folder. Could this be the problem?  By the name I take it it is related to swfdec. albout swfdec is installed and running fine. Only the plugin not working properly.  I'm going ot be away for a while and would like ot save this thread for when I resume working on trying ot get this working. How to ave this thread? Thanks.

---

### Post by lambros on 2007-08-08
To save this thread, you could bookmark it in your browser.  This should work as a permanent link to this thread:
[http://ubuntuforums.org/showthread.php?t=509430](http://ubuntuforums.org/showthread.php?t=509430)

I'm sure it will stay around long enough, at least until Gutsy is released.  Or you could subscribe to this thread.  I think it's under "Thread Tools" near the top of this page.

For your problem with deleting files, it sounds like you've accidentally run something as root when you shouldn't have.  Perhaps you accidentally did a 'sudo make' instead of 'make', or maybe you ran a graphical program with 'sudo'?  Try running this command from a terminal (make sure you're logged in as yourself, not root!)

```
sudo chown -R $USERNAME:$USERNAME $HOME
```

It might take a couple of minutes, but it will make sure your personal files are actually "owned" by you.  That will probably fix your permission problems.  If not, post again, and we'll do a more detailed repair :-)

Lambros

---

### Post by startgame412 on 2007-08-09
Thank you. The command sudo chown -R $USERNAME:$USERNAME $HOME worked  I thought one must install programs by typing sudo make install. Do you think that not being able to delete the libswfdec folder from the trash has anything to do with the plugin not working the way it is supposed to? Thanks.

---

### Post by lambros on 2007-08-09
> **startgame412 said:**
> Thank you. The command sudo chown -R $USERNAME:$USERNAME $HOME worked  I thought one must install programs by typing sudo make install. Do you think that not being able to delete the libswfdec folder from the trash has anything to do with the plugin not working the way it is supposed to? Thanks.

Sorry if that confused you.  Hope this clarifies:

[COLOR="DarkOrchid"]make install[/COLOR] <-- WRONG, will complain "Permission denied"
[COLOR="DarkOrchid"]sudo make install[/COLOR] <-- CORRECT, installation requires root privileges
[COLOR="DarkOrchid"]make[/COLOR] <-- CORRECT, compiling should be done as a normal user
[COLOR="DarkOrchid"]sudo make[/COLOR] <-- WRONG, will create files/folders with root ownership, preventing normal user from modifying/deleting them

In answer to your last question: no, I doubt it.  I think if the files had wrong ownership, and it was affecting the plugin, I think it would have shown an error-message on the terminal where you typed that special command to run firefox.

I'm afraid your problem is mysterious to me, I'm not sure what you can do about it.  But I've thought of something else you could try:
Maybe there is a strange interaction between your swfdec plugin and some other firefox plugin you have installed?  Try uninstalling any other plugins you've added, such as Java, RealPlayer, AdobeReader, QuickTime, and anything else.  Try to get Firefox down to its bare bones, the way it was when you originally installed Ubuntu.  See if that helps.

Otherwise, here's a Web site that explains how to debug Firefox problems: [http://wiki.ubuntu.com/DebuggingFirefox](http://wiki.ubuntu.com/DebuggingFirefox)

You could try the suggestions there - perhaps they might shed light on your problem.  It will help you if you run the command:
```
export MOZ_PLUGIN_PATH=/usr/local/lib/mozilla/plugins
```
before doing any of the commands suggested on that web page.  That will make the setting "permanent" within that terminal window, so that Firefox will "see" the swfdec plugin whenever it is run from that same terminal window.

Also, whenever you run a test with Firefox, always close any running instances first.  Otherwise the results may be confusing and unpredictable.  Firefox tries to "recycle" any instances it finds already running.  That would interfere with your tests.

Sorry if any of this is confusing.  It will become clearer as you gain more experience with how GNU/Linux works.

Lambros

---

### Post by startgame412 on 2007-08-10
Hi thanks for the clarification. I do have other plugins installed with firefox. I currently have java, divx web player totem web browser plugin and windows media player plugin 10 (compatible; Totem) Any of these plugins you think could interfere with swfdec mozilla plugin?  I'm not sure on how to uninstall them. How do I do so? Thanks.

---

### Post by lambros on 2007-08-10
> **startgame412 said:**
> Hi thanks for the clarification. I do have other plugins installed with firefox. I currently have java, divx web player totem web browser plugin and windows media player plugin 10 (compatible; Totem) Any of these plugins you think could interfere with swfdec mozilla plugin?  I'm not sure on how to uninstall them. How do I do so? Thanks.

I think you're OK with those.  I have all those as well, yet the swfdec plugin works fine on my system.  Would be nice if there was a way of running Firefox such that it only loads the swfdec plugin.  I don't know how, off the top of my head.

If I were in your shoes, I would try to find what's causing Firefox to crash without any sort of error message whatsoever.  That's very unusual in my experience of GNU/Linux.  Usually when something dies, it leaves some sort of message behind; in most cases it involves 'sigsegv' :-)  I would try running Firefox under the 'gdb' debugger, or use 'strace' to get an idea of what's wrong.

If I have any more ideas, I'll post them here.  Meanwhile, your best bet is to use that link I posted earlier and follow their suggestions.

Lambros

---

### Post by bwtranch on 2007-08-10
sudo apt-get install build-essential

Get back to me if there are any other problems. Which I doubt.

---

### Post by startgame412 on 2007-08-11
Hi thanks for replying. I already have build\essintial package installed. Thanks.

---

