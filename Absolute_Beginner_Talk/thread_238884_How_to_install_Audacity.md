---
title: "How to install Audacity?"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by saxofoner on 2006-08-18
I got [this]("http://packages.ubuntu.com/dapper/sound/audacity") far.

But I don't know what to do! :-k 

How do you install apps in Linux!  



...I hate being a noob.  ](*,)

---

### Post by DimaIL on 2006-08-18
hmmm, run in console:
sudo apt-get install audacity
or run synaptic and search audacity there.

easy, no?
Dima

---

### Post by Tomosaur on 2006-08-18
There's a much easier way! Type this into a terminal:
```

sudo apt-get install audacity

```

Input your login password, and audacity will be downloaded and installed in a minute or two (if that) :)

---

### Post by saxofoner on 2006-08-18
Does that only work for apps that Linux "knows", or will it just figure out what you mean?

Thanks.

EDIT:  THAT CODE DIDN'T WORK.  RETURNED:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package audacity

---

### Post by Tomosaur on 2006-08-18
Ah right, you may need to edit your sources file:

```

sudo nano /etc/apt/sources.list

```

Read the file carefully and uncomment the lines you want to use. When you're done, press Ctrl+O to save (followed by enter, since it asks to confirm the filename), then Ctrl+X to exit nano. Then you can try
```

sudo apt-get install audacity

```

again.

---

### Post by saxofoner on 2006-08-18
I erased the ## comment symbols before the two url lines, but I still get the same error message from
sudo apt-get install audacity

---

### Post by Perfect Storm on 2006-08-18
```
cat /etc/apt/sources.list
```

please post it.

---

### Post by syedn on 2006-08-18
I don't believe audacity is in the repos, even if you've enabled both uni-and-multi verse.

---

### Post by saxofoner on 2006-08-18
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by Perfect Storm on 2006-08-18
okay
```
sudo nano /etc/apt/sources.list
```

add:

[b]
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
[/b]
save and exit <ctrl>+<o> and <ctrl> + <x>

```
sudo apt-get update
sudo apt-get install audacity
```

---

### Post by saxofoner on 2006-08-18
Yay!  It's working.  Thank you.  I  have no idea what I actually DID, but I'll learn.  Thanks!

---

### Post by saxofoner on 2006-08-18
Well it installed, but now Audacity can't do i/o for audio, which sort of defeats the purpsose... I'll check their forums.

---

### Post by Perfect Storm on 2006-08-18
the "cat" command displayed what's in the sources.list file.

```
cat /etc/apt/sources.list
```


to modify the sources.list file you used the "nano" to edit it. With the sudo infront of it you are given priveledge to edit it (sudo = superuser do).

```
sudo nano /etc/apt/sources.list
```


You added the lines:

```
deb http://archive.ubuntu.com/ubuntu dapper universe multiverse
deb http://archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse

deb-src http://archive.ubuntu.com/ubuntu dapper universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

```

Which tells the application called "apt-get" where it can download extra stuff for your ubuntu. You can also use the Synaptic package manager (System tab ---> Adminstration). It's actually having a central data base to download everything you need, so you don't have to browse through tons of web-sites.

---

### Post by Perfect Storm on 2006-08-18
> **saxofoner said:**
> Well it installed, but now Audacity can't do i/o for audio, which sort of defeats the purpsose... I'll check their forums.

add this to your source list:

[b]## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free       [/b]

and do the same thing you did last time you added multiverse/universe.

When done.

```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base
sudo apt-get install gstreamer0.10-plugins-good gstreamer0.10-plugins-bad
sudo apt-get install gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly 
sudo apt-get install gstreamer0.10-plugins-ugly-multiverse
sudo apt-get install w32codecs
```

That should make it work.

---

### Post by saxofoner on 2006-08-18
Kay, I'll do that.  Is there a way to update to the current version?  The one I installed is WAY Old.

EDIT:  They all worked except that last codecs one.  Now I'll see if Audacity works.

---

### Post by Perfect Storm on 2006-08-18
Then you need to compile. I could guide you through it.

---

### Post by saxofoner on 2006-08-18
Uh, yeah, okay.  I'll try.  Can I install it where I'd like?  I think these have been going in the wrong places.  I need to put them on a certain partition.

[http://www.audacityteam.org/wiki/index.php?title=CompilingAudacityForBeginners](http://www.audacityteam.org/wiki/index.php?title=CompilingAudacityForBeginners)

^I'm going to try that.

---

### Post by Perfect Storm on 2006-08-18
Well, the script its running install it in the right place.

First download the source here: [http://audacity.sourceforge.net/download/beta_source](http://audacity.sourceforge.net/download/beta_source) (beta 1.30 source tarball)
to you Desktop.

Now you need some compiling tool and the gtk2 engine header:
```
 sudo apt-get install build-essential libgtk2.0-dev
```

Unpack the source to your Desktop.
Now 
```
cd /to/the/audacity/folder
./configure
```

please post all the output of the ./configure

---

### Post by saxofoner on 2006-08-18
```
julian@saxofone:~/Desktop/audacity-src-1.3.0b-beta$ ./configure
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
checking for egrep... grep -E
checking whether gcc needs -traditional... no
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking how to run the C++ preprocessor... g++ -E
checking for a BSD-compatible install... /usr/bin/install -c
configure: Determining what libraries are available in this tree and on the system
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
checking for vorbis_bitrate_addblock in -lvorbisfile... no
checking vorbis/vorbisfile.h usability... no
checking vorbis/vorbisfile.h presence... no
checking for vorbis/vorbisfile.h... no
configure: Vorbis libraries are NOT available as system libraries
checking for ./lib-src/libvorbis/include/vorbis/vorbisenc.h... no
checking for ./lib-src/libogg/include/ogg/ogg.h... no
configure: Vorbis libraries are NOT available in this source tree
checking for mad_decoder_init in -lmad... no
checking mad.h usability... no
checking mad.h presence... no
checking for mad.h... no
configure: libmad libraries are NOT available as system libraries
checking for ./lib-src/libmad/frame.h... no
configure: libmad libraries are NOT available in the local tree
checking for FLAC__file_decoder_new in -lFLAC... no
checking FLAC/format.h usability... no
checking FLAC/format.h presence... no
checking for FLAC/format.h... no
configure: FLAC/FLAC++ libraries are NOT available as system libraries
checking for ./lib-src/libflac/include/FLAC/format.h... no
checking for ./lib-src/libflac/include/FLAC++/decoder.h... no
configure: FLAC libraries are NOT available in this source tree
checking for pkg-config... /usr/bin/pkg-config
checking for sndfile >= 1.0.0... configure: Libsndfile libraries are NOT available as system libraries
checking for ./lib-src/libsndfile/src/sndfile.h.in... yes
configure: libsndfile libraries are available in this source tree
checking for id3_file_open in -lid3tag... no
checking id3tag.h usability... no
checking id3tag.h presence... no
checking for id3tag.h... no
configure: Libid3tag libraries are NOT available as system libraries
checking for ./lib-src/libid3tag/frame.h... no
configure: libid3tag libraries are NOT available in the local tree
checking for samplerate >= 0.15.0... configure: Libsamplerate libraries are NOT available as system libraries
checking for ./lib-src/libsamplerate/src/samplerate.h... no
configure: libsamplerate libraries are NOT available in the local tree
checking for ./lib-src/libresample/include/libresample.h... yes
configure: libresample libraries are available in the local tree
checking for ./lib-src/soundtouch/include/SoundTouch.h... yes
configure: libsoundtouch libraries are available in the local tree
checking for ./lib-src/libnyquist/nyx/nyx.h... yes
configure: nyquist libraries are available in the local tree
configure: Figuring out what libraries to enable
configure: disabling LIBVORBIS
configure: disabling LIBMAD
configure: disabling LIBFLAC
configure: Using LOCAL libraries for LIBSNDFILE
configure: disabling LIBID3TAG
configure: disabling LIBSAMPLERATE
configure: Using LOCAL libraries for LIBRESAMPLE
configure: Using LOCAL libraries for LIBSOUNDTOUCH
configure: Using LOCAL libraries for LIBNYQUIST
checking for zip... /usr/bin/zip
checking for wx-config... no
configure: error: "Could not find wx-config: is wxWindows installed? is wx-config in your path?"

```

---

### Post by Perfect Storm on 2006-08-18
```
sudo apt-get install libvorbis-dev libmad0-dev libflac-dev libflac++-dev libsndfile1-dev libid3tag0-dev libsamplerate0-dev libwxgtk2.6-dev
```

As you might see this is what your ./configure says you are missing. When install these -dev package run ./configure again and post it.

---

### Post by saxofoner on 2006-08-18
Oh, I'm starting to get it.  Will do. I'll update this post when finished.

```
julian@saxofone:~/Desktop/audacity-src-1.3.0b-beta$ ./configure
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
checking for egrep... grep -E
checking whether gcc needs -traditional... no
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking how to run the C++ preprocessor... g++ -E
checking for a BSD-compatible install... /usr/bin/install -c
configure: Determining what libraries are available in this tree and on the system
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
checking for vorbis_bitrate_addblock in -lvorbisfile... yes
checking vorbis/vorbisfile.h usability... yes
checking vorbis/vorbisfile.h presence... yes
checking for vorbis/vorbisfile.h... yes
configure: Vorbis libraries are available as system libraries
checking for ./lib-src/libvorbis/include/vorbis/vorbisenc.h... no
checking for ./lib-src/libogg/include/ogg/ogg.h... no
configure: Vorbis libraries are NOT available in this source tree
checking for mad_decoder_init in -lmad... yes
checking mad.h usability... yes
checking mad.h presence... yes
checking for mad.h... yes
configure: libmad libraries are available as system libraries
checking for ./lib-src/libmad/frame.h... no
configure: libmad libraries are NOT available in the local tree
checking for FLAC__file_decoder_new in -lFLAC... yes
checking FLAC/format.h usability... yes
checking FLAC/format.h presence... yes
checking for FLAC/format.h... yes
configure: FLAC libraries are available as system libraries
checking for ./lib-src/libflac/include/FLAC/format.h... no
checking for ./lib-src/libflac/include/FLAC++/decoder.h... no
configure: FLAC libraries are NOT available in this source tree
checking for pkg-config... /usr/bin/pkg-config
checking for sndfile >= 1.0.0... yes
checking SNDFILE_CFLAGS...
checking SNDFILE_LIBS... -lsndfile
configure: Libsndfile libraries are available as system libraries
checking for ./lib-src/libsndfile/src/sndfile.h.in... yes
configure: libsndfile libraries are available in this source tree
checking for id3_file_open in -lid3tag... yes
checking id3tag.h usability... yes
checking id3tag.h presence... yes
checking for id3tag.h... yes
configure: Libid3tag libraries are available as system libraries
checking for ./lib-src/libid3tag/frame.h... no
configure: libid3tag libraries are NOT available in the local tree
checking for samplerate >= 0.15.0... configure: Libsamplerate libraries are NOT available as system libraries
checking for ./lib-src/libsamplerate/src/samplerate.h... no
configure: libsamplerate libraries are NOT available in the local tree
checking for ./lib-src/libresample/include/libresample.h... yes
configure: libresample libraries are available in the local tree
checking for ./lib-src/soundtouch/include/SoundTouch.h... yes
configure: libsoundtouch libraries are available in the local tree
checking for ./lib-src/libnyquist/nyx/nyx.h... yes
configure: nyquist libraries are available in the local tree
configure: Figuring out what libraries to enable
configure: Using SYSTEM libraries for LIBVORBIS
configure: Using SYSTEM libraries for LIBMAD
configure: Using SYSTEM libraries for LIBFLAC
configure: Using SYSTEM libraries for LIBSNDFILE
configure: Using SYSTEM libraries for LIBID3TAG
configure: disabling LIBSAMPLERATE
configure: Using LOCAL libraries for LIBRESAMPLE
configure: Using LOCAL libraries for LIBSOUNDTOUCH
configure: Using LOCAL libraries for LIBNYQUIST
checking for zip... /usr/bin/zip
checking for wx-config... /usr/bin/wx-config
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for lrint... yes
checking for lrintf... yes
checking for an ANSI C-conforming const... yes
checking for size_t... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating lib-src/Makefile
config.status: creating lib-src/allegro/Makefile
config.status: creating lib-src/expat/Makefile
config.status: creating lib-src/libnyquist/Makefile
config.status: creating lib-src/portaudio/pa_unix_oss/Makefile
config.status: creating locale/Makefile
config.status: creating tests/Makefile
config.status: creating src/configunix.h
configure: configuring in lib-src/libresample
configure: running /bin/sh './configure' --prefix=/usr/local  --cache-file=/dev/null --srcdir=.
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for ranlib... ranlib
checking for ar... /usr/bin/ar
checking for sf_open in -lsndfile... yes
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
checking sndfile.h usability... yes
checking sndfile.h presence... yes
checking for sndfile.h... yes
checking for src_simple in -lsamplerate... yes
checking for inttypes.h... (cached) yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/config.h

Configured to build tests/resample-sndfile using libsndfile

Configured to build tests/compareresample to compare against
Erik de Castro Lopo's libsamplerate library.

Type 'configure --help' to see options.

Type 'make' to build libresample and tests.
configure: configuring in lib-src/soundtouch
configure: running /bin/sh './configure' --prefix=/usr/local  --cache-file=/dev/null --srcdir=.
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
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
checking how to run the C preprocessor... gcc -E
checking how to run the C++ preprocessor... g++ -E
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... (cached) yes
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
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... no
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
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
appending configuration tag "F77" to libtool
checking for ANSI C header files... (cached) yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether byte ordering is bigendian... no
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking return type of signal handlers... void
checking for sqrt in -lm... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating source/Makefile
config.status: creating source/SoundTouch/Makefile
config.status: creating source/example/Makefile
config.status: creating source/example/SoundStretch/Makefile
config.status: creating source/example/bpm/Makefile
config.status: creating include/Makefile
config.status: creating config/config.h
config.status: executing depfiles commands

Finished configure:
LIBVORBIS: using SYSTEM libraries
LIBMAD: using SYSTEM libraries
LIBFLAC: using SYSTEM libraries
LIBSNDFILE: using SYSTEM libraries
LIBID3TAG: using SYSTEM libraries
LIBSAMPLERATE: disabled
LIBRESAMPLE: using LOCAL libraries
LIBSOUNDTOUCH: using LOCAL libraries
LIBNYQUIST: using LOCAL libraries
ladspa: enabled
audiounits: disabled
prefix=/usr/local

Note: portaudio v18 only supports OSS.  If your system supports
ALSA, you may want to reconfigure --with-portaudio=v19, though
portaudio v19 is newer and possibly less stable.

Run 'configure --help' for an explanation of these options,
otherwise run 'make' to build Audacity.
julian@saxofone:~/Desktop/audacity-src-1.3.0b-beta$

```

Uh oh. There's a lot of nos.  Shall I "sudo apt-get install" all those?


And one other thing.  How do I see where all these files are installing when it asks me "Presss Y/N"?

---

### Post by Perfect Storm on 2006-08-18
:) 

You use the -dev package when you want to compile stuff (in most cases).

---

### Post by saxofoner on 2006-08-18
Alright I posted the code.  Now that I have the -dev package, I don't have to do that step in the future, correct?

---

### Post by Perfect Storm on 2006-08-18
Aye, now the -dev packages are installed, so you don't have to install these -dev package again.

Can I get the last ./configure?

---

### Post by saxofoner on 2006-08-18
Yes it's about 3 posts up.  That's the new one.  I added to that post.

---

### Post by Perfect Storm on 2006-08-18
Okay.

> Uh oh. There's a lot of nos. Shall I "sudo apt-get install" all those?

No, it's actually looking for it in diffrent places and setups. (every linux distro is diffrent)

> 
And one other thing. How do I see where all these files are installing when it asks me "Presss Y/N"?

You can
```
locate XXXXX
whereis XXXXX

```

another option is open up synaptic, search for the thing you installed and hit the properties button.



You sould be ready to go further now. But if you want to see some  option for ./configure do:
```
./configure --help
```
If you want to see stuff you can change.



now, before typing in the next commands, make sure that your previous audacity is uninstall. When done, back to the terminal;
```
make
```
This will take time. This command puts the pieces togehter.
When done use this command, which install the application on Linux/ubuntu;
```
sudo make install
```
[code]

---

### Post by saxofoner on 2006-08-18
```
julian@saxofone:~/Desktop/audacity-src-1.3.0b-beta$ sudo make install
Password:
make -C lib-src
make[1]: Entering directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/lib-src'
make -C libresample
make[2]: Entering directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/lib-src/libresample'
gcc -o tests/testresample \
                -g -O2 -Wall ./tests/testresample.c \
                libresample.a -lm
make[2]: Leaving directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/lib-src/libresample'
ln -sf libresample/libresample.a libresample.a
make -C soundtouch
make[2]: Entering directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/lib-src/soundtouch'
Making all in include
make[3]: Entering directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/lib-src/soundtouch/include'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/lib-src/soundtouch/include'
Making all in source
make[3]: Entering directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/lib-src/soundtouch/source'
Making all in SoundTouch
make[4]: Entering directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/lib-src/soundtouch/source/SoundTouch'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/lib-src/soundtouch/source/SoundTouch'
Making all in example
make[4]: Entering directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/lib-src/soundtouch/source/example'
Making all in bpm
make[5]: Entering directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/lib-src/soundtouch/source/example/bpm'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/lib-src/soundtouch/source/example/bpm'
Making all in SoundStretch
make[5]: Entering directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/lib-src/soundtouch/source/example/SoundStretch'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/lib-src/soundtouch/source/example/SoundStretch'
make[5]: Entering directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/lib-src/soundtouch/source/example'
make[5]: Nothing to be done for `all-am'.
make[5]: Leaving directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/lib-src/soundtouch/source/example'
make[4]: Leaving directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/lib-src/soundtouch/source/example'
make[4]: Entering directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/lib-src/soundtouch/source'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/lib-src/soundtouch/source'
make[3]: Leaving directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/lib-src/soundtouch/source'
make[3]: Entering directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/lib-src/soundtouch'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/lib-src/soundtouch'
make[2]: Leaving directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/lib-src/soundtouch'
ln -sf soundtouch/source/SoundTouch/.libs/libSoundTouch.a .
make -C libnyquist
make[2]: Entering directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/lib-src/libnyquist'
make[2]: Nothing to be done for `current'.
make[2]: Leaving directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/lib-src/libnyquist'
ln -sf libnyquist/libnyquist.a libnyquist.a
make -C expat
make[2]: Entering directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/lib-src/expat'
make[2]: `expat.a' is up to date.
make[2]: Leaving directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/lib-src/expat'
ln -sf expat/expat.a expat.a
make -C allegro
make[2]: Entering directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/lib-src/allegro'
make[2]: `allegro.a' is up to date.
make[2]: Leaving directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/lib-src/allegro'
ln -sf allegro/allegro.a allegro.a
make[1]: Leaving directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/lib-src'
make -C src
make[1]: Entering directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/src'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/src'
make -C locale
make[1]: Entering directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/locale'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/locale'
# install desktop file
/usr/bin/install -c -d /usr/local/share/applications
/usr/bin/install -c -m 644 src/audacity.desktop /usr/local/share/applications
# install MIME information
/usr/bin/install -c -d /usr/local/share/mime/packages
/usr/bin/install -c -m 644 src/audacity.xml /usr/local/share/mime/packages
# install the binary
/usr/bin/install -c -d /usr/local/bin
/usr/bin/install -c -m 755 audacity /usr/local/bin/audacity
# install docs
/usr/bin/install -c -d /usr/local/share/audacity
test -f audacity-1.2-help.htb && /usr/bin/install -c -m 644 audacity-1.2-help.htb \
                /usr/local/share/audacity/audacity-1.2-help.htb
/usr/bin/install -c -d /usr/local/share/doc/audacity
/usr/bin/install -c -m 644 README.txt /usr/local/share/doc/audacity/README.txt
/usr/bin/install -c -m 644 LICENSE.txt /usr/local/share/doc/audacity/LICENSE.txt# install manpage
/usr/bin/install -c -d /usr/local/man/man1
test -f help/audacity.1.gz && \
                /usr/bin/install -c -m 644 help/audacity.1.gz \
                /usr/local/man/man1/audacity.1.gz
# install nyquist
/usr/bin/install -c -d /usr/local/share/audacity/nyquist
/usr/bin/install -c -m 644 nyquist/*.lsp /usr/local/share/audacity/nyquist
# install plug-ins
/usr/bin/install -c -d /usr/local/share/audacity/plug-ins
/usr/bin/install -c -m 644 plug-ins/*.ny /usr/local/share/audacity/plug-ins
# install locales
make -C locale install
make[1]: Entering directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/locale'
linguas='ar bg ca cs da de el es eu fi fr ga hu it ja lt mk nb nl pl pt ru sl sv uk zh zh_TW'; for lang in $linguas ; do \
           /usr/bin/install -c -d /usr/local/share/locale/$lang/LC_MESSAGES ; \
           /usr/bin/install -c -m 644 $lang/audacity.mo /usr/local/share/locale/$lang/LC_MESSAGES/audacity.mo ; \
        done
make[1]: Leaving directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/locale'
```

i tried running it, and I got the same old "no audio i/o" error.

---

### Post by Perfect Storm on 2006-08-18
```
cd
audacity

```

To check if it works.

---

### Post by Perfect Storm on 2006-08-18
> **saxofoner said:**
> ```
julian@saxofone:~/Desktop/audacity-src-1.3.0b-beta$ sudo make install
Password:
make -C lib-src
make[1]: Entering directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/lib-src'
make -C libresample
make[2]: Entering directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/lib-src/libresample'
gcc -o tests/testresample \
                -g -O2 -Wall ./tests/testresample.c \
                libresample.a -lm
make[2]: Leaving directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/lib-src/libresample'
ln -sf libresample/libresample.a libresample.a
make -C soundtouch
make[2]: Entering directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/lib-src/soundtouch'
Making all in include
make[3]: Entering directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/lib-src/soundtouch/include'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/lib-src/soundtouch/include'
Making all in source
make[3]: Entering directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/lib-src/soundtouch/source'
Making all in SoundTouch
make[4]: Entering directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/lib-src/soundtouch/source/SoundTouch'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/lib-src/soundtouch/source/SoundTouch'
Making all in example
make[4]: Entering directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/lib-src/soundtouch/source/example'
Making all in bpm
make[5]: Entering directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/lib-src/soundtouch/source/example/bpm'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/lib-src/soundtouch/source/example/bpm'
Making all in SoundStretch
make[5]: Entering directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/lib-src/soundtouch/source/example/SoundStretch'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/lib-src/soundtouch/source/example/SoundStretch'
make[5]: Entering directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/lib-src/soundtouch/source/example'
make[5]: Nothing to be done for `all-am'.
make[5]: Leaving directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/lib-src/soundtouch/source/example'
make[4]: Leaving directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/lib-src/soundtouch/source/example'
make[4]: Entering directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/lib-src/soundtouch/source'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/lib-src/soundtouch/source'
make[3]: Leaving directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/lib-src/soundtouch/source'
make[3]: Entering directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/lib-src/soundtouch'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/lib-src/soundtouch'
make[2]: Leaving directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/lib-src/soundtouch'
ln -sf soundtouch/source/SoundTouch/.libs/libSoundTouch.a .
make -C libnyquist
make[2]: Entering directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/lib-src/libnyquist'
make[2]: Nothing to be done for `current'.
make[2]: Leaving directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/lib-src/libnyquist'
ln -sf libnyquist/libnyquist.a libnyquist.a
make -C expat
make[2]: Entering directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/lib-src/expat'
make[2]: `expat.a' is up to date.
make[2]: Leaving directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/lib-src/expat'
ln -sf expat/expat.a expat.a
make -C allegro
make[2]: Entering directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/lib-src/allegro'
make[2]: `allegro.a' is up to date.
make[2]: Leaving directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/lib-src/allegro'
ln -sf allegro/allegro.a allegro.a
make[1]: Leaving directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/lib-src'
make -C src
make[1]: Entering directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/src'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/src'
make -C locale
make[1]: Entering directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/locale'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/locale'
# install desktop file
/usr/bin/install -c -d /usr/local/share/applications
/usr/bin/install -c -m 644 src/audacity.desktop /usr/local/share/applications
# install MIME information
/usr/bin/install -c -d /usr/local/share/mime/packages
/usr/bin/install -c -m 644 src/audacity.xml /usr/local/share/mime/packages
# install the binary
/usr/bin/install -c -d /usr/local/bin
/usr/bin/install -c -m 755 audacity /usr/local/bin/audacity
# install docs
/usr/bin/install -c -d /usr/local/share/audacity
test -f audacity-1.2-help.htb && /usr/bin/install -c -m 644 audacity-1.2-help.htb \
                /usr/local/share/audacity/audacity-1.2-help.htb
/usr/bin/install -c -d /usr/local/share/doc/audacity
/usr/bin/install -c -m 644 README.txt /usr/local/share/doc/audacity/README.txt
/usr/bin/install -c -m 644 LICENSE.txt /usr/local/share/doc/audacity/LICENSE.txt# install manpage
/usr/bin/install -c -d /usr/local/man/man1
test -f help/audacity.1.gz && \
                /usr/bin/install -c -m 644 help/audacity.1.gz \
                /usr/local/man/man1/audacity.1.gz
# install nyquist
/usr/bin/install -c -d /usr/local/share/audacity/nyquist
/usr/bin/install -c -m 644 nyquist/*.lsp /usr/local/share/audacity/nyquist
# install plug-ins
/usr/bin/install -c -d /usr/local/share/audacity/plug-ins
/usr/bin/install -c -m 644 plug-ins/*.ny /usr/local/share/audacity/plug-ins
# install locales
make -C locale install
make[1]: Entering directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/locale'
linguas='ar bg ca cs da de el es eu fi fr ga hu it ja lt mk nb nl pl pt ru sl sv uk zh zh_TW'; for lang in $linguas ; do \
           /usr/bin/install -c -d /usr/local/share/locale/$lang/LC_MESSAGES ; \
           /usr/bin/install -c -m 644 $lang/audacity.mo /usr/local/share/locale/$lang/LC_MESSAGES/audacity.mo ; \
        done
make[1]: Leaving directory `/home/julian/Desktop/audacity-src-1.3.0b-beta/locale'
```

i tried running it, and I got the same old "no audio i/o" error.

Did you install the extra stuff I've shown previously?

Do you have sound on everything else? If not you might have a soundcard problem.

---

### Post by saxofoner on 2006-08-18
Yes, I've got sound, I'm listening to internet radio.  Sounds great.

By the way, the error says "Error:  Host error."

---

### Post by Perfect Storm on 2006-08-18
Is it onboard card?

---

### Post by saxofoner on 2006-08-18
Yes.  I have an ASUS mobo with integrated sound.

Lemme guess... I need a real sound card?

---

### Post by Perfect Storm on 2006-08-18
Well, I read some troubles with onboard cards. Either you can take the problem to the hardware forum or you can boy a cheap good creative card (not the newest one).

I myself have an Audigy 2.

---

### Post by saxofoner on 2006-08-18
I forgot to mention this:  Earlier, when I was on the old version, it started once with sound working, but it wouldn't actually record.

---

### Post by Perfect Storm on 2006-08-18
No errors?

If you want to uninstall the compiled one do
```
sudo make uninstall
```
In the folder you compiled audacity.

It could also be audacity beta version that doesn't work for your card.

---

### Post by derouge on 2006-08-18
I can only use Audacity when every other program that uses sound is shut down .. Rhythmbox, XFMedia, etc. close those and other sound-using programs (internet radio) down and then try it.

---

