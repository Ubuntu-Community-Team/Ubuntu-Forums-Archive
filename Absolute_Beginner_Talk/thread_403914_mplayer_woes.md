---
title: "mplayer woes"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by fuscia on 2007-04-07
tried to play a dvd using mplayer. i did *mplayer dvd://*. it didn't work. i'm not even sure what to ask. here's what i got...

[i]MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Celeron(R) M processor         1.60GHz (Family: 6, Model: 13, Step
ping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup 
scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.

Playing dvd://.
Reading disc structure, please wait...
There are 8 titles on this DVD.
There are 1 chapters in this DVD title.
There are 1 angles in this DVD title.
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_1.VOB (0x0000e815)!!
DVD successfully opened.
MPEG-PS file format detected.
MPEG: No audio stream found -> no sound.
VIDEO:  MPEG2  720x480  (aspect 2)  29.970 fps  3000.0 kbps (375.0 kbyte/s)
open: No such file or directory
Couldn't open: /dev/mga_vid
open: No such file or directory
Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 480 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
Audio: no sound
Starting playback...
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x480 => 720x540 Planar YV12 
V:   1.2  30/ 30  6%  1%  0.0% 0 0 

Exiting... (End of file)[/i]

---

### Post by PriceChild on 2007-04-07
*approved & bumped*

---

### Post by %hMa@?b&lt;C on 2007-04-07
MPEG-PS file format detected.
MPEG: No audio stream found -> no sound.
VIDEO: MPEG2 720x480 (aspect 2) 29.970 fps 3000.0 kbps (375.0 kbyte/s)
open: No such file or directory
Couldn't open: /dev/mga_vid
open: No such file or directory
Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.

it cant find sound, cant open 3d, do those usually work? can you try in totem/something else

---

### Post by fuscia on 2007-04-07
> **jeffc313 said:**
> MPEG-PS file format detected.
MPEG: No audio stream found -> no sound.
VIDEO: MPEG2 720x480 (aspect 2) 29.970 fps 3000.0 kbps (375.0 kbyte/s)
open: No such file or directory
Couldn't open: /dev/mga_vid
open: No such file or directory
Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.

it cant find sound, cant open 3d, do those usually work? can you try in totem/something else

oh, it's fine in kmplayer and kaffeine (any xine thing). i just want it to work in mplayer as it has become my latest darling.

---

