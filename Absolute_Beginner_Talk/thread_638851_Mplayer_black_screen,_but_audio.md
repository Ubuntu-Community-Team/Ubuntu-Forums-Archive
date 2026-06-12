---
title: "Mplayer black screen, but audio"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by SpinningAround on 2007-12-12
I tried to play a .avi file in mplayer, the sound was ok but the screen was black. Don't got a clue where to start :confused:

The output from command mplayer (movie)
```

MPlayer 2:1.0~rc1-0ubuntu13.1 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Celeron(R) M CPU        530  @ 1.73GHz (Family: 6, Model: 22, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing #.avi.
AVI file format detected.
VIDEO:  [XVID]  640x352  12bpp  25.000 fps  1024.0 kbps (125.0 kbyte/s)
Clip info:
 Software: VirtualDubMod 1.5.10.2 (build 2540/release)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 640 x 352 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.82:1 - prescaling to correct movie aspect.
VO: [xv] 640x352 => 640x352 Planar YV12 

```


Have ATI X1100 with the correct drivers.

---

### Post by philinux on 2007-12-12
When its playing right click then configure. Select video output at top to be X11. See if that fixes it.

Check out the mutlimedia link below

---

### Post by SpinningAround on 2007-12-13
Got it working thanks :D

---

### Post by ImALittleTeaPot on 2007-12-14
Hello, 

I pressed X11 and now have video where none was before(thanks for that!), but the mplayer firefox plugin video has a 'squashed' appearence and has has poor audio. Any know what this problem might be?

thanks.

---

