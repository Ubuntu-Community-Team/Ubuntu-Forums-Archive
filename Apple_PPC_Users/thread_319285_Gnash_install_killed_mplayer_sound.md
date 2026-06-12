---
title: "Gnash install killed mplayer sound"
date: 2006-12-15
forum: Apple PPC Users
---

### Post by ubuntubrian on 2006-12-15
Hopefully there's some help for my problem. I had mplayer working great
and playing .wmv files just fine. I installed Gnash to play flash and
installed it from source. I didn't select any options when I installed
Gnash and it does play flash in firefox-great!
But now I have no sound in mplayer for any video type, .wmv, mpeg, .mov,
etc.
I get this in a terminal. Help is greatly appreciated and many thanks!
Happy holidays! Oh, I can play mpegs with vlc or totem and the sound is
fine so I don't understand the error.

mplayer /home/brianokeefe/Desktop/geniusbird.wmv
MPlayer dev-SVN-r19849-4.0.3 (C) 2000-2006 MPlayer Team
AltiVec found
CPU: PowerPC

Playing /home/brianokeefe/Desktop/geniusbird.wmv.
ASF file format detected.
VIDEO:  [WMV3]  320x240  24bpp  1000.000 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Requested video codec family [wmv9dmo] (vfm=dmo) not available.
Enable it at compilation.
Requested video codec family [wmvdmo] (vfm=dmo) not available.
Enable it at compilation.
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffwmv3] vfm: ffmpeg (FFmpeg M$ WMV3/WMV9)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 22050 Hz, 1 ch, s16be, 20.0 kbit/5.67% (ratio: 2501->44100)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))
==========================================================================
[AO OSS] audio_setup: Can't open audio device /dev/dsp: Device or
resource busy
ao_nas: init(): Can't open nas audio server -> nosound
Opening /dev/dvb/adapter0/audio0
DVB AUDIO DEVICE: No such file or directory
AO: [null] 22050Hz 1ch s16be (2 bytes per sample)
Starting playback...
VDec: vo config request - 320 x 240 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [x11] 320x240 => 320x240 Planar YV12
SwScaler: using unscaled 0x32315659 (21VY) -> 0x42475220 (BGR ) special
converter
A:   7.6 V:   7.6 A-V:  0.006 ct: -0.044  70/ 70 12%  5%  0.9% 2 0
Exiting... (Quit)

I checked my mplayer.conf file and found 
##################
# audio settings #
##################

# Specify default audio driver (see -ao help for a list).
ao=alsa,oss,sdl,esd,arts

# Use SDL audio driver with the esd subdriver by default.
#ao = sdl:esd

# Specify the mixer device.
#mixer = /dev/mixer

# Resample the sound to 44100Hz with the lavcresample audio filter.
#af=lavcresample=44100

---

### Post by ubuntubrian on 2006-12-15
Another idea-I updated the kernel to 2.6.15-27 and in reading the Alsa info in synaptic:
"For ALSA to work on a system with a given sound card,
there must be an ALSA driver for that card in the kernel.
Linux 2.6 as shipped in linux-image packages contains
ALSA drivers for all supported sound cards in the form
of loadable modules. For either Linux 2.6 or Linux 2.4
a custom alsa-modules package can be built from the
sources in the alsa-source package using the make-kpkg
utility (included in the kernel-package package). Some
pre-built alsa-modules packages are available in the
Debian archive. Please read the README.Debian file for
information about loading modules."


Would this have any relevance?

---

### Post by ubuntubrian on 2006-12-15
More info. I ran in a terminal:
@ubuntu:~$ mplayer -ao help
MPlayer dev-SVN-r19849-4.0.3 (C) 2000-2006 MPlayer Team
AltiVec found
CPU: PowerPC
Available audio output drivers:
        oss     OSS/ioctl audio output
        nas     NAS audio output
        mpegpes DVB audio output
        null    Null audio output
        pcm     RAW PCM/WAVE file writer audio output
 
And I see no alsa driver at all. I have the alsa wrapper for oss installed. Is that sufficient?

---

### Post by ubuntubrian on 2006-12-15
It seems that I can run 'killall esd' and mplayer has sound. I don't know what app is using esd as mplayer has no sound even after restarting. I thought that I saw a post to create a script to do this on logout/in and booting but I don't know where.

---

