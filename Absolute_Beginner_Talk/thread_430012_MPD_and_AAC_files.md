---
title: "MPD and AAC files?"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by kylevan on 2007-05-01
I've been looking through various stuff on-line, but I haven't been able to suss this out.

I'm building a little music player using feisty server for my parents to hook up to their home stereo, and I have MPD working great with various .flac, .ogg, and .mp3 files, but there are a bunch of .m4a AAC files kicking around on the disk, and MPD doesn't put them in the db.

Everything was installed from the feisty repos, and I have libfaad2 and libmp4v2 installed, but these were installed after MPD.  Is the version of MPD in the repos not built with AAC support?  I was browsing the MPD forums and it looks like mp4/aac support was added some time ago (v. 0.10.x or so,) so I'm confused as to why this won't work.

---

### Post by zvacet on 2007-05-02
[https://help.ubuntu.com/community/RestrictedFormats/AAC]("https://help.ubuntu.com/community/RestrictedFormats/AAC")

---

### Post by potrick on 2007-05-10
Hey there. I looked into this once, and it seems that to keep MPD out of the restricted repository it has not been compiled with AAC support. I can only get MPD with AAC by recompiling MPD with FAAD installed. It's a pain but it's worth it.

---

### Post by El_Belgicano on 2008-02-25
Hi all,
I guess I'll have to recompile MPD to use it with AAC, but I get struck at some point:
1) untar
2) cd to dir
3) ./configure
then it tells me that AAC support is disabled
looking on the mpd website learned me I need FAAD2 installed, which I think I have...
to be sure I went to the site of the AudioCoding and downloaded the FAAD2, but I don't know how to install it...

Any help will be appreciated...
Thanks

---

### Post by fenian on 2008-02-25
You need to make sure you have the dev packages installed when building from source for faad and faac you need to do this...

> sudo apt-get install libfaad2-dev libmp4v2-dev libfaac-dev

If you get more errors for formats not being supported use synaptic to check that you have the corresponding dev packages installed.

---

### Post by El_Belgicano on 2008-02-26
That's what ./configure gives me:
```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
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
checking whether gcc and cc understand -c and -o together... yes
checking for a BSD-compatible install... /usr/bin/install -c
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
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
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
appending configuration tag "F77" to libtool
checking whether make sets $(MAKE)... (cached) yes
checking whether byte ordering is bigendian... no
checking for short... yes
checking size of short... 2
checking for int... yes
checking size of int... 4
checking for long... yes
checking size of long... 4
checking for long long... yes
checking size of long long... 8
checking sys/inttypes.h usability... no
checking sys/inttypes.h presence... no
checking for sys/inttypes.h... no
checking for socket in -lsocket... no
checking for gethostbyname in -lnsl... yes
checking for exp in -lm... yes
checking for setenv... yes
checking for nl_langinfo and CODESET... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for ipv6... yes
checking for pkg-config... /usr/bin/pkg-config
configure: /usr/bin/pkg-config couldn't find libshout. Try adjusting PKG_CONFIG_PATH.
checking for shout-config... no
checking sys/soundcard.h usability... yes
checking sys/soundcard.h presence... yes
checking for sys/soundcard.h... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for PULSE... no
configure: WARNING: PulseAudio not found -- disabling
checking for SAMPLERATE... no
configure: WARNING: libsamplerate not found -- disabling
checking for ALSA CFLAGS... 
checking for ALSA LDFLAGS...  -lasound -lm -ldl -lpthread
checking for libasound headers version >= 0.9.0... not present.
checking for snd_ctl_open in -lasound... no
checking for JACK... no
configure: WARNING: JACK not found -- disabling
checking iconv.h usability... yes
checking iconv.h presence... yes
checking for iconv.h... yes
checking for main in -liconv... no
checking id3tag.h usability... no
checking id3tag.h presence... no
checking for id3tag.h... no
checking mad.h usability... no
checking mad.h presence... no
checking for mad.h... no
checking mpcdec/mpcdec.h usability... no
checking mpcdec/mpcdec.h presence... no
checking for mpcdec/mpcdec.h... no
configure: WARNING: mpcdec lib needed for MPC support -- disabling MPC support
checking faad.h usability... yes
checking faad.h presence... yes
checking for faad.h... yes
checking whether FAAD2_VERSION is declared... yes
checking whether faacDecInit2 is declared... yes
checking for faacDecInit2 in -lfaad... yes
checking that FAAD2 uses buffer and bufferlen... yes
checking for mp4AudioSpecificConfig... yes
checking for faacDecConfiguration.downMatrix... yes
checking for faacDecConfiguration.dontUpSampleImplicitSBR... yes
checking for faacDecFrameInfo.samplerate... yes
checking for Ogg... yes
checking for Vorbis... yes
checking for libFLAC... no
*** Could not run libFLAC test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means libFLAC was incorrectly installed
*** or that you have moved libFLAC since it was installed. In the latter case, you
*** may want to edit the libFLAC-config script: 
checking for libOggFLAC... no
*** Could not run libOggFLAC test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means libOggFLAC was incorrectly installed
*** or that you have moved libOggFLAC since it was installed. In the latter case, you
*** may want to edit the libOggFLAC-config script: 
checking for audiofile-config... no
checking for Audio File Library - version >= 0.1.7... no
*** The audiofile-config script installed by the Audio File Library could
*** not be found.  If the Audio File Library was installed in PREFIX, make
*** sure PREFIX/bin is in your path, or set the AUDIOFILE_CONFIG
*** environment variable to the full path to audiofile-config.
configure: WARNING: You need audiofile  -- disabling audiofile support
checking for libmikmod-config... no
checking for libmikmod - version >= 3.1.7... no
*** The libmikmod-config script installed by libmikmod could not be found
*** If libmikmod was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the LIBMIKMOD_CONFIG environment variable to the
*** full path to libmikmod-config.
checking for AVAHI... no
configure: WARNING: No supported Zeroconf backend found, disabling Zeroconf
configure: creating ./config.status
config.status: creating src/mp4ff/Makefile
config.status: creating doc/Makefile
config.status: creating src/Makefile
config.status: creating Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands

########### MPD CONFIGURATION ############

 Playback Support:
 libao support .................disabled
 OSS support ...................enabled
 ALSA support ..................disabled
 JACK support ..................disabled
 OS X support ..................disabled
 PulseAudio support ............disabled
 Media MVP support .............disabled
 Shout streaming support .......disabled

 File Format Support:
 ID3 tag support ...............disabled
 mp3 support ...................disabled
 Ogg Vorbis support ............enabled
   using tremor.................no
 FLAC support ..................disabled
 OggFLAC support ...............disabled
 Wave file support .............disabled
 MP4/AAC support ...............enabled
 Musepack (MPC) support ........disabled
 MOD support ...................disabled

 Other features:
 libsamplerate support .........disabled
 Zeroconf support ..............disabled

##########################################

You are now ready to compile MPD
Type "make" to compile MPD

```

Can you tell me what other packages do I need?
(filetypes I need are just the AAC, and MP3)
Or where I can find a list of them.
Thanks for the fast reply :)


**EDIT1 27-02-08 :**
Installed some more dev packages (alsa, jack, flac, an some others) but still nothing...
Maybe a stupid question: after running ./configure, when I run make, it should create a .deb package right?

**EDIT2 28-02-08 :**
Next try, with the new packages: ./configure
```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
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
checking whether gcc and cc understand -c and -o together... yes
checking for a BSD-compatible install... /usr/bin/install -c
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
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
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
appending configuration tag "F77" to libtool
checking whether make sets $(MAKE)... (cached) yes
checking whether byte ordering is bigendian... no
checking for short... yes
checking size of short... 2
checking for int... yes
checking size of int... 4
checking for long... yes
checking size of long... 4
checking for long long... yes
checking size of long long... 8
checking sys/inttypes.h usability... no
checking sys/inttypes.h presence... no
checking for sys/inttypes.h... no
checking for socket in -lsocket... no
checking for gethostbyname in -lnsl... yes
checking for exp in -lm... yes
checking for setenv... yes
checking for nl_langinfo and CODESET... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for ipv6... yes
checking for pkg-config... /usr/bin/pkg-config
checking shout/shout.h usability... yes
checking shout/shout.h presence... yes
checking for shout/shout.h... yes
checking for shout_new... yes
checking sys/soundcard.h usability... yes
checking sys/soundcard.h presence... yes
checking for sys/soundcard.h... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for PULSE... no
configure: WARNING: PulseAudio not found -- disabling
checking for SAMPLERATE... yes
checking for ALSA CFLAGS... 
checking for ALSA LDFLAGS...  -lasound -lm -ldl -lpthread
checking for libasound headers version >= 0.9.0... found.
checking for snd_ctl_open in -lasound... yes
checking for JACK... yes
checking iconv.h usability... yes
checking iconv.h presence... yes
checking for iconv.h... yes
checking for main in -liconv... no
checking id3tag.h usability... yes
checking id3tag.h presence... yes
checking for id3tag.h... yes
checking for id3_file_open in -lid3tag... yes
checking mad.h usability... yes
checking mad.h presence... yes
checking for mad.h... yes
checking for mad_stream_init in -lmad... yes
checking mpcdec/mpcdec.h usability... yes
checking mpcdec/mpcdec.h presence... yes
checking for mpcdec/mpcdec.h... yes
checking for main in -lmpcdec... yes
checking faad.h usability... yes
checking faad.h presence... yes
checking for faad.h... yes
checking whether FAAD2_VERSION is declared... yes
checking whether faacDecInit2 is declared... yes
checking for faacDecInit2 in -lfaad... yes
checking that FAAD2 uses buffer and bufferlen... yes
checking for mp4AudioSpecificConfig... yes
checking for faacDecConfiguration.downMatrix... yes
checking for faacDecConfiguration.dontUpSampleImplicitSBR... yes
checking for faacDecFrameInfo.samplerate... yes
checking for Ogg... yes
checking for Vorbis... yes
checking for libFLAC... yes
checking for FLAC__metadata_object_vorbiscomment_find_entry_from in -lFLAC... yes
checking whether FLAC_API_SUPPORTS_OGG_FLAC is declared... yes
checking for audiofile-config... /usr/bin/audiofile-config
checking for Audio File Library - version >= 0.1.7... yes
checking for libmikmod-config... /usr/bin/libmikmod-config
checking for libmikmod - version >= 3.1.7... yes, `/usr/bin/libmikmod-config --version`
checking for AVAHI... no
configure: WARNING: No supported Zeroconf backend found, disabling Zeroconf
configure: creating ./config.status
config.status: creating src/mp4ff/Makefile
config.status: creating doc/Makefile
config.status: creating src/Makefile
config.status: creating Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands

########### MPD CONFIGURATION ############

 Playback Support:
 libao support .................disabled
 OSS support ...................enabled
 ALSA support ..................enabled
 JACK support ..................enabled
 OS X support ..................disabled
 PulseAudio support ............disabled
 Media MVP support .............disabled
 Shout streaming support .......enabled

 File Format Support:
 ID3 tag support ...............enabled
 mp3 support ...................enabled
 Ogg Vorbis support ............enabled
   using tremor.................no
 FLAC support ..................enabled
 OggFLAC support ...............enabled(FLAC 1.1.3)
 Wave file support .............enabled
 MP4/AAC support ...............enabled
 Musepack (MPC) support ........enabled
 MOD support ...................enabled

 Other features:
 libsamplerate support .........enabled
 Zeroconf support ..............disabled

##########################################

You are now ready to compile MPD
Type "make" to compile MPD
```
...but still nothing

---

### Post by El_Belgicano on 2008-02-28
bump, ... complete explanation of the problem in the post above, thanks.

---

### Post by flybiwire on 2008-03-09
After running the ./configure like you've done, type "sudo make" -- have you already done this?  If so, what happens?  I must confess that i'm a 1 week old to Linux/ Ubuntu, so forgive me if I'm asking too basic of a question.  I'm working on compiling mpd, too, and have finally gotten it to read in m4a files.

-fbw

---

### Post by El_Belgicano on 2008-03-11
ok, solved for me...

---

### Post by angry_johnnie on 2008-03-11
have you installed faac and libfaac ?

---

