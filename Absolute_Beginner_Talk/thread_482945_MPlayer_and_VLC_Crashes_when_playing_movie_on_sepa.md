---
title: "MPlayer and VLC Crashes when playing movie on separate X-Screen"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by kasperbs on 2007-06-24
Hi,
I have a problem when I'm playing movies through tv-out on my pc. I have a nvidia GeForce ti 4200, and I'm using a separate X-Screen to play my tv-out on.

But when i play the movie it pauses regularly and starts again after a 10sek break. It happens every 10-15 minutes, and it getting pretty annoying.

I thought that it might be because I was using other programs while playing back the movie, but it also happens when I'm just watching the movie with no other programs running.

Does anyone know what could cause this, I have tried both MPlayer and VLC it happens on both players. heres is the output I get when Im running MPlayer with this command:
> DISPLAY=:0.1 mplayer -fs '/media/ext3_180gb/Kasper/Media/Movies/Flushed Away (2006)/Flushed Away (2006).avi'
The movie starts playing:
> MPlayer 2:1.0~rc1-0ubuntu9.1 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.66GHz (Family: 15, Model: 2, Stepping: 7)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /media/ext3_180gb/Kasper/Media/Movies/Flushed Away (2006)/Flushed Away (2006).avi.
AVI file format detected.
VIDEO:  [DX50]  608x320  12bpp  23.976 fps  954.6 kbps (116.5 kbyte/s)
Clip info:
 Software: VirtualDubMod 1.5.10.1 (build 2366/release)
SUB: Detected subtitle file format: subviewer
SUB: Read 823 subtitles.
SUB: Adjusted 330 subtitle(s).
SUB: Added subtitle file (1): /media/ext3_180gb/Kasper/Media/Movies/Flushed Away (2006)/Flushed Away (2006).srt
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 608 x 320 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.90:1 - prescaling to correct movie aspect.
VO: [xv] 608x320 => 608x320 Planar YV12  [fs]
No bind found for key 'MOUSE_BTN0'.                           0.4% 27 0 
A:1937.0 V:1937.0 A-V: -0.000 ct:  0.000 46443/46443  3%  0%  0.4% 27 0
This is really annoying so if anyone knows what could cause this I would be happy to hear your thoughts.

EDIT: I just got this output from the terminal, this is the first time I see it but I just wanted to include it since it might help you guys.
           > ************************************************
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

---

### Post by kasperbs on 2007-06-25
I have tried a different set of settings as suggested in the output from the terminal, some of them seem to help, but its far from good. Does anyone know which one might be the best?

---

### Post by hasplu on 2007-06-30
That really sucks man:) 
anyway, what's your PC configuration?
and how big is yours swap space?
I'm not sure about your case, but sometimes things are simple...

Have fun:)

---

### Post by kasperbs on 2007-07-02
> That really sucks man
anyway, what's your PC configuration?
I have got a nvidia GeForce4 ti 4200, 750mb RAM, and some 2.6 GHz intel Processor. But the problem isn't that big anymore I have found two settings which I switch between, If the first one is bad then the other one works in most cases.

---

