---
title: "Can't play dvd after changing hard drives."
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by bwallum on 2008-01-09
Hi

I can't get my dvd player to run dvds any more. It has run in the past, then I added two new SATA drives and reinstalled 7.10 AMD64. Everything goes like a train but I can't get dvd's to play properly.

When i put a dvd in the drive the media is mounted and I get an icon on the desktop correctly identifying the dvd disc.

However it just won't play. I have tried VLC, Mplayer and Movie Player but all to no effect. I have Ubuntu Restricted Extras loaded. I can watch BBC News streams ok.

The dvd drive is now the only IDE parallel drive. Previously I had a IDE parallel harddrive. Could this be a problem in identifying the drive?

I also tried running Mplayer from a terminal to see if any clues could be found. Output is below, note the "The selected video_out device is incompatible with this codec" line.

Can you help please?

Rgds
Bob 

bob@bob-desktop:~$ mplayer /dev/dvd
MPlayer 1.0rc2-4.1.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ (Family: 15, Model: 75, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /dev/dvd.
MPEG-PS file format detected.
MPEG: No audio stream found -> no sound.
VIDEO:  MPEG2  720x576  (aspect 2)  25.000 fps  2000.0 kbps (250.0 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 576 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
Audio: no sound
Starting playback...
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x576 => 768x576 Planar YV12 
V:   0.8  15/ 15 32% 20%  0.0% 0 0 
GNOME screensaver enabled

Exiting... (End of file)

---

### Post by dcstar on 2008-01-09
> **bwallum said:**
> Hi

I can't get my dvd player to run dvds any more. It has run in the past, then I added two new SATA drives and reinstalled 7.10 AMD64. Everything goes like a train but I can't get dvd's to play properly.

When i put a dvd in the drive the media is mounted and I get an icon on the desktop correctly identifying the dvd disc.

However it just won't play. I have tried VLC, Mplayer and Movie Player but all to no effect. I have Ubuntu Restricted Extras loaded. I can watch BBC News streams ok.

The dvd drive is now the only IDE parallel drive. Previously I had a IDE parallel harddrive. Could this be a problem in identifying the drive?
.........

Set the jumpers on the DVD drive to be a "Master" device, it may be set to "Slave" and that could cause an issue if you have removed the previous Master device.

---

### Post by bwallum on 2008-01-10
Hi

I've checked and it is set up as master. The players pick it up in the menu list but when run, stops immediately. I think I'm a codec short somewhere.

---

