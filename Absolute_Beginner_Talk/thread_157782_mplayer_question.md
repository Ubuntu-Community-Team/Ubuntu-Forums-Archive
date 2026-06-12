---
title: "mplayer question"
date: 2006-04-09
forum: Absolute Beginner Talk
---

### Post by LiquidFlame on 2006-04-09
so i'm installing mplayer and i was going of of these instructions: [http://www.oldskoolphreak.com/tfiles/hack/ubuntu.txt]("http://www.oldskoolphreak.com/tfiles/hack/ubuntu.txt")  Everything was working fine until i got to the part to compile mplayer.  i got to the part where i ./configure --enable-gui and then when i tried to make it, it said command not found.  here's an out of when i did the ./configure --enable-gui

> Detected operating system: Linux
Detected host architecture: i386
Checking for cc version ... 4.0.2, bad
Checking for gcc version ... 4.0.2, bad
Checking for gcc-3.4 version ... 3.4.5, ok
Checking for host cc ... gcc-3.4
Checking for CPU vendor ... GenuineIntel (15:2:5)
Checking for CPU type ...  Intel(R) Pentium(R) 4 CPU 2.26GHz
Checking for GCC & CPU optimization abilities ... pentium4
Checking for kernel support of mmx ... yes
Checking for kernel support of mmx2 ... yes
Checking for kernel support of sse ... yes
Checking for kernel support of sse2 ... yes
Checking for mtrr support ... yes
Checking for assembler support of -pipe option ... yes
Checking for assembler (as 2.16.1) ... ok
Checking for Linux kernel version ... 2.6.12-9-386, ok
Checking for mplayer binary name ... mplayer
Checking for awk ... mawk
Checking for extra headers ... none
Checking for extra libs ... none
Checking for -lposix ... no
Checking for -lm ... yes
Checking for i18n ... yes
Checking for iconv ... yes
Checking for langinfo ... yes
Checking for language ... using en (man pages:  en)
Checking for enable sighandler ... yes
Checking for runtime cpudetection ... no
Checking for restrict keyword ... __restrict
Checking for __builtin_expect ... yes
Checking for kstat ... no
Checking for posix4 ... no
Checking for lrintf ... yes
Checking for nanosleep ... yes
Checking for socklib ... yes (using -lnsl)
Checking for inet_pton() ... yes (using -lnsl)
Checking for inttypes.h (required) ... yes
Checking for int_fastXY_t in inttypes.h ... yes
Checking for word size ... 32
Checking for stddef.h ... yes
Checking for malloc.h ... yes
Checking for memalign() ... yes
Checking for alloca.h ... yes
Checking for mman.h ... yes
Checking for dynamic loader ... yes
Checking for dynamic a/v plugins support ... no
Checking for pthread ... yes (using -lpthread)
Checking for sys/soundcard.h ... yes
Checking for sys/dvdio.h ... no
Checking for sys/cdio.h ... no
Checking for linux/cdrom.h ... yes
Checking for dvd.h ... no
Checking for BSDI dvd.h ... no
Checking for HPUX SCSI header ... no
Checking for userspace SCSI headers (Solaris) ... no
Checking for termcap ... no
Checking for termios ... yes (using sys/termios.h)
Checking for shm ... yes
Checking for linux devfs ... no
Checking for scandir() ... yes
Checking for strsep() ... yes
Checking for strlcpy() ... no
Checking for strlcat() ... no
Checking for fseeko() ... yes
Checking for localtime_r() ... yes
Checking for vsscanf() ... yes
Checking for swab() ... yes
Checking for posix select() ... yes
Checking for gettimeofday() ... yes
Checking for glob() ... yes
Checking for sys/sysinfo.h ... yes
Checking for Mac OS X APIs ... no
Checking for Mac OS X Finder Support ... no
Checking for Mac OS X Bundle file locations ... no
Checking for Samba support (libsmbclient) ... no
Checking for 3dfx ... no
Checking for tdfxfb ... no
Checking for tdfxvid ... no
Checking for tga ... yes
Checking for DirectFB headers presence ... not found
Checking for DirectFB ... no
Checking for X11 headers presence ... yes (using /usr/include)
Checking for X11 libs presence ... yes (using /usr/lib)
Checking for X11 ... yes
Checking for DPMS ... yes (using Xdpms 4)
Checking for Xv ... yes
Checking for XvMC ... no
Checking for Xinerama ... no
Checking for Xxf86vm ... no
Checking for XF86keysym ... yes
Checking for DGA ... no
Checking for OpenGL ... yes
Checking for /dev/mga_vid ... no
Checking for xmga ... no
Checking for GGI ... no
Checking for AA ... no
Checking for CACA ... no
Checking for SVGAlib ... no
Checking for FBDev ... yes
Checking for DVB ... no (specify path to DVB/ost/include with --with-dvbincdir=DIR)
Checking for DVB HEAD ... yes
Checking for PNG support ... yes
Checking for JPEG support ... no
Checking for PNM support ... yes
Checking for md5sum support ... yes
Checking for GIF support ... no
Checking for VESA support ... yes
Checking for SDL ... no
Checking for Windows waveout ... no
Checking for Directx ... no
Checking for NAS ... no
Checking for DXR2 ... no
Checking for DXR3/H+ ... no
Checking for libmp1e ... no
Checking for libfame ... no
Checking for OSS Audio ... yes
Checking for aRts ... no
Checking for EsounD ... no
Checking for Polyp ... no
Checking for JACK ... no
Checking for ALSA audio ... no
Checking for Sun audio ... no
Checking for Sun mediaLib ... no
Checking for SGI audio ... no
Checking for VCD support ... ok
Checking for DVD support (libmpdvdkit) ... yes
Checking for DVD support (libdvdread) ... disabled by libmpdvdkit2
Checking for cdparanoia ... no
Checking for freetype >= 2.0.9 ... no
Checking for fontconfig ... no
Checking for fribidi with charsets ... no
Checking for ENCA ... no
Checking for zlib ... yes
Checking for RTC ... yes
Checking for external liblzo support ... no
Checking for mad support ... no
Checking for Toolame ... no
Checking for OggVorbis support ... yes (internal Tremor)
Checking for OggTheora support (only the CVS version!) ... no
Checking for mp3lib support ... yes
Checking for liba52 support ... yes
Checking for libdts support ... no
Checking for libmpeg2 support ... yes
Checking for Matroska support ... yes
Checking for internal FAAD2 (AAC) support ... yes
Checking for external FAAD2 (AAC) support ... no
Checking for LADSPA plugin support ... no
Checking for Win32 codec DLL support ... yes (using /usr/local/lib/codecs)
Checking for Win32 loader support ... yes
Checking for DirectShow ... yes
Checking for XAnim DLL ... yes (using /usr/local/lib/codecs)
Checking for RealPlayer DLL ... yes (using /usr/local/lib/codecs)
Checking for LIVE.COM Streaming Media libraries ... no
Checking for FFmpeg libavcodec (static) ... yes
Checking for FFmpeg libavformat (static) ... yes
Checking for amr narrowband ... no
Checking for amr narrowband, fixed point ... no
Checking for amr wideband ... no
Checking for libdv-0.9.5+ ... no
Checking for zr ... no
Checking for bl ... no
Checking for XviD ... no
Checking for x264 ... no
Checking for DivX4linux/DivX5linux/OpenDivX decore ... no
Checking for libmp3lame (for mencoder) ... no
Checking for DivX4linux encore (for mencoder) ... no
Checking for mencoder ... yes
Checking for fastmemcpy ... yes
Checking for UniquE RAR File Library ... yes
Checking for TV interface ... yes
Checking for EDL support ... yes
Checking for *BSD BrookTree 848 TV interface ... no
Checking for Video 4 Linux TV interface ... no
Checking for Video 4 Linux 2 TV interface ... no
Checking for audio select() ... yes
Checking for network ... yes
Checking for ftp ... yes
Checking for vstream client ... no
Checking for byte order ... little-endian
Checking for shared postprocess lib ... no
Checking for OSD menu ... no
Checking for QTX codecs ... yes
Checking for Subtitles sorting ... yes
Checking for XMMS inputplugin support ... no
Checking for inet6 ... yes
Checking for gethostbyname2 ... yes
Checking for GUI ... yes
Checking for XShape extension ... yes
Checking for GTK version ... 1.2.10 (using gtk-config)
Checking for glib version ... 1.2.10 (using glib-config)
Creating Gui/config.mak
Checking for automatic gdb attach ... no
Checking for compiler support for -fno-PIC ... yes
Checking for ftello() ... yes
Checking for VIDIX ... yes
Checking for joystick ... no
Checking for lirc ... no
Checking for lircc ... no
Creating config.mak
Creating config.h
Creating libvo/config.mak
Creating libao2/config.mak
Creating libaf/config.mak

Config files successfully generated by ./configure !

  Install prefix: /usr/local
  Data directory: /usr/local/share/mplayer
  Config direct.: /usr/local/etc/mplayer

  Byte order: little-endian
  Optimizing for: pentium4 mmx mmx2 sse sse2 mtrr

  Languages:
    Messages/GUI: en
    Manual pages:  en

  Enabled optional drivers:
    Input: ftp network edl tv matroska mpdvdkit2 vcd dvb
    Codecs: qtx libavcodec real xanim dshow/dmo win32 faad2(internal) libmpeg2 liba52 mp3lib tremor(internal)
    Audio output: oss mpegpes(dvb)
    Video output: xvidix cvidix vesa md5sum pnm png mpegpes(dvb) fbdev opengl xv x11 xover tga
    Audio filters:
  Disabled optional drivers:
    Input: vstream tv-v4l2 tv-v4l tv-bsdbt848 live.com cdda dvdread smb
    Codecs: opendivx x264 xvid libdv amr_wb amr_nb libdts libtheora toolame libmad liblzo gif
    Audio output: sgi sun alsa jack polyp esd arts dxr2 nas dsound win32 sdl macosx
    Video output: winvidix bl zr zr2 dxr3 dxr2 directx sdl gif89a jpeg svga caca aa ggi xmga mga dga xvmc directfb tdfx_vid tdfxfb 3dfx quartz
    Audio filters: ladspa

'config.h' and 'config.mak' contain your configuration options.
Note: If you alter theses files (for instance CFLAGS) MPlayer may no longer
      compile *** DO NOT REPORT BUGS if you tweak these files ***

'make' will now compile MPlayer and 'make install' will install it.
Note: On non-Linux systems you might need to use 'gmake' instead of 'make'.

Please check mtrr settings at /proc/mtrr (see DOCS/HTML/en/video.html#mtrr)


Check configure.log if you wonder why an autodetection failed (check whether
the development headers/packages are installed).

If you suspect a bug, please read DOCS/HTML/en/bugreports.html.



if anyone could help me that would be great.

---

### Post by joshrobinson on 2006-04-09
you gota do

sudo apt-get install buld-essential

for all the make file stuff
once thats done downloading and installing you can do your make then make install

---

### Post by LiquidFlame on 2006-04-09
k little confused, i did the sudo apt-get install buld-essential and i got this output
> root@ubuntu:/home/liquidflame/MPlayer-1.0pre7try2# sudo apt-get install buld-essential
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package buld-essential


i do something wrong, im a little new to this

---

### Post by joshrobinson on 2006-04-09
[QUOTE=LiquidFlame]k little confused, i did the sudo apt-get install buld-essential and i got this output


i do something wrong, im a little new to this[/QUOTE]

hahaha no you didnt.. i spelled something wrong ](*,) 

sudo apt-get install build-essential

my bad :mad:

also did you put the codec's in the codec folder before you ./configure --enable-gui
if the codec's arent in the codec folder before you compile they wont be included

---

### Post by LiquidFlame on 2006-04-09
k great got it to install and run and can play my video files but i don't get any sound.  how do i tell it to use my sound card

---

### Post by joshrobinson on 2006-04-09
[QUOTE=LiquidFlame]k great got it to install and run and can play my video files but i don't get any sound.  how do i tell it to use my sound card[/QUOTE]

does it give you a failed to initialize audio device? do any kind of files work? mp3 avi mpg whatever?

did you put the codec's from the mplayer website in the codec folder before you compiled?

---

### Post by LiquidFlame on 2006-04-09
it doesn't give me any kind of errors, when i play a mp3 file, it plays but not sound.  as for the codec's im not sure what order i did it in, i just did it in the order as the site told my that i had as a link in the first post.  is there any way to find out?

---

### Post by nalmeth on 2006-04-09
Did you need to install a newer version of mplayer for some reason?
It can easily be installed in synaptic, but regardless you have it installed now. 
Do you have audio outside of mplayer - music etc?

---

### Post by LiquidFlame on 2006-04-09
yes i have audio outside of MPlayer like i said i just don't get sound when i trying to play files in MPlayer

---

### Post by joshrobinson on 2006-04-09
ok well im guessing its a codec thing.. 

you have to put the codec's in the codec folder before you did ./configure --enable-gui

you can always put them in the folder then re configure and make make install again and see if that works

if you dont get a failed to initialize error it has to be a codec

---

### Post by LiquidFlame on 2006-04-10
do i have to uninstall it first and the re-install it and do the make thing

---

### Post by Perfect Storm on 2006-04-10
You might want to go with this howto instead: [http://doc.gwos.org/index.php/Mplayer_cvs](http://doc.gwos.org/index.php/Mplayer_cvs)
You'll get the newest mplayer which also support GTK2 engine (graphical).

[[img]http://www.imageviper.com/displayimage/27894/0/smallmplayer.jpg[/img]]("http://www.imageviper.com/displayimage/27893/0/mplayer.jpg")
*[size=1]click to enlarge*[/size]


uninstall:
```
sudo make uninstall
```

---

### Post by LiquidFlame on 2006-04-10
ok will i uninstalled, and re did the steps and now when i try to play any time of file i get > Error: Could not open/initialize audio device -> no sound 

---

### Post by LiquidFlame on 2006-04-10
so after reading around i found out that i need to select esd EsounD Audio Output under the audio tab, but i don't have that option so it looks like that its not there/not installed does anyone no why or how to install that for mplayer, like i said i keep getting the error > Error: Could not open/initialize audio device -> no sound any help would be great

---

### Post by Perfect Storm on 2006-04-10
It should enable esd.

> Installation directories:
  --prefix=DIR           use this prefix for installing mplayer [/usr/local]
  --bindir=DIR           use this prefix for installing mplayer binary
                         [PREFIX/bin]
  --datadir=DIR          use this prefix for installing machine independent
                         data files (fonts, skins) [PREFIX/share/mplayer]
  --mandir=DIR           use this prefix for installing manpages [PREFIX/man]
  --confdir=DIR          use this prefix for installing configuration files
                         [PREFIX/etc/mplayer]
  --libdir=DIR           use this prefix for object code libraries [PREFIX/lib]

Optional features:
  --disable-mencoder     disable mencoder (a/v encoder) compilation [enable]
  --enable-gui           enable gmplayer compilation (GTK+ GUI) [disable]
  --enable-old-gtk       force using GTK 1.2 for GUI  [disable]
  --enable-largefiles    enable support for files > 2 GBytes [disable]
  --enable-linux-devfs   set default devices to devfs ones [disable]
  --enable-termcap       use termcap database for key codes [autodetect]
  --enable-termios       use termios database for key codes [autodetect]
  --disable-iconv        do not use iconv(3) function [autodetect]
  --disable-setlocale    disable setlocale using in mplayer [autodetect]
  --disable-langinfo     do not use langinfo [autodetect]
  --enable-lirc          enable LIRC (remote control) support [autodetect]
  --enable-lircc         enable LIRCCD (LIRC client daemon) input [autodetect]
  --enable-joystick      enable joystick support [disable]
  --disable-vm           disable support X video mode extensions [autodetect]
  --disable-xf86keysym   disable support for 'multimedia' keys [autodetect]
  --disable-tv           disable TV Interface (tv/dvb grabbers) [enable]
  --disable-tv-v4l       disable Video4Linux TV Interface support [autodetect]
  --disable-tv-v4l2      disable Video4Linux2 TV Interface support [autodetect]
  --disable-tv-bsdbt848  disable BSD BT848 Interface support [autodetect]
  --disable-edl          disable EDL (edit decision list) support [enable]
  --disable-rtc          disable RTC (/dev/rtc) on Linux [autodetect]
  --disable-network      disable network support (for: http/mms/rtp) [enable]
  --enable-winsock2      enable winsock2 usage [autodetect]
  --enable-smb           enable Samba (SMB) input support [autodetect]
  --enable-live          enable LIVE555 Streaming Media support [autodetect]
  --disable-dvdread      Disable libdvdread support [autodetect]
  --disable-mpdvdkit     Disable mpdvdkit2 support [autodetect]
  --disable-cdparanoia   Disable cdparanoia support [autodetect]
  --disable-freetype     Disable freetype2 font rendering support [autodetect]
  --disable-fontconfig   Disable fontconfig font lookup support [autodetect]
  --disable-unrarlib     Disable Unique RAR File Library [enabled]
  --enable-menu          Enable OSD menu support (NOT DVD MENU) [disabled]
  --disable-sortsub      Disable subtitles sorting [enabled]
  --enable-fribidi       Enable using the FriBiDi libs [autodetect]
  --disable-enca         Disable using ENCA charset oracle library [autodetect]
  --disable-macosx       Disable Mac OS X specific features [autodetect]
  --enable-macosx-finder-support  Enable Mac OS X Finder invocation parameter parsing [disabled]
  --enable-macosx-bundle Enable Mac OS X bundle file locations [autodetect]
  --disable-inet6        Disable IPv6 support [autodetect]
  --disable-gethostbyname2  gethostbyname() function is not provided by the C
                            library [autodetect]
  --disable-ftp          Disable ftp support [enabled]
  --disable-vstream      Disable tivo vstream client support [autodetect]
  --disable-pthreads     Disable Posix threads support [autodetect]

Codecs:
  --enable-gif           enable gif support [autodetect]
  --enable-png           enable png input/output support [autodetect]
  --enable-jpeg          enable jpeg input/output support [autodetect]
  --enable-libcdio       enable external libcdio support [autodetect]
  --enable-liblzo        enable external liblzo support [autodetect]
  --disable-win32        disable Win32 DLL support [autodetect]
  --disable-dshow        disable Win32/DirectShow support [autodetect]
  --disable-qtx          disable Quicktime codecs [autodetect]
  --disable-xanim        disable XAnim DLL support [autodetect]
  --disable-real         disable RealPlayer DLL support [autodetect]
  --disable-xvid         disable XviD codec [autodetect]
  --disable-x264         disable H.264 encoder [autodetect]
  --disable-divx4linux   disable DivX4linux/Divx5linux codec [autodetect]
  --enable-opendivx      enable _old_ OpenDivx codec [disable]
  --disable-libavcodec   disable libavcodec [autodetect]
  --disable-libavformat  disable libavformat [autodetect]
  --disable-libpostproc  disable libpostproc [autodetect]
  --disable-libavcodec_so  disable shared libavcodec [autodetect]
  --disable-libavformat_so disable shared libavformat [autodetect]
  --disable-libpostproc_so disable shared libpostproc [autodetect]
  --enable-libfame       enable libfame realtime encoder [autodetect]
  --disable-internal-tremor do not build internal OggVorbis support [enabled]
  --enable-tremor-low    build with lower accuracy internal tremor [disabled]
  --enable-external-tremor build with external tremor [disabled]
  --disable-vorbis       disable OggVorbis support entirely [autodetect]
  --disable-speex        disable Speex support [autodetect]
  --enable-theora        build with OggTheora support [autodetect]
  --disable-internal-matroska disable internal Matroska support [enabled]
  --enable-external-faad build with external FAAD2 (AAC) support [autodetect]
  --disable-internal-faad disable internal FAAD2 (AAC) support [autodetect]
  --disable-faac         disable support for FAAC (AAC encoder) [autodetect]
  --disable-ladspa       disable LADSPA plugin support [autodetect]
  --disable-libdv        disable libdv 0.9.5 en/decoding support [autodetect]
  --disable-mad          disable libmad (MPEG audio) support [autodetect]
  --disable-toolame      disable Toolame (MPEG layer 2 audio) support in mencoder [autodetect]
  --disable-twolame      disable Twolame (MPEG layer 2 audio) support in mencoder [autodetect]
  --enable-xmms          build with XMMS inputplugin support [disabled]
  --disable-mp3lib       disable builtin mp3lib [enabled]
  --disable-liba52       disable builtin liba52 [enabled]
  --enable-libdts        enable libdts support [autodetect]
  --disable-libmpeg2     disable builtin libmpeg2 [enabled]
  --disable-musepack     disable musepack support [autodetect]
  --disable-amr_nb       disable amr narrowband, floating point [autodetect]
  --disable-amr_nb-fixed disable amr narrowband, fixed point [autodetect]
  --disable-amr_wb       disable amr wideband, floating point [autodetect]
  --disable-codec=CODEC  disable specified codec
  --enable-codec=CODEC   dnable specified codec

Video output:
  --disable-internal-vidix disable internal VIDIX [for x86 *nix]
  --disable-external-vidix disable external VIDIX [for x86 *nix]
  --enable-gl            build with OpenGL render support [autodetect]
  --enable-dga[=n]       build with DGA [n in {1, 2} ] support [autodetect]
  --enable-vesa          build with VESA support [autodetect]
  --enable-svga          build with SVGAlib support [autodetect]
  --enable-sdl           build with SDL render support [autodetect]
  --enable-aa            build with AAlib render support [autodetect]
  --enable-caca          build with CACA render support [autodetect]
  --enable-ggi           build with GGI render support [autodetect]
  --enable-ggiwmh        build with GGI libggiwmh extension [autodetect]
  --enable-directx       build with DirectX support [autodetect]
  --enable-dxr2          build with DXR2 render support [autodetect]
  --enable-dxr3          build with DXR3/H+ render support [autodetect]
  --enable-dvb           build with support for output via DVB-Card [autodetect]  --enable-dvbhead       build with DVB support (HEAD version) [autodetect]
  --enable-mga           build with mga_vid (for Matrox G200/G4x0/G550) support
                         (check for /dev/mga_vid) [autodetect]
  --enable-xmga          build with mga_vid X Window support
                         (check for X & /dev/mga_vid) [autodetect]
  --enable-xv            build with Xv render support for X 4.x [autodetect]
  --enable-xvmc          build with XvMC acceleration for X 4.x [disable]
  --enable-vm            build with XF86VidMode support for X11 [autodetect]
  --enable-xinerama      build with Xinerama support for X11 [autodetect]
  --enable-x11           build with X11 render support [autodetect]
  --enable-fbdev         build with FBDev render support [autodetect]
  --enable-mlib          build with MLIB support (Solaris only) [autodetect]
  --enable-3dfx          build with obsolete /dev/3dfx support [disable]
  --enable-tdfxfb        build with tdfxfb (Voodoo 3/banshee) support [disable]
  --enable-directfb      build with DirectFB support [autodetect]
  --enable-zr            build with ZR360[56]7/ZR36060 support [autodetect]
  --enable-bl            build with Blinkenlights support [disable]
  --enable-tdfxvid       build with tdfx_vid support [disable]
  --disable-tga          disable targa output support [enable]
  --disable-pnm          disable pnm output support [enable]
  --disable-md5sum       disable md5sum output support [enable]

Audio output:
  --disable-alsa         disable ALSA sound support [autodetect]
  --disable-ossaudio     disable OSS sound support [autodetect]
  --disable-arts         disable aRts sound support [autodetect]
  **--disable-esd          disable esd sound support [autodetect]**
  --disable-polyp        disable Polypaudio sound support [autodetect]
  --disable-jack         disable JACK sound support [autodetect]
  --disable-openal       disable OpenAL sound support [autodetect]
  --disable-nas          disable NAS sound support [autodetect]
  --disable-sgiaudio     disable SGI sound support [autodetect]
  --disable-sunaudio     disable Sun sound support [autodetect]
  --disable-win32waveout disable Windows waveout sound support [autodetect]
  --disable-select       disable using select() on audio device [enable]

Miscellaneous options:
  --enable-runtime-cpudetection    Enable runtime CPU detection [disable]
  --enable-cross-compile Enable cross-compilation [autodetect]
  --cc=COMPILER          use this C compiler to build MPlayer [gcc]
  --host-cc=COMPILER     use this C compiler to build apps needed for the build process [gcc]
  --as=ASSEMBLER         use this assembler to build MPlayer [as]
  --target=PLATFORM      target platform (i386-linux, arm-linux, etc)
  --enable-static        build a statically linked binary. Set further linking
                         options with --enable-static="-lslang -lncurses"
  --charset              convert the help messages to this charset
  --language=list        a white space or comma separated list of languages
                         for translated man pages, the first language is the
                         primary and therefore used for translated messages
                         and GUI (also the environment variable $LINGUAS is
                         honored) [en]
                         (Available: bg cs de dk el en es fr hu it ja ko mk nl no pl ro ru sk sv tr uk pt_BR zh_CN zh_TW all)
  --with-install=PATH    use a custom install program (useful if your OS uses
                         a GNU-incompatible install utility by default and
                         you want to use GNU version)
  --install-path=PATH    the path to a custom install program
                         this option is obsolete and will be removed soon,
                         use --with-install instead.

Advanced options:
  --enable-mmx           build with MMX support [autodetect]
  --enable-mmx2          build with MMX2 support (PIII, Athlon) [autodetect]
  --enable-3dnow         build with 3DNow! support [autodetect]
  --enable-3dnowex       build with extended 3DNow! support [autodetect]
  --enable-sse           build with SSE support [autodetect]
  --enable-sse2          build with SSE2 support [autodetect]
  --enable-shm           build with shm support [autodetect]
  --enable-altivec       build with Altivec support (PowerPC) [autodetect]
  --disable-fastmemcpy   disable 3DNow!/SSE/MMX optimized memcpy() [enable]
  --enable-big-endian    Force byte order to big-endian [autodetect]
  --enable-debug[=1-3]   compile debugging information into mplayer [disable]
  --enable-profile       compile profiling information into mplayer [disable]
  --disable-sighandler   disable sighandler for crashes [enable]
  --enable-crash-debug   enable automatic gdb attach on crash [disable]
  --enable-dynamic-plugins  Enable support for dynamic a/v plugins [disable]

Hazardous options a.k.a. "DO NOT REPORT ANY BUGS!"
  --disable-gcc-checking   disable gcc version checking [enable]

Use these options if autodetection fails (Options marked with (*) accept
multiple paths separated by ':'):
  --with-extraincdir=DIR   extra headers (png, mad, sdl, ...) in DIR (*)
  --with-extralibdir=DIR   extra library files (png, mad, sdl, ...) in DIR (*)
  --with-x11incdir=DIR     X headers in DIR (*)
  --with-x11libdir=DIR     X library files in DIR (*)
  --with-dxr2incdir=DIR    DXR2 headers in DIR (*)
  --with-dvbincdir=DIR     DVB headers in DIR (*)
  --with-madlibdir=DIR     libmad (libmad shared library) in DIR (*)
  --with-mlibdir=DIR       libmlib (MLIB support) in DIR (Solaris only)
  --with-codecsdir=DIR     Binary codec files in DIR
  --with-win32libdir=DIR   W*ndows DLL files in DIR
  --with-xanimlibdir=DIR   XAnim DLL files in DIR
  --with-reallibdir=DIR    RealPlayer DLL files in DIR
  --with-xvidlibdir=DIR    libxvidcore (XviD) in DIR  (*)
  --with-xvidincdir=DIR    XviD header in DIR (*)
  --with-x264libdir=DIR    libx264 in DIR
  --with-x264incdir=DIR    x264 header in DIR
  --with-dtslibdir=DIR     libdts library in DIR  (*)
  --with-dtsincdir=DIR     libdts header in DIR (*)
  --with-livelibdir=DIR    LIVE555 Streaming Media libraries in DIR
  --with-toolamedir=DIR    path to Toolame library and include file
  --with-xmmsplugindir=DIR XMMS plugins in DIR
  --with-xmmslibdir=DIR    libxmms.so.1 in DIR
  --with-cdparanoiaincdir=DIR  cdparanoia headers in DIR (*)
  --with-cdparanoialibdir=DIR  cdparanoia libraries (libcdda_*) in DIR (*)
  --with-xvmclib=NAME      name of adapter-specific library (e.g. XvMCNVIDIA)
  --with-termcaplib=NAME   name of library with termcap functionality
                           name should be given without leading "lib"
                           checks for "termcap" and "tinfo"

  --with-freetype-config=PATH path to freetype-config
                              (e.g. /opt/bin/freetype-config)
  --with-fribidi-config=PATH  path to fribidi-config
                              (e.g. /opt/bin/fribidi-config)
  --with-glib-config=PATH  path to glib*-config (e.g. /opt/bin/glib-config)
  --with-gtk-config=PATH   path to gtk*-config (e.g. /opt/bin/gtk-config)
  --with-sdl-config=PATH   path to sdl*-config (e.g. /opt/bin/sdl-config)

This configure script is NOT autoconf-based, even though its output is similar.
It will try to autodetect all configuration options. If you --enable an option
it will be forcefully turned on, skipping autodetection. This can break
compilation, so you need to know what you are doing.


Look under **Audio output**:As you can see esd is set to auto-detect by default. The problem might lies elsewhere. Have you tried other sound options?


You have libmikmod-dev and esound, esound-commen installed?


EDIT: You could try running this command before starting mplayer:
```
killall esd
```
See if it helps.

---

