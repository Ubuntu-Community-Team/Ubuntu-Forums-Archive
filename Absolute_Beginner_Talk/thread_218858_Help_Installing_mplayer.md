---
title: "Help Installing mplayer"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by James_N on 2006-07-19
Hi

Following this guide: [http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/15076-ubuntu-multimedia-howto.html](http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/15076-ubuntu-multimedia-howto.html)
Im trying to install mplayer (but using the latest versions of these).

Ive got as far as:

> Time to compile MPlayer. Issue these commands.

$ tar -xjf MPlayer-1.0pre5.tar.bz2
$ cd MPlayer-1.0pre5
$ ./configure --enable-gui

the ./configure --enable-gui worked
```

root@jimbo-desktop:/home/jimbo/MPlayer-1.0pre8# ./configure --enable-gui
Detected operating system: Linux
Detected host architecture: i386
Checking for cc version ... 4.0.3, ok
Checking for host cc ... cc
Checking for cross compilation ... no
Checking for CPU vendor ... AuthenticAMD (15:31:0)
Checking for CPU type ...  AMD Athlon(tm) 64 Processor 3200+
Checking for GCC & CPU optimization abilities ... k8
Checking for kernel support of mmx ... yes
Checking for kernel support of mmxext ... yes
Checking for kernel support of 3dnow ... yes
Checking for kernel support of 3dnowext ... yes
Checking for kernel support of sse ... yes
Checking for kernel support of sse2 ... yes
Checking for mtrr support ... yes
Checking for xmmintrin.h ... yes
Checking for mm3dnow.h ... yes
Checking for assembler support of -pipe option ... yes
Checking for assembler (as 2.16.91) ... ok
Checking for Linux kernel version ... 2.6.15-26-386, ok
Checking for MPlayer binary name ... mplayer
Checking for awk ... mawk
Checking for extra headers ... none
Checking for extra libs ... none
Checking for -lposix ... no
Checking for -lm ... yes
Checking for langinfo ... yes
Checking for language ... using en (man pages:  en)
Checking for enable sighandler ... yes
Checking for runtime cpudetection ... no
Checking for restrict keyword ... __restrict
Checking for __builtin_expect ... yes
Checking for kstat ... no
Checking for posix4 ... no
Checking for lrintf ... yes
Checking for round ... yes
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
Checking for rpath ... no
Checking for iconv ... yes
Checking for sys/soundcard.h ... yes
Checking for sys/dvdio.h ... no
Checking for sys/cdio.h ... no
Checking for linux/cdrom.h ... yes
Checking for dvd.h ... no
Checking for BSDI dvd.h ... no
Checking for HP-UX SCSI header ... no
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
Checking for POSIX select() ... yes
Checking for gettimeofday() ... yes
Checking for glob() ... yes
Checking for setenv() ... yes
Checking for sys/sysinfo.h ... yes
Checking for Mac OS X APIs ... auto
Checking for Mac OS X Finder Support ... no
Checking for Mac OS X Bundle file locations ... no
Checking for Samba support (libsmbclient) ... no
Checking for 3dfx ... no
Checking for tdfxfb ... no
Checking for s3fb ... no
Checking for tdfxvid ... no
Checking for tga ... yes
Checking for DirectFB headers presence ... not found
Checking for DirectFB ... no
Checking for X11 headers presence ... yes (using /usr/include)
Checking for X11 ... yes (using /usr/X11R6/lib)
Checking for DPMS ... yes (using Xdpms 4)
Checking for Xv ... no
Checking for XvMC ... no
Checking for Xinerama ... no
Checking for Xxf86vm ... no
Checking for XF86keysym ... yes
Checking for DGA ... no
Checking for OpenGL ... no
Checking for /dev/mga_vid ... no
Checking for xmga ... no
Checking for GGI ... no
Checking for GGI extension: libggiwmh ... no
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
Checking for VESA support ... no
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
Checking for OpenAL ... no
Checking for ALSA audio ... no
Checking for Sun audio ... no
Checking for Sun mediaLib ... no
Checking for SGI audio ... no
Checking for VCD support ... yes
Checking for DVD support (libmpdvdkit2) ... yes
Checking for DVD support (libdvdread) ... no (disabled by libmpdvdkit2)
Checking for cdparanoia ... no
Checking for libcdio ... no
Checking for freetype >= 2.0.9 ... no
Checking for fontconfig ... no (freetype support needed)
Checking for fribidi with charsets ... no
Checking for ENCA ... no
Checking for zlib ... yes
Checking for RTC ... yes
Checking for external liblzo support ... no
Checking for mad support ... no
Checking for Toolame ... no
Checking for Twolame ... no
Checking for OggVorbis support ... yes (internal Tremor)
Checking for libspeex (version >= 1.1 required) ... no
Checking for OggTheora support ... no
Checking for mp3lib support ... yes
Checking for liba52 support ... yes
Checking for libdts support ... no
Checking for libmpeg2 support ... yes
Checking for libmpcdec (musepack, version >= 1.2.1 required) ... no
Checking for FAAC (AAC encoder) support ... no
Checking for internal FAAD2 (AAC) support ... yes
Checking for external FAAD2 (AAC) support ... no
Checking for LADSPA plugin support ... no
Checking for Win32 codec DLL support ... yes (using /usr/local/lib/codecs)
Checking for Win32 loader support ... yes
Checking for DirectShow ... yes
Checking for XAnim DLL ... yes (using /usr/local/lib/codecs)
Checking for RealPlayer DLL ... yes (using /usr/local/lib/codecs)
Checking for LIVE555 Streaming Media libraries ... no
Checking for FFmpeg libavutil (static) ... yes
Checking for FFmpeg libavcodec (static) ... yes
Checking for FFmpeg libavformat (static) ... yes
Checking for FFmpeg libpostproc (static) ... yes
Checking for AMR narrowband ... no
Checking for AMR narrowband, fixed point ... no
Checking for AMR wideband ... no
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
Checking for *BSD BrookTree 848 TV interface ... no
Checking for Video 4 Linux TV interface ... yes
Checking for Video 4 Linux 2 TV interface ... yes
Checking for audio select() ... yes
Checking for network ... yes
Checking for ftp ... yes
Checking for vstream client ... no
Checking for byte order ... little-endian
Checking for OSD menu ... no
Checking for QTX codecs ... yes
Checking for Subtitles sorting ... yes
Checking for XMMS inputplugin support ... no
Checking for inet6 ... yes
Checking for gethostbyname2 ... yes
Checking for GUI ... yes
Checking for XShape extension ... yes
Checking for GTK+ version ... GTK-2 devel packages were not found, trying GTK 1.2
Checking for GTK version ... 1.2.10 (using gtk-config)
Checking for glib version ... 1.2.10 (using glib-config)
Creating Gui/config.mak
Checking for automatic gdb attach ... no
Checking for compiler support for -fno-PIC ... yes
Checking for compiler support for noexecstack ... yes
Checking for ftello() ... yes
Checking for VIDIX (internal) ... yes
Checking for VIDIX (external) ... no
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
  Optimizing for: k8 mmx mmxext 3dnow 3dnowext sse sse2 mtrr

  Languages:
    Messages/GUI: en
    Manual pages:  en

  Enabled optional drivers:
    Input: ftp network tv-v4l2 tv-v4l tv mpdvdkit2 vcd dvb
    Codecs: qtx libavcodec real xanim dshow/dmo win32 faad2(internal) libmpeg2 liba52 mp3lib tremor(internal)
    Audio output: oss mpegpes(dvb)
    Video output: xvidix cvidix md5sum pnm png mpegpes(dvb) fbdev x11 xover tga
    Audio filters:
  Disabled optional drivers:
    Input: vstream tv-bsdbt848 live555 cdda dvdread smb
    Codecs: opendivx x264 xvid libdv amr_wb amr_nb faac musepack libdts libtheora speex twolame toolame libmad liblzo gif
    Audio output: sgi sun alsa openal jack polyp esd arts dxr2 nas dsound win32 sdl
    Video output: winvidix bl zr zr2 dxr3 dxr2 directx sdl vesa gif89a jpeg svga caca aa ggi xmga mga opengl dga xvmc xv directfb tdfx_vid s3fb tdfxfb 3dfx
    Audio filters: ladspa

'config.h' and 'config.mak' contain your configuration options.
Note: If you alter theses files (for instance CFLAGS) MPlayer may no longer
      compile *** DO NOT REPORT BUGS if you tweak these files ***

'make' will now compile MPlayer and 'make install' will install it.
Note: On non-Linux systems you might need to use 'gmake' instead of 'make'.

Please check mtrr settings at /proc/mtrr (see DOCS/HTML/en/video.html#mtrr)


Check configure.log if you wonder why an autodetection failed (check whether
the development headers/packages are installed).
Do not report compilation errors if you used any of the --enable-* options
(except --enable-gui and maybe --enable-debug).

If you suspect a bug, please read DOCS/HTML/en/bugreports.html.

```

and then it said to type "make" but i get this:

```

root@jimbo-desktop:/home/jimbo/MPlayer-1.0pre8# make
bash: make: command not found

```

What am i doing wrong ](*,) 

Thanks :)

---

### Post by madmetal on 2006-07-19
try first 

sudo aptitude install build-essential

---

### Post by mogelhead on 2006-07-19
Are you sure you wanto compile mplayer from source? That guide seem a little old, from 2004.

If you are using Ubuntu 6.06 (Dapper Drake), it's very easy to install mplayer. (Already built for you, ready to use.) 

[Enable the multiverse repository]("https://help.ubuntu.com/community/Repositories/Ubuntu") and then use this command in the terminal:
```
sudo apt-get install mplayer
```

But the guide references a good article: [http://wiki.ubuntu.com/RestrictedFormats](http://wiki.ubuntu.com/RestrictedFormats), which is useful for setting up all the codecs.

---

### Post by James_N on 2006-07-19
> **mogelhead said:**
> Are you sure you wanto compile mplayer from source? That guide seem a little old, from 2004.

If you are using Ubuntu 6.06 (Dapper Drake), it's very easy to install mplayer. (Already built for you, ready to use.) Just use this command in the terminal:
```
sudo apt-get install mplayer
```

But the guide references a good article: [http://wiki.ubuntu.com/RestrictedFormats](http://wiki.ubuntu.com/RestrictedFormats), which is useful for setting up all the codecs.


Hi

Thanks for this. But i get

```

jimbo@jimbo-desktop:~$ sudo apt-get install mplayer
Reading package lists... Done
Building dependency tree... Done
Package mplayer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mplayer has no installation candidate
jimbo@jimbo-desktop:~$

```

---

### Post by James_N on 2006-07-19
> **madmetal said:**
> try first 

sudo aptitude install build-essential

Thanks that worked, just tried "make" and its doing lots of things. I'll see if it installs ok.

---

### Post by mogelhead on 2006-07-19
> E: Package mplayer has no installation candidate
Yes, sorry. I realised that you have to [enable the multiverse repository]("https://help.ubuntu.com/community/Repositories/Ubuntu") first.

---

### Post by madmetal on 2006-07-19
"make" is doing a lot of things but i also suggest what mogelhead suggested.
using synaptic or aptitute to install ready packets is better and easier(for noobs like me:) )

---

### Post by James_N on 2006-07-19
right, it plays but i get this in terminal

```

93 audio & 211 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts
```

It plays AVI file fine but then this:

[[IMG]http://img80.imageshack.us/img80/8927/screenshotya3.th.png[/IMG]](http://img80.imageshack.us/my.php?image=screenshotya3.png)

[[IMG]http://img214.imageshack.us/img214/934/screenshot1qn0.th.png[/IMG]](http://img214.imageshack.us/my.php?image=screenshot1qn0.png)

Thats not good is it :(

---

### Post by James_N on 2006-07-19
> **mogelhead said:**
> Yes, sorry. I realised that you have to [enable the multiverse repository]("https://help.ubuntu.com/community/Repositories/Ubuntu") first.

Done that and it seems to work fine now - Many thanks to all that helped.

One last thing though. The video sizes seem very small. I mean, some videos that i have played full screen in windows only come up in a tiny window with mplayer. Ive tried clicking fullscreen but all i get is the blue border round my very small video.

Any way of fixing this?

Many thanks again, your all very helpfull :)

---

### Post by Perfect Storm on 2006-07-19
> 93 audio & 211 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts


```
sudo gedit /etc/sysctl.conf
```

add: **dev.rtc.max-user-freq=1024**

Then:
```
sudo /etc/init.d/procps.sh restart
```

If you still want to compile it you should go for the latest version (svn)
svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer

also check mplayerplug-in for the browser: [http://mplayerplug-in.sourceforge.net/](http://mplayerplug-in.sourceforge.net/)


> One last thing though. The video sizes seem very small. I mean, some videos that i have played full screen in windows only come up in a tiny window with mplayer. Ive tried clicking fullscreen but all i get is the blue border round my very small video.
Try change video driver to xv in mplayer.

---

### Post by James_N on 2006-07-19
> **Artificial Intelligence said:**
> 
Try change video driver to xv in mplayer.

Tried that and it failed to open any video at all, just came up with fatal error :(

This is what im on about:

[[IMG]http://img507.imageshack.us/img507/7372/screenshothj1.th.png[/IMG]](http://img507.imageshack.us/my.php?image=screenshothj1.png)

You can see how big the screen is and how small the picture in the middle is :(

Thanks again.

---

### Post by James_N on 2006-07-20
well mplayer did work fine but now i get no sound no matter what i do.

I get the error: "Could not open/initialize audio device > no sound"

Yet i can play MP3's fine in XMMS but i get no sound in movies no matter what i use to play them with.

Any ideas please? :)

---

