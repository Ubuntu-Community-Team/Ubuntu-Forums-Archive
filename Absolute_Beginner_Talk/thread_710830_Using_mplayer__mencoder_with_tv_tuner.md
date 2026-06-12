---
title: "Using mplayer / mencoder with tv tuner"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by e_james on 2008-02-28
I would like to try to use mplayer and / or mencoder with my hauppauge WinTV PCI FM tuner card. I have studying threads, man pages and anything else I can find for several days and this seems to be the extreme example of a Windows user's problem with Linux - Too Much Information Too Little Explanation. Most recently I lifted the command below out of the man page and it actually seemed to do something instead of just quitting with lots of error messages.

```
edward@ubuntu-em2:~$ mplayer tv:// &#8722;tv driver=v4l:width=640:height=480:outfmt=i420 &#8722;vc rawi420 &#8722;vo xv
MPlayer 2:1.0~rc1-0ubuntu13 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.80GHz (Family: 15, Model: 2, Stepping: 9)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing tv://.
TV file format detected.
Selected driver: dummy
 name: NULL-TV
 author: alex
Selected input hasn't got a tuner!
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
VDec: vo config request - 320 x 200 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 320x200 => 320x200 Planar YV12 
Selected video codec: [rawyv12] vfm: raw (RAW YV12)
==========================================================================
Audio: no sound
Starting playback...
gnome_screensaver_control()% ??,?% 0 0 
Exiting... (Quit)

```

Is there anyone out there who can advise me how to edit the command so that it really works?

---

