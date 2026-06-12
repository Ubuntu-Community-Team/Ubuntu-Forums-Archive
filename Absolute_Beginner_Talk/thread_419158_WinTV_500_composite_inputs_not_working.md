---
title: "WinTV 500 composite inputs not working"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by arnabbiswas on 2007-04-22
Hi,

I am using Ubuntu Feisty which comes preinstaled with te ivtv drivers for this card.

When I try to view trough the composite inputs of card 1 I dont get any picture. I see a black screen with snow. Here is the output:

arnab@mythbox:~$ mplayer /dev/video0
MPlayer 2:1.0~rc1-0ubuntu9 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3000+ (Family: 15, Model: 47, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /dev/video0.
Win32 LoadLibrary failed to load: avisynth.dll, /usr/lib/win32/avisynth.dll, /usr/local/lib/win32/avisynth.dll
MPEG-PS file format detected.
VIDEO:  MPEG2  720x480  (aspect 2)  29.970 fps  8000.0 kbps (1000.0 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
It seems there is no Xvideo support for your video card available.
Run 'xvinfo' to verify its Xv support and read DOCS/HTML/en/video.html#xv!
See 'mplayer -vo help' for other (non-xv) video out drivers. Try -vo x11
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
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 224.0 kbit/14.58% (ratio: 28000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [x11] 720x480 => 720x540 Planar YV12 
SwScaler: using unscaled yuv420p -> rgb32 special converter
A:   9.1 V:   8.7 A-V:  0.456 ct: -0.359 237/237 12% 21% 57.8% 75 0 

           ************************************************
           **** Your system is too SLOW to play this!  ****
           ************************************************

Possible reasons, problems, workarounds:
- Most common: broken/buggy _audio_ driver
  - Try -ao sdl or use the OSS emulation of ALSA.
  - Experiment with different values for -autosync, 30 is a good start.
- Slow video output
  - Try a different -vo driver (-vo help for a list) or try -framedrop!
- Slow CPU
  - Don't try to play a big DVD/DivX on a slow CPU! Try some of the lavdopts,
    e.g. -vfm ffmpeg -lavdopts lowres=1:fast:skiploopfilter=all.
- Broken file
  - Try various combinations of -nobps -ni -forceidx -mc 0.
- Slow media (NFS/SMB mounts, DVD, VCD etc)
  - Try -cache 8192.
- Are you using -cache to play a non-interleaved AVI file?
  - Try -nocache.
Read DOCS/HTML/en/video.html for tuning/speedup tips.
If none of this helps you, read DOCS/HTML/en/bugreports.html.

A:  11.3 V:  11.0 A-V:  0.253 ct: -0.362 307/307 11% 19% 59.6% 140 0 

MPlayer interrupted by signal 2 in module: decode_audio

But when I try to view from the coax in of this card, I can see te video fine.

Any thoughts please?

---

### Post by jiminycricket on 2007-04-22
I would file a bug at launchpad.net and see where they direct you from there.

---

### Post by arnabbiswas on 2007-04-24
Looks like the problem here is that the card is tuned to the tuner input and I need to change the inputs to composite. 

I was looking at the command line for V4l2-ctl (formerly ivtvctl) but could not figure out how to do so.

Could someone please provide the command for changing inputs on the WinTV 500 card from tuner to composite?

Thanks

---

