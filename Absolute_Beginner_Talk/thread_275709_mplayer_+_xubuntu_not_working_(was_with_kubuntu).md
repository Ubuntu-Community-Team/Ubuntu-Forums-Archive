---
title: "mplayer + xubuntu not working (was with kubuntu)"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by guysmiley25 on 2006-10-11
I can't get mplayer to play dvd's in xubuntu, but it does work in kubuntu on the same machine!!! Can anyone help? also while your here I can't get wmv's to play. I installed w32codecs and it open's and looks like its playing but I can not see anything? avi etc are fine.

Here is my error when I ran
$ mplayer dvd://1

```

MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel Pentium 4 Willamette; Xeon Foster (Family: 15, Stepping: 10)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


91 audio & 204 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing dvd://1.
libdvdread: Using libdvdcss version 1.2.5 for DVD access
Reading disc structure, please wait...
There are 2 titles on this DVD.
There are 36 chapters in this DVD title.
There are 1 angles in this DVD title.

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000011f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0000040c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000006a7
libdvdread: Elapsed time 0
libdvdread: Found 1 VTS's
libdvdread: Elapsed time 0
DVD successfully opened.
MPEG-PS file format detected.
VIDEO:  MPEG2  720x576  (aspect 3)  25.000 fps  7500.0 kbps (937.5 kbyte/s)
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
AC3: 2.0 (dolby)  48000 Hz  192.0 kbit/s
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 576 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
Building audio filter chain for 48000Hz/2ch/s16le -> 0Hz/0ch/??...
alsa-init: 1 soundcard found, using: default
alsa: 48000 Hz/2 channels/4 bpf/65536 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Building audio filter chain for 48000Hz/2ch/s16le -> 48000Hz/2ch/s16le...
Starting playback...
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 720x576 => 1024x576 Planar YV12
X11 error: BadAlloc (insufficient resources for operation)?,?% 3 0


MPlayer interrupted by signal 6 in module: vo_check_events
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
alsa-uninit: pcm closed

```

Any Ideas?

---

### Post by guysmiley25 on 2006-10-14
Any one?

---

