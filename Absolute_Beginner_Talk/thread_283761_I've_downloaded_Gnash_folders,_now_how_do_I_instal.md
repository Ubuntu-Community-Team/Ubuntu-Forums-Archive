---
title: "I've downloaded Gnash folders, now how do I install it?"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by Kouki on 2006-10-24
Hi, I'm used to installing all my programs through synaptic package mangager, but Gnash isn't on there.  Therefore I'm trying to work out how on earth you install something that isn't on there.

I've downloaded all these files [ftp://ftp.mcc.ac.uk/pub/gnu/gnash/0.7.1](ftp://ftp.mcc.ac.uk/pub/gnu/gnash/0.7.1) and extracted them to my desktop.

Whats the process for installing these tar files.  I've searched, but cannot find exactly what to do.

Any help would be great.  At present I can't watch any online videos.

---

### Post by bsussman on 2006-10-24
Either tar file, only 1 of which you need, when unpacked, containd a README and an INSTALL file - these give instructions for building and installing.

This is a source distribution, which is why you need to build the executables.

---

### Post by Kouki on 2006-10-24
> **bsussman said:**
> Either tar file, only 1 of which you need, when unpacked, containd a README and an INSTALL file - these give instructions for building and installing.

This is a source distribution, which is why you need to build the executables.

Thanks, cool so that's how you install downloaded applications, very useful, I'm not used to reading the readme files from windows.

I've followed it through but encountered a problem... typical, why do these things never work first time for me?

Here is exactly what I typed in the console, and the result:

stuart@stuart-desktop:~$ cd /home/stuart/Desktop/gnash-0.7.1
stuart@stuart-desktop:~/Desktop/gnash-0.7.1$ ./configure
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking whether make sets $(MAKE)... (cached) yes
checking for pkg-config... yes
checking for kde-config... /usr/bin/kde-config
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for style of include used by make... GNU
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking for C++ compiler default output file name... configure: error: C++ compiler cannot create executables
See `config.log' for more details.
stuart@stuart-desktop:~/Desktop/gnash-0.7.1$ make
make: *** No targets specified and no makefile found. Stop.
stuart@stuart-desktop:~/Desktop/gnash-0.7.1$


Surely that should have worked? ](*,)

---

### Post by TitusDalwards on 2006-10-24
> **Kouki said:**
> Thanks, cool so that's how you install downloaded applications, very useful, I'm not used to reading the readme files from windows.

I've followed it through but encountered a problem... typical, why do these things never work first time for me?

Here is exactly what I typed in the console, and the result:

stuart@stuart-desktop:~$ cd /home/stuart/Desktop/gnash-0.7.1
stuart@stuart-desktop:~/Desktop/gnash-0.7.1$ ./configure
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking whether make sets $(MAKE)... (cached) yes
checking for pkg-config... yes
checking for kde-config... /usr/bin/kde-config
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for style of include used by make... GNU
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking for C++ compiler default output file name... configure: error: C++ compiler cannot create executables
See `config.log' for more details.
stuart@stuart-desktop:~/Desktop/gnash-0.7.1$ make
make: *** No targets specified and no makefile found. Stop.
stuart@stuart-desktop:~/Desktop/gnash-0.7.1$


Surely that should have worked? ](*,)
```
sudo aptitude install build-essential
```

your system has'nt got C compiler by this command you can install it.

---

### Post by Kouki on 2006-10-24
> **TitusDalwards said:**
> ```
sudo aptitude install build-essential
```

your system has'nt got C compiler by this command you can install it.


Thanks, ./configure did a lot more once that was installed.

However at the end it gave the following errors:

ERROR: No OGG Vorbis development package installed!
        Opengl flags are: default include path
        Opengl libs are: -lopengl32 -lglu32
        Xft flags are: -I/usr/include/X11
        Xft libs are: -lXft
ERROR: No SDL development package installed! You need to have the SDL development package installed to compile, or install libsdl1.2-dev (using apt-get) or SDL-devel (using yum).
ERROR: No SDL_Mixer development package installed! You need to have the SDL Mixer development package installed to compile this project with SDL sound support or install libsdl-mixer1.2-dev (using apt-get) or SDL_mixer-devel (using yum).
        Plugin will be installed in /home/stuart/.firefox/plugins
        POSIX Threads flags are: -I/usr/include
        POSIX Threads lib is: -lpthread

configure: error: Please install required packages


Having then typed 'make'
followed by 'make install'

I can confirm that I received a lot of errors and I still can't stream online video's in ubuntu.  I feel I'm getting closer now though, thanks for the advice.

---

### Post by TitusDalwards on 2006-10-24
after ./configure you got some errors but by the time you got the solution, for example:
**ERROR: No SDL development package installed! You need to have the SDL development package installed to compile, or install libsdl1.2-dev (using apt-get) or SDL-devel (using yum).**

try to install all required packages by using APT.

---

### Post by Kouki on 2006-10-24
Right, worked out how to install some of those missing things using SPM.

Latest error is this, putting it up also for my own use, so that I can see what I need if I accidently shut the console which I have a habit of doing.

Configurable options are:
        Intel 810 LOD bias hack disabled (default). Use --enable-i810-lod-bias to enable.
        MP3 (libmad) support disabled (default). Use --enable-mp3 to enable
        POSIX Threads support enabled (default)
        Web server support disabled (default)
        DMalloc support disabled (default). Use --enable-dmalloc to enable.
        XML and XMLSocket enabled (default). Use --disble-xml to disable.
        Firefox plugin enabled (default). Use --disble-plugin to disable.
        Konqueror plugin disabled (default). Use --enable-klash to enable.
        GNOME help disabled (default). Use --enable-ghelp to enable.
        Unit testing support enabled (default)

Configured paths for x86_64-unknown-linux-gnu are:
        DocBook document processing disabled (default)
        ERROR: No libxml2 development package installed!
               Reconfigure with --disable-xml to continue
        PNG flags are: default include path
        PNG libs are: -lpng
        JPEG flags are: default include path
        JPEG libs are: -ljpeg
        OGG flags are: default include path
        OGG libs are: -logg
        Opengl flags are: default include path
        Opengl libs are: -lGL -lGLU
        Xft flags are: -I/usr/include/X11
        Xft libs are: -lXft
        SDL flags are: -I/usr/include/SDL
        SDL libs are: -lSDL
        SDL_Mixer flags are: -I/usr/include/SDL
        SDL_Mixer libs are: -L/usr/lib64 -lSDL_mixer
        Plugin will be installed in /home/stuart/.firefox/plugins
        POSIX Threads flags are: -I/usr/include
        POSIX Threads lib is: -lpthread

configure: error: Please install required packages

---

### Post by Kouki on 2006-10-24
Ok, I think I found everything I needed.

This ./configure result seems better.

stuart@stuart-desktop:~/Desktop/gnash-0.7.1$ ./configure
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking whether make sets $(MAKE)... (cached) yes
checking for pkg-config... yes
checking for kde-config... /usr/bin/kde-config
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for style of include used by make... GNU
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking if C++ programs can be compiled... yes
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
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
checking for strlcat... no
checking if strlcat needs custom prototype... yes - in libkdefakes
checking for strlcpy... no
checking if strlcpy needs custom prototype... yes - in libkdefakes
checking for main in -lutil... yes
checking for main in -lcompat... no
checking for crypt in -lcrypt... yes
checking for socklen_t... yes
checking for dnet_ntoa in -ldnet... no
checking for dnet_ntoa in -ldnet_stub... no
checking for inet_ntoa... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for sys/types.h... (cached) yes
checking for stdint.h... (cached) yes
checking sys/bitypes.h usability... yes
checking sys/bitypes.h presence... yes
checking for sys/bitypes.h... yes
checking for poll in -lpoll... no
checking Carbon/Carbon.h usability... no
checking Carbon/Carbon.h presence... no
checking for Carbon/Carbon.h... no
checking CoreAudio/CoreAudio.h usability... no
checking CoreAudio/CoreAudio.h presence... no
checking for CoreAudio/CoreAudio.h... no
checking if res_init needs -lresolv... yes
checking for res_init... yes
checking if res_init needs custom prototype... no
checking for killpg in -lucb... no
checking for int... yes
checking size of int... 4
checking for short... yes
checking size of short... 2
checking for long... yes
checking size of long... 8
checking for char *... yes
checking size of char *... 8
checking for dlopen in -ldl... yes
checking for shl_unload in -ldld... no
checking for size_t... yes
checking size of size_t... 8
checking for unsigned long... yes
checking size of unsigned long... 8
checking sizeof size_t == sizeof unsigned long... yes
checking crt_externs.h usability... no
checking crt_externs.h presence... no
checking for crt_externs.h... no
checking for _NSGetEnviron... no
checking for vsnprintf... yes
checking for snprintf... yes
not using lib directory suffix
checking for X... libraries /usr/X11R6/lib, headers .
checking for IceConnectionNumber in -lICE... yes
checking for libXext... yes
checking for pthread_create in -lpthread... yes
checking for extra includes...
checking for zlib header... /usr/include
checking for zlib library... /usr/lib64
checking for libpng... -lpng -L/usr/lib64 -lz -lm
checking for libjpeg6b... no
checking for libjpeg... no
checking for perl... /usr/bin/perl
checking for Qt... configure: Qt (headers and libraries) not found.
no
yes
checking for rpath... yes
checking for KDE... configure: no KDE headers installed.
configure: no KDE libraries installed.
will be installed in /usr/local
checking for KDE paths... defaults
checking for xml2-config... /usr/bin/xml2-config
checking for libxml2... yes
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking whether we are using the GNU C++ compiler... (cached) yes
checking whether g++ accepts -g... (cached) yes
checking dependency style of g++... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c -p
checking for library file name specifics... no
checking for mallinfo... yes
checking for X... libraries /usr/X11R6/lib, headers .
checking for gethostbyname... yes
checking for connect... (cached) yes
checking for remove... (cached) yes
checking for shmat... (cached) yes
checking for IceConnectionNumber in -lICE... (cached) yes
checking dejagnu.h usability... no
checking dejagnu.h presence... no
checking for dejagnu.h... no
checking for XmuCvtStringToOrientation in -lXmu... yes
checking for XInput_find_display in -lXi... yes
checking for XDisableAccessControl in -lX11... yes
checking for shm_unlink in -lrt... yes
checking for shm_open... yes
checking for strcasecmp... yes
checking for stricmp... no
checking for vsnprintf... (cached) yes
checking for finite... yes
checking for isfinite... no
checking for sysconf... yes
checking for shmget... yes
checking for shmat... (cached) yes
checking for mmap... yes
checking for gettimeofday... yes
checking winsock.h usability... no
checking winsock.h presence... no
checking for winsock.h... no
checking for socket... yes
checking for CreateFileMappingA... no
checking how to run the C++ preprocessor... g++ -E
checking ext/hash_map usability... yes
checking ext/hash_map presence... yes
checking for ext/hash_map... yes
(cached) checking for zlib header... /usr/include
checking for zlib library... (cached) checking jpeglib.h usability... no
checking jpeglib.h presence... no
checking for jpeglib.h... no
checking for libjpeg header... checking for jpeg_mem_init in -ljpeg... no
checking for libjpeg library... checking for png.h header in specified directory... no
checking png.h usability... yes
checking png.h presence... yes
checking for png.h... yes
checking for png_check_sig in -lpng... yes
checking for ming-config... no
checking for doxygen... no
checking ogg.h usability... no
checking ogg.h presence... no
checking for ogg.h... no
checking for libogg header... checking for ogg_sync_init in -logg... yes
checking for the SDL Version... checking for SDL header... /usr/include/SDL
checking for sdl library... checking for SDL_Init in -lSDL... yes
checking for SDL_mixer header... /usr/include/SDL
checking for sdl_mixer library... checking for Mix_Linked_Version in -lSDL_mixer... yes
checking for Mix_Linked_Version in -lSDL_mixer-1.2... no
checking for SDL_mixer library... checking for the Gstreamer Version... none
checking gst/gst.h usability... no
checking gst/gst.h presence... no
checking for gst/gst.h... no
checking for libgstreamer header... checking GL/gl.h usability... yes
checking GL/gl.h presence... yes
checking for GL/gl.h... yes
checking for glBegin in -lGL... yes
checking for the Gtk GL Extensions Version... none
checking gtk/gtkgl.h usability... no
checking gtk/gtkgl.h presence... no
checking for gtk/gtkgl.h... no
checking for libglext header... checking for fltk.h header in specified directory... no
checking fltk/FL_API.h usability... no
checking fltk/FL_API.h presence... no
checking for fltk/FL_API.h... no
checking for libfltk header... checking for fl_xmap in -lfltk... no
checking for libfltk library... checking for xft.h header in specified directory... no
checking Xft/Xft.h usability... no
checking Xft/Xft.h presence... no
checking for Xft/Xft.h... no
checking for libxft header... checking for XftGlyphRender in -lXft... yes
checking cairo/cairo.h usability... no
checking cairo/cairo.h presence... no
checking for cairo/cairo.h... no
checking for Cairo header... yes
checking for cairo_status in -lcairo... yes
checking for pthread.h... no
checking for libpthread header... yes
checking for pthread_kill in -lpthread... yes
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
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
configure: creating ./config.status
config.status: creating Makefile
config.status: creating libbase/Makefile
config.status: creating libgeometry/Makefile
config.status: creating server/Makefile
config.status: creating libamf/Makefile
config.status: creating backend/Makefile
config.status: creating utilities/Makefile
config.status: creating doc/Makefile
config.status: creating doc/C/Makefile
config.status: creating doc/Doxyfile
config.status: creating testsuite/Makefile
config.status: creating testsuite/actionscript.all/Makefile
config.status: creating plugin/Makefile
config.status: creating plugin/klash/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands

Configurable options are:
        Intel 810 LOD bias hack disabled (default). Use --enable-i810-lod-bias to enable.
        MP3 (libmad) support disabled (default). Use --enable-mp3 to enable
        POSIX Threads support enabled (default)
        Web server support disabled (default)
        DMalloc support disabled (default). Use --enable-dmalloc to enable.
        XML and XMLSocket enabled (default). Use --disble-xml to disable.
        Firefox plugin enabled (default). Use --disble-plugin to disable.
        Konqueror plugin disabled (default). Use --enable-klash to enable.
        GNOME help disabled (default). Use --enable-ghelp to enable.
        Unit testing support enabled (default)

Configured paths for x86_64-unknown-linux-gnu are:
        DocBook document processing disabled (default)
        XML flags are: -I/usr/include/libxml2
        XML libs are: -L/usr/lib -lxml2 -lz -lm
        PNG flags are: default include path
        PNG libs are: -lpng
        JPEG flags are: default include path
        JPEG libs are: -ljpeg
        OGG flags are: default include path
        OGG libs are: -logg
        Opengl flags are: default include path
        Opengl libs are: -lGL -lGLU
        Xft flags are: -I/usr/include/X11
        Xft libs are: -lXft
        SDL flags are: -I/usr/include/SDL
        SDL libs are: -lSDL
        SDL_Mixer flags are: -I/usr/include/SDL
        SDL_Mixer libs are: -L/usr/lib64 -lSDL_mixer
        Plugin will be installed in /home/stuart/.firefox/plugins
        POSIX Threads flags are: -I/usr/include
        POSIX Threads lib is: -lpthread
stuart@stuart-desktop:~/Desktop/gnash-0.7.1$





However, when I type 'make' I get this:

stuart@stuart-desktop:~/Desktop/gnash-0.7.1$ make
make  all-recursive
make[1]: Entering directory `/home/stuart/Desktop/gnash-0.7.1'
Making all in libbase
make[2]: Entering directory `/home/stuart/Desktop/gnash-0.7.1/libbase'
if /bin/sh ../libtool --mode=compile --tag=CXX g++ -DHAVE_CONFIG_H -I. -I. -I.. -I.. -I. -I.. -I../server -I/usr/include  -I/usr/include/libxml2  -I/usr/include/SDL -I/usr/include/SDL    -DQT_THREAD_SUPPORT  -D_REENTRANT -I.. -I. -I.. -I../server -I/usr/include  -I/usr/include/libxml2  -I/usr/include/SDL -I/usr/include/SDL   -g -O2 -Wall -MT jpeg.lo -MD -MP -MF ".deps/jpeg.Tpo" -c -o jpeg.lo jpeg.cpp; \
        then mv -f ".deps/jpeg.Tpo" ".deps/jpeg.Plo"; else rm -f ".deps/jpeg.Tpo"; exit 1; fi
 g++ -DHAVE_CONFIG_H -I. -I. -I.. -I.. -I. -I.. -I../server -I/usr/include -I/usr/include/libxml2 -I/usr/include/SDL -I/usr/include/SDL -DQT_THREAD_SUPPORT -D_REENTRANT -I.. -I. -I.. -I../server -I/usr/include -I/usr/include/libxml2 -I/usr/include/SDL -I/usr/include/SDL -g -O2 -Wall -MT jpeg.lo -MD -MP -MF .deps/jpeg.Tpo -c jpeg.cpp  -fPIC -DPIC -o .libs/jpeg.o
jpeg.cpp:18:21: error: jpeglib.h: No such file or directory
jpeg.cpp:37: error: field 'm_pub' has incomplete type
jpeg.cpp:41: error: 'JOCTET' does not name a type
jpeg.cpp:60: error: 'j_decompress_ptr' has not been declared
jpeg.cpp:66: error: 'boolean' does not name a type
jpeg.cpp:111: error: 'j_decompress_ptr' has not been declared
jpeg.cpp:131: error: 'j_decompress_ptr' has not been declared
jpeg.cpp: In constructor 'jpeg::rw_source::rw_source(tu_file*)':
jpeg.cpp:51: error: 'm_pub' was not declared in this scope
jpeg.cpp:52: error: 'fill_input_buffer' was not declared in this scope
jpeg.cpp:54: error: 'jpeg_resync_to_restart' was not declared in this scope
jpeg.cpp: In static member function 'static void jpeg::rw_source::init_source(int)':
jpeg.cpp:62: error: base operand of '->' is not a pointer
jpeg.cpp: In static member function 'static void jpeg::rw_source::skip_input_data(int, long int)':
jpeg.cpp:115: error: base operand of '->' is not a pointer
jpeg.cpp:121: error: 'struct jpeg::rw_source' has no member named 'm_pub'
jpeg.cpp:122: error: 'struct jpeg::rw_source' has no member named 'm_pub'
jpeg.cpp:123: error: 'fill_input_buffer' was not declared in this scope
jpeg.cpp:126: error: 'struct jpeg::rw_source' has no member named 'm_pub'
jpeg.cpp:127: error: 'struct jpeg::rw_source' has no member named 'm_pub'
jpeg.cpp: In member function 'void jpeg::rw_source::discard_partial_buffer()':
jpeg.cpp:151: error: 'm_pub' was not declared in this scope
jpeg.cpp: In function 'void jpeg::setup_rw_source(jpeg_decompress_struct*, tu_file*)':
jpeg.cpp:162: error: invalid use of undefined type 'struct jpeg_decompress_struct'
jpeg.h:15: error: forward declaration of 'struct jpeg_decompress_struct'
jpeg.cpp: At global scope:
jpeg.cpp:170: error: field 'm_pub' has incomplete type
jpeg.cpp:173: error: 'JOCTET' does not name a type
jpeg.cpp:190: error: 'j_compress_ptr' has not been declared
jpeg.cpp:199: error: 'boolean' does not name a type
jpeg.cpp:218: error: 'j_compress_ptr' has not been declared
jpeg.cpp: In constructor 'jpeg::rw_dest::rw_dest(tu_file*)':
jpeg.cpp:182: error: 'm_pub' was not declared in this scope
jpeg.cpp:183: error: 'empty_output_buffer' was not declared in this scope
jpeg.cpp:186: error: 'm_buffer' was not declared in this scope
jpeg.cpp: In static member function 'static void jpeg::rw_dest::init_destination(int)':
jpeg.cpp:192: error: base operand of '->' is not a pointer
jpeg.cpp:195: error: 'struct jpeg::rw_dest' has no member named 'm_pub'
jpeg.cpp:195: error: 'struct jpeg::rw_dest' has no member named 'm_buffer'
jpeg.cpp:196: error: 'struct jpeg::rw_dest' has no member named 'm_pub'
jpeg.cpp: In static member function 'static void jpeg::rw_dest::term_destination(int)':
jpeg.cpp:222: error: base operand of '->' is not a pointer
jpeg.cpp:226: error: 'struct jpeg::rw_dest' has no member named 'm_pub'
jpeg.cpp:228: error: 'struct jpeg::rw_dest' has no member named 'm_buffer'
jpeg.cpp:237: error: base operand of '->' is not a pointer
jpeg.cpp: At global scope:
jpeg.cpp:242: error: variable or field 'setup_rw_dest' declared void
jpeg.cpp:242: error: 'int jpeg::setup_rw_dest' redeclared as different kind of symbol
jpeg.cpp:27: error: previous declaration of 'void jpeg::setup_rw_dest(jpeg_compress_struct*, tu_file*)'
jpeg.cpp:242: error: 'j_compress_ptr' was not declared in this scope
jpeg.cpp:242: error: expected primary-expression before '*' token
jpeg.cpp:242: error: 'outstream' was not declared in this scope
jpeg.cpp:255: error: variable or field 'jpeg_error_exit' declared void
jpeg.cpp:255: error: 'j_common_ptr' was not declared in this scope
jpeg.cpp:257: error: expected ',' or ';' before '{' token
jpeg.cpp:264: error: variable or field 'setup_jpeg_err' declared void
jpeg.cpp:264: error: 'jpeg_error_mgr' was not declared in this scope
jpeg.cpp:264: error: 'jerr' was not declared in this scope
jpeg.cpp:266: error: expected ',' or ';' before '{' token
jpeg.cpp:284: error: field 'm_cinfo' has incomplete type
jpeg.cpp:285: error: field 'm_jerr' has incomplete type
jpeg.cpp: In constructor 'jpeg::input_impl::input_impl(tu_file*)':
jpeg.cpp:299: error: 'm_jerr' was not declared in this scope
jpeg.cpp:299: error: 'jpeg::setup_jpeg_err' cannot be used as a function
jpeg.cpp:300: error: 'm_cinfo' was not declared in this scope
jpeg.cpp:303: error: 'jpeg_create_decompress' was not declared in this scope
jpeg.cpp: In constructor 'jpeg::input_impl::input_impl(jpeg::input_impl::SWF_DEFINE_BITS_JPEG2_HEADER_ONLY, tu_file*)':
jpeg.cpp:321: error: 'm_jerr' was not declared in this scope
jpeg.cpp:321: error: 'jpeg::setup_jpeg_err' cannot be used as a function
jpeg.cpp:322: error: 'm_cinfo' was not declared in this scope
jpeg.cpp:325: error: 'jpeg_create_decompress' was not declared in this scope
jpeg.cpp:330: error: 'FALSE' was not declared in this scope
jpeg.cpp:330: error: 'jpeg_read_header' was not declared in this scope
jpeg.cpp: In destructor 'virtual jpeg::input_impl::~input_impl()':
jpeg.cpp:341: error: 'm_cinfo' was not declared in this scope
jpeg.cpp:346: error: 'jpeg_destroy_decompress' was not declared in this scope
jpeg.cpp: In member function 'virtual void jpeg::input_impl::discard_partial_buffer()':
jpeg.cpp:355: error: 'm_cinfo' was not declared in this scope
jpeg.cpp: In member function 'virtual void jpeg::input_impl::start_image()':
jpeg.cpp:379: error: 'm_cinfo' was not declared in this scope
jpeg.cpp:379: error: 'FALSE' was not declared in this scope
jpeg.cpp:379: error: 'jpeg_read_header' was not declared in this scope
jpeg.cpp:380: error: 'JPEG_HEADER_TABLES_ONLY' was not declared in this scope
jpeg.cpp:381: error: 'JPEG_HEADER_OK' was not declared in this scope
jpeg.cpp:383: error: 'm_cinfo' was not declared in this scope
jpeg.cpp:383: error: 'jpeg_start_decompress' was not declared in this scope
jpeg.cpp: In member function 'virtual void jpeg::input_impl::finish_image()':
jpeg.cpp:391: error: 'm_cinfo' was not declared in this scope
jpeg.cpp:391: error: 'jpeg_finish_decompress' was not declared in this scope
jpeg.cpp: In member function 'virtual int jpeg::input_impl::get_height() const':jpeg.cpp:400: error: 'm_cinfo' was not declared in this scope
jpeg.cpp: In member function 'virtual int jpeg::input_impl::get_width() const':
jpeg.cpp:407: error: 'm_cinfo' was not declared in this scope
jpeg.cpp: In member function 'int jpeg::input_impl::get_components() const':
jpeg.cpp:416: error: 'm_cinfo' was not declared in this scope
jpeg.cpp: In member function 'virtual void jpeg::input_impl::read_scanline(unsigned char*)':
jpeg.cpp:426: error: 'm_cinfo' was not declared in this scope
jpeg.cpp:427: error: 'jpeg_read_scanlines' was not declared in this scope
jpeg.cpp:431: error: 'JCS_GRAYSCALE' was not declared in this scope
jpeg.cpp: At global scope:
jpeg.cpp:473: error: field 'm_cinfo' has incomplete type
jpeg.cpp:474: error: field 'm_jerr' has incomplete type
jpeg.cpp: In constructor 'jpeg::output_impl::output_impl(tu_file*, int, int, int)':
jpeg.cpp:480: error: 'm_cinfo' was not declared in this scope
jpeg.cpp:480: error: 'm_jerr' was not declared in this scope
jpeg.cpp:480: error: 'jpeg_std_error' was not declared in this scope
jpeg.cpp:483: error: 'jpeg_create_compress' was not declared in this scope
jpeg.cpp:489: error: 'JCS_RGB' was not declared in this scope
jpeg.cpp:490: error: 'jpeg_set_defaults' was not declared in this scope
jpeg.cpp:491: error: 'TRUE' was not declared in this scope
jpeg.cpp:491: error: 'jpeg_set_quality' was not declared in this scope
jpeg.cpp:493: error: 'jpeg_start_compress' was not declared in this scope
jpeg.cpp: In destructor 'virtual jpeg::output_impl::~output_impl()':
jpeg.cpp:500: error: 'm_cinfo' was not declared in this scope
jpeg.cpp:500: error: 'jpeg_finish_compress' was not declared in this scope
jpeg.cpp:506: error: 'jpeg_destroy_compress' was not declared in this scope
jpeg.cpp: In member function 'virtual void jpeg::output_impl::write_scanline(unsigned char*)':
jpeg.cpp:513: error: 'm_cinfo' was not declared in this scope
jpeg.cpp:513: error: 'jpeg_write_scanlines' was not declared in this scope
make[2]: *** [jpeg.lo] Error 1
make[2]: Leaving directory `/home/stuart/Desktop/gnash-0.7.1/libbase'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/stuart/Desktop/gnash-0.7.1'
make: *** [all] Error 2
stuart@stuart-desktop:~/Desktop/gnash-0.7.1$


Which is full of errors, but no hints as to what programs are needed to fix them.

---

### Post by Kouki on 2006-10-24
Ok, although I'm no professional, hopefully this can help people - it would certainly help me had this thread been here when I started.

Basically 'make' wasn't working because I was missing:

libjpeg and libjpeg-devel

Installing these using SPM seems to have fixed the 'make' problem.  Lets see what goes wrong next (console is still going through the make command)

---

### Post by Kouki on 2006-10-24
Ok, I think it worked.  If following the readme you type 'make install' and get an error, this can be solved by typing 'sudo make install' instead.

I think it's installed now, thanks for the help everyone :D 

Just to verify, this is my final screen in console, does this mean the installation was a success?

stuart@stuart-desktop:~/Desktop/gnash-0.7.1$ sudo make install
Password:
Making install in libbase
make[1]: Entering directory `/home/stuart/Desktop/gnash-0.7.1/libbase'
make[2]: Entering directory `/home/stuart/Desktop/gnash-0.7.1/libbase'
test -z "/usr/local/lib" || mkdir -p -- "/usr/local/lib"
 /bin/sh ../libtool --mode=install /usr/bin/install -c -p  'libgnashbase.la' '/usr/local/lib/libgnashbase.la'
/usr/bin/install -c -p .libs/libgnashbase.so.0.0.0 /usr/local/lib/libgnashbase.so.0.0.0
(cd /usr/local/lib && { ln -s -f libgnashbase.so.0.0.0 libgnashbase.so.0 || { rm -f libgnashbase.so.0 && ln -s libgnashbase.so.0.0.0 libgnashbase.so.0; }; })
(cd /usr/local/lib && { ln -s -f libgnashbase.so.0.0.0 libgnashbase.so || { rm -f libgnashbase.so && ln -s libgnashbase.so.0.0.0 libgnashbase.so; }; })
/usr/bin/install -c -p .libs/libgnashbase.lai /usr/local/lib/libgnashbase.la
/usr/bin/install -c -p .libs/libgnashbase.a /usr/local/lib/libgnashbase.a
ranlib /usr/local/lib/libgnashbase.a
chmod 644 /usr/local/lib/libgnashbase.a
PATH="$PATH:/sbin" ldconfig -n /usr/local/lib
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/stuart/Desktop/gnash-0.7.1/libbase'
make[1]: Leaving directory `/home/stuart/Desktop/gnash-0.7.1/libbase'
Making install in libgeometry
make[1]: Entering directory `/home/stuart/Desktop/gnash-0.7.1/libgeometry'
make[2]: Entering directory `/home/stuart/Desktop/gnash-0.7.1/libgeometry'
test -z "/usr/local/lib" || mkdir -p -- "/usr/local/lib"
 /bin/sh ../libtool --mode=install /usr/bin/install -c -p  'libgnashgeo.la' '/usr/local/lib/libgnashgeo.la'
libtool: install: warning: relinking `libgnashgeo.la'
(cd /home/stuart/Desktop/gnash-0.7.1/libgeometry; /bin/sh ../libtool  --tag=CXX --mode=relink g++ -g -O2 -Wall -I/usr/include/SDL -I.. -I. -I.. -I../libbase -I/usr/include -I/usr/include/SDL -g -O2 -Wall -o libgnashgeo.la -rpath /usr/local/lib axial_box.lo bsp.lo collision.lo cull.lo geometry.lo kd_tree_dynamic.lo kd_tree_packed.lo tqt.lo -L../libbase -lgnashbase -lSDL_mixer -lrt -lX11 -lXi -lXmu )
g++ -shared -nostdlib /usr/lib/gcc/x86_64-linux-gnu/4.0.3/../../../../lib64/crti.o /usr/lib/gcc/x86_64-linux-gnu/4.0.3/crtbeginS.o  .libs/axial_box.o .libs/bsp.o .libs/collision.o .libs/cull.o .libs/geometry.o .libs/kd_tree_dynamic.o .libs/kd_tree_packed.o .libs/tqt.o  -Wl,--rpath -Wl,/usr/local/lib -L/usr/local/lib -lgnashbase -L/usr/lib -lSDL_mixer -lrt -lX11 -lXi -lXmu -L/usr/lib/gcc/x86_64-linux-gnu/4.0.3 -L/usr/lib/gcc/x86_64-linux-gnu/4.0.3/../../../../lib64 -L/usr/lib/gcc/x86_64-linux-gnu/4.0.3/../../.. -L/lib/../lib64 -L/usr/lib/../lib64 -lstdc++ -lm -lc -lgcc_s /usr/lib/gcc/x86_64-linux-gnu/4.0.3/crtendS.o /usr/lib/gcc/x86_64-linux-gnu/4.0.3/../../../../lib64/crtn.o  -Wl,-soname -Wl,libgnashgeo.so.0 -o .libs/libgnashgeo.so.0.0.0
/usr/bin/install -c -p .libs/libgnashgeo.so.0.0.0T /usr/local/lib/libgnashgeo.so.0.0.0
(cd /usr/local/lib && { ln -s -f libgnashgeo.so.0.0.0 libgnashgeo.so.0 || { rm -f libgnashgeo.so.0 && ln -s libgnashgeo.so.0.0.0 libgnashgeo.so.0; }; })
(cd /usr/local/lib && { ln -s -f libgnashgeo.so.0.0.0 libgnashgeo.so || { rm -f libgnashgeo.so && ln -s libgnashgeo.so.0.0.0 libgnashgeo.so; }; })
/usr/bin/install -c -p .libs/libgnashgeo.lai /usr/local/lib/libgnashgeo.la
/usr/bin/install -c -p .libs/libgnashgeo.a /usr/local/lib/libgnashgeo.a
ranlib /usr/local/lib/libgnashgeo.a
chmod 644 /usr/local/lib/libgnashgeo.a
PATH="$PATH:/sbin" ldconfig -n /usr/local/lib
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/stuart/Desktop/gnash-0.7.1/libgeometry'
make[1]: Leaving directory `/home/stuart/Desktop/gnash-0.7.1/libgeometry'
Making install in server
make[1]: Entering directory `/home/stuart/Desktop/gnash-0.7.1/server'
make[2]: Entering directory `/home/stuart/Desktop/gnash-0.7.1/server'
test -z "/usr/local/lib" || mkdir -p -- "/usr/local/lib"
 /bin/sh ../libtool --mode=install /usr/bin/install -c -p  'libgnashserver.la' '/usr/local/lib/libgnashserver.la'
/usr/bin/install -c -p .libs/libgnashserver.so.0.0.0 /usr/local/lib/libgnashserver.so.0.0.0
(cd /usr/local/lib && { ln -s -f libgnashserver.so.0.0.0 libgnashserver.so.0 || { rm -f libgnashserver.so.0 && ln -s libgnashserver.so.0.0.0 libgnashserver.so.0; }; })
(cd /usr/local/lib && { ln -s -f libgnashserver.so.0.0.0 libgnashserver.so || { rm -f libgnashserver.so && ln -s libgnashserver.so.0.0.0 libgnashserver.so; }; })
/usr/bin/install -c -p .libs/libgnashserver.lai /usr/local/lib/libgnashserver.la/usr/bin/install -c -p .libs/libgnashserver.a /usr/local/lib/libgnashserver.a
ranlib /usr/local/lib/libgnashserver.a
chmod 644 /usr/local/lib/libgnashserver.a
PATH="$PATH:/sbin" ldconfig -n /usr/local/lib
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
 /bin/sh ../libtool --mode=install /usr/bin/install -c -p  'libgnashasobjs.la' '/usr/local/lib/libgnashasobjs.la'
/usr/bin/install -c -p .libs/libgnashasobjs.so.0.0.0 /usr/local/lib/libgnashasobjs.so.0.0.0
(cd /usr/local/lib && { ln -s -f libgnashasobjs.so.0.0.0 libgnashasobjs.so.0 || { rm -f libgnashasobjs.so.0 && ln -s libgnashasobjs.so.0.0.0 libgnashasobjs.so.0; }; })
(cd /usr/local/lib && { ln -s -f libgnashasobjs.so.0.0.0 libgnashasobjs.so || { rm -f libgnashasobjs.so && ln -s libgnashasobjs.so.0.0.0 libgnashasobjs.so; }; })
/usr/bin/install -c -p .libs/libgnashasobjs.lai /usr/local/lib/libgnashasobjs.la/usr/bin/install -c -p .libs/libgnashasobjs.a /usr/local/lib/libgnashasobjs.a
ranlib /usr/local/lib/libgnashasobjs.a
chmod 644 /usr/local/lib/libgnashasobjs.a
PATH="$PATH:/sbin" ldconfig -n /usr/local/lib
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/stuart/Desktop/gnash-0.7.1/server'
make[1]: Leaving directory `/home/stuart/Desktop/gnash-0.7.1/server'
Making install in backend
make[1]: Entering directory `/home/stuart/Desktop/gnash-0.7.1/backend'
make[2]: Entering directory `/home/stuart/Desktop/gnash-0.7.1/backend'
test -z "/usr/local/lib" || mkdir -p -- "/usr/local/lib"
 /bin/sh ../libtool --mode=install /usr/bin/install -c -p  'libgnashbackend.la' '/usr/local/lib/libgnashbackend.la'
/usr/bin/install -c -p .libs/libgnashbackend.so.0.0.0 /usr/local/lib/libgnashbackend.so.0.0.0
(cd /usr/local/lib && { ln -s -f libgnashbackend.so.0.0.0 libgnashbackend.so.0 || { rm -f libgnashbackend.so.0 && ln -s libgnashbackend.so.0.0.0 libgnashbackend.so.0; }; })
(cd /usr/local/lib && { ln -s -f libgnashbackend.so.0.0.0 libgnashbackend.so || { rm -f libgnashbackend.so && ln -s libgnashbackend.so.0.0.0 libgnashbackend.so; }; })
/usr/bin/install -c -p .libs/libgnashbackend.lai /usr/local/lib/libgnashbackend.la
/usr/bin/install -c -p .libs/libgnashbackend.a /usr/local/lib/libgnashbackend.a
ranlib /usr/local/lib/libgnashbackend.a
chmod 644 /usr/local/lib/libgnashbackend.a
PATH="$PATH:/sbin" ldconfig -n /usr/local/lib
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
test -z "/usr/local/bin" || mkdir -p -- "/usr/local/bin"
  /bin/sh ../libtool --mode=install /usr/bin/install -c -p  'gnash' '/usr/local/bin/gnash'
/usr/bin/install -c -p .libs/gnash /usr/local/bin/gnash
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/stuart/Desktop/gnash-0.7.1/backend'
make[1]: Leaving directory `/home/stuart/Desktop/gnash-0.7.1/backend'
Making install in utilities
make[1]: Entering directory `/home/stuart/Desktop/gnash-0.7.1/utilities'
make[2]: Entering directory `/home/stuart/Desktop/gnash-0.7.1/utilities'
test -z "/usr/local/bin" || mkdir -p -- "/usr/local/bin"
  /bin/sh ../libtool --mode=install /usr/bin/install -c -p  'gparser' '/usr/local/bin/gparser'
/usr/bin/install -c -p .libs/gparser /usr/local/bin/gparser
  /bin/sh ../libtool --mode=install /usr/bin/install -c -p  'gprocessor' '/usr/local/bin/gprocessor'
/usr/bin/install -c -p .libs/gprocessor /usr/local/bin/gprocessor
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/stuart/Desktop/gnash-0.7.1/utilities'
make[1]: Leaving directory `/home/stuart/Desktop/gnash-0.7.1/utilities'
Making install in plugin
make[1]: Entering directory `/home/stuart/Desktop/gnash-0.7.1/plugin'
make[2]: Entering directory `/home/stuart/Desktop/gnash-0.7.1/plugin'
make[3]: Entering directory `/home/stuart/Desktop/gnash-0.7.1/plugin'
make[3]: Nothing to be done for `install-exec-am'.
test -d "/home/stuart/.firefox/plugins" || /bin/sh ../mkinstalldirs "/home/stuart/.firefox/plugins"
mkdir -p -- /home/stuart/.firefox/plugins
/bin/sh ../libtool --mode=install /usr/bin/install -c -p  libgnashplugin.la "/home/stuart/.firefox/plugins/libgnashplugin.la"
libtool: install: warning: relinking `libgnashplugin.la'
(cd /home/stuart/Desktop/gnash-0.7.1/plugin; /bin/sh ../libtool  --tag=CXX --mode=relink g++ -I.. -I. -I../libbase -I../backend -I../libgeometry -I../server -I./mozilla-sdk -I./mozilla-sdk/include -I/usr/include/libxml2 -I/usr/include/cairo -I/usr/include/SDL -I/usr/include/SDL -I. -g -O2 -Wall -L/usr/X11R6/lib -lX11 -lXi -lXmu -lSDL -L/usr/lib64 -lSDL_mixer -lGL -lGLU -lcairo -L/usr/lib -lxml2 -lz -lm -ljpeg -lpng -logg -o libgnashplugin.la -rpath /home/stuart/.firefox/plugins -module -avoid-version -no-undefined -L/home/stuart/.firefox/plugins plugin.lo npn_gate.lo npp_gate.lo np_entry.lo -L/usr/X11R6/lib -lX11 -lXi -lXmu -lSDL -L/usr/lib64 -lSDL_mixer -lGL -lGLU -lcairo -L/usr/lib -lxml2 -lz -lm -ljpeg -lpng -logg ../backend/libgnashbackend.la ../server/libgnashasobjs.la ../server/libgnashserver.la ../libgeometry/libgnashgeo.la ../libbase/libgnashbase.la -lSDL_mixer -lrt -lX11 -lXi -lXmu )
g++ -shared -nostdlib /usr/lib/gcc/x86_64-linux-gnu/4.0.3/../../../../lib64/crti.o /usr/lib/gcc/x86_64-linux-gnu/4.0.3/crtbeginS.o  .libs/plugin.o .libs/npn_gate.o .libs/npp_gate.o .libs/np_entry.o  -Wl,--rpath -Wl,/usr/local/lib -L/usr/X11R6/lib -L/usr/lib64 -L/usr/lib -L/home/stuart/.firefox/plugins -lSDL -lGL -lGLU -lcairo -lxml2 -lz -ljpeg -lpng -logg -L/usr/local/lib -lgnashbackend -lgnashasobjs -lgnashserver -lgnashgeo -lgnashbase -lSDL_mixer -lrt -lX11 -lXi -lXmu -L/usr/lib/gcc/x86_64-linux-gnu/4.0.3 -L/usr/lib/gcc/x86_64-linux-gnu/4.0.3/../../../../lib64 -L/usr/lib/gcc/x86_64-linux-gnu/4.0.3/../../.. -L/lib/../lib64 -L/usr/lib/../lib64 -lstdc++ -lm -lc -lgcc_s /usr/lib/gcc/x86_64-linux-gnu/4.0.3/crtendS.o /usr/lib/gcc/x86_64-linux-gnu/4.0.3/../../../../lib64/crtn.o  -Wl,-soname -Wl,libgnashplugin.so -o .libs/libgnashplugin.so
/usr/bin/install -c -p .libs/libgnashplugin.soT /home/stuart/.firefox/plugins/libgnashplugin.so
/usr/bin/install -c -p .libs/libgnashplugin.lai /home/stuart/.firefox/plugins/libgnashplugin.la
/usr/bin/install -c -p .libs/libgnashplugin.a /home/stuart/.firefox/plugins/libgnashplugin.a
ranlib /home/stuart/.firefox/plugins/libgnashplugin.a
chmod 644 /home/stuart/.firefox/plugins/libgnashplugin.a
PATH="$PATH:/sbin" ldconfig -n /home/stuart/.firefox/plugins
----------------------------------------------------------------------
Libraries have been installed in:
   /home/stuart/.firefox/plugins

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
rm -f /home/stuart/.firefox/plugins/libgnashplugin.*a
make[3]: Leaving directory `/home/stuart/Desktop/gnash-0.7.1/plugin'
make[2]: Leaving directory `/home/stuart/Desktop/gnash-0.7.1/plugin'
make[1]: Leaving directory `/home/stuart/Desktop/gnash-0.7.1/plugin'
make[1]: Entering directory `/home/stuart/Desktop/gnash-0.7.1'
make[2]: Entering directory `/home/stuart/Desktop/gnash-0.7.1'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/stuart/Desktop/gnash-0.7.1'
make[1]: Leaving directory `/home/stuart/Desktop/gnash-0.7.1'
stuart@stuart-desktop:~/Desktop/gnash-0.7.1$

---

### Post by mkoyle on 2007-01-14
For anyone looking to install Gnash now, the easiest way is to install it from the universe repository.

add the ubuntu universe repository (the following directions are for Edgy):

System --> Administration --> Synaptic Package Manager

Settings --> Repositories --> add a check by 'Community maintained Open Source software (universe).  Then click close.

Click search and search for gnash.  One of the items that comes up is 'mozilla-plugin-gnash."  Mark this for installation and install it and you're done.



Alternatively, to accomplish the same thing, you can also use apt-get.  You need to edit /etc/sources.list and add universe:

open a terminal and type

sudo gedit /etc/sources.list

there will be several lines that begin with hash marks (#) that say 'universe' at (or near) the end.  Remove those hash marks and save the file.

then type

sudo apt-get update

and finally

sudo apt-get install mozilla-plugin-gnash

and you're done.  Since this is an option, it is probably preferable to compiling from source unless you have a reason to compile.  This is the only flash plugin which works for me on an AMD-64 system right now.

--Matthew

---

