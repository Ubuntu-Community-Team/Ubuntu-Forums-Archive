---
title: "[SOLVED] Last Annoyance: MOV files"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by Paulmd on 2007-07-22
OK, First I want to thank everybody who has helped me so far.

Realplayer is now  working fine. I've resigned myself that the sis630 3d acceleration is a classic "linux doesn't do that" issue. 

There is only one more thing I want to make my system do everything it has done under Windows: 

Quicktime/Mov files.

I know VLC says it does movs, and it probably does OK for the older versions, but I've been having trouble with a certain set of videos.

[http://marsrovers.jpl.nasa.gov/gallery/press/opportunity/20070720a.html](http://marsrovers.jpl.nasa.gov/gallery/press/opportunity/20070720a.html)

(actually, pretty much anything MOV from nasa). No problems with the MP4s, or the other media. 



The VLC browser plugin does nothing. Or more precisely I get a video player control, but no video.

When the videos are downloaded manually, and attempted to play, VLC tries, but crashes before doing anything.  Totem wants a plugin that doesn't exist. So does Realplayer, and MPlayer. 

Anyone has these working?

---

### Post by pyros on 2007-07-22
> **Paulmd said:**
> OK, First I want to thank everybody who has helped me so far.

Realplayer is now  working fine. I've resigned myself that the sis630 3d acceleration is a classic "linux doesn't do that" issue. 

There is only one more thing I want to make my system do everything it has done under Windows: 

Quicktime/Mov files.

I know VLC says it does movs, and it probably does OK for the older versions, but I've been having trouble with a certain set of videos.

[http://marsrovers.jpl.nasa.gov/gallery/press/opportunity/20070720a.html](http://marsrovers.jpl.nasa.gov/gallery/press/opportunity/20070720a.html)

(actually, pretty much anything MOV from nasa). No problems with the MP4s, or the other media. 



The VLC browser plugin does nothing. Or more precisely I get a video player control, but no video.

When the videos are downloaded manually, and attempted to play, VLC tries, but crashes before doing anything.  Totem wants a plugin that doesn't exist. So does Realplayer, and MPlayer. 

Anyone has these working?

I managed to get mov files playing in totem by adding the gstreamer ugly plugins from the medibuntu repositories. for a howto on adding the repositories, see:
[http://www.medibuntu.org/repository.php](http://www.medibuntu.org/repository.php)

EDIT: just tested it with the link to nasa videos you supplied and they play with the totem browser plugin just fine.

---

### Post by wak_maximus on 2007-07-22
i just like has a similar problem..
but i cannot play avi file on totem?
how to fixed this??

---

### Post by pyros on 2007-07-22
> **wak_maximus said:**
> i just like has a similar problem..
but i cannot play avi file on totem?
how to fixed this??

Please see:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
and here:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Basically you want the codecs to allow you to play differnt (non-open source or open standard) formats. there are many posts on this forum relating to just this subject, including a stickied one you can find at the top of this subforum entitled "Enabling Multimedia in Feisty (HOW-TO)"

---

### Post by wak_maximus on 2007-07-22
if the player said need DivX MPEG-4 version 5 decoder plugin not installed??

---

### Post by Paulmd on 2007-07-22
> **pyros said:**
> I managed to get mov files playing in totem by adding the gstreamer ugly plugins from the medibuntu repositories. for a howto on adding the repositories, see:
[http://www.medibuntu.org/repository.php](http://www.medibuntu.org/repository.php)

EDIT: just tested it with the link to nasa videos you supplied and they play with the totem browser plugin just fine.

Already have the ugly set. (and ugly-multiverse) 

More details:

Totem returns: "gstreamer encountered a general stream error" Ever so helpful ;)

VLC now doesn't crash: instead the "cursor" goes across the screen and doesn't play the video.

Xine does crash.

MPlayer: "Fatal Error!"  "Error opening/initializing the selected video_out (-vo) device"

I have already been to mediabuntu previously.

libquicktime0 IS installed.

What next?

What else?


Hmmmm.  These videos are 3d animations, is it possible that 3d acceleration is required to play them? (which I don't have)

---

### Post by pyros on 2007-07-22
> **Paulmd said:**
> Already have the ugly set. (and ugly-multiverse) 

More details:

Totem returns: "gstreamer encountered a general stream error" Ever so helpful ;)

VLC now doesn't crash: instead the "cursor" goes across the screen and doesn't play the video.

Xine does crash.

MPlayer: "Fatal Error!"  "Error opening/initializing the selected video_out (-vo) device"

I have already been to mediabuntu previously.

libquicktime0 IS installed.

What next?

What else?

OK, are you trying to play it in the browser, or in totem? vlc, xine, and mplayer do not use gstreamer. if you have installed totem-xine, then it doesn't use gstreamer either. I just have the totem-mozilla plugin installed and the totem-gstreamer packaged instead of totem-xine.

---

### Post by Paulmd on 2007-07-22
> **pyros said:**
> OK, are you trying to play it in the browser, or in totem? vlc, xine, and mplayer do not use gstreamer. if you have installed totem-xine, then it doesn't use gstreamer either. I just have the totem-mozilla plugin installed and the totem-gstreamer packaged instead of totem-xine.


Actually, I've tried both in the browser, and in all the standalone apps.  No dice.

Frankly, I'd be happy if one of these worked.

---

### Post by pyros on 2007-07-22
if you enter the following into a terminal:
```

mplayer http://marsrovers.jpl.nasa.gov/gallery/press/opportunity/20070720a/620_718_cimmeria_small.mov

```
what do you get?

---

### Post by bluenova on 2007-07-22
The Nasa links work fine for me with the mplayer mozilla plugin.

```
sudo aptitude install mozilla-mplayer
```

---

### Post by Paulmd on 2007-07-22
> **pyros said:**
> if you enter the following into a terminal:
```

mplayer http://marsrovers.jpl.nasa.gov/gallery/press/opportunity/20070720a/620_718_cimmeria_small.mov

```
what do you get?


A couple pages:


MPlayer 2:1.0~rc1-0ubuntu9.1 (C) 2000-2006 MPlayer Team
CPU: Intel Celeron 2/Pentium III Coppermine,Geyserville (Family: 6, Model: 8, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing [http://marsrovers.jpl.nasa.gov/gallery/press/opportunity/20070720a/620_718_cimmeria_small.mov](http://marsrovers.jpl.nasa.gov/gallery/press/opportunity/20070720a/620_718_cimmeria_small.mov).
Resolving marsrovers.jpl.nasa.gov for AF_INET6...
Couldn't resolve name for AF_INET6: marsrovers.jpl.nasa.gov
Resolving marsrovers.jpl.nasa.gov for AF_INET...
Connecting to server marsrovers.jpl.nasa.gov[64.62.193.129]: 80...
Cache size set to 320 KBytes
Cache fill:  0.00% (0 bytes)   
ISO: File Type Major Brand: Original QuickTime
Quicktime/MOV file format detected.
VIDEO:  [avc1]  640x480  24bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
Audio: no sound
Starting playback...
VDec: vo config request - 640 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 640x480 => 640x480 Planar YV12 
X11 error: BadAlloc (insufficient resources for operation)


MPlayer interrupted by signal 6 in module: vo_check_events
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.

---

### Post by Paulmd on 2007-07-22
> **bluenova said:**
> The Nasa links work fine for me with the mplayer mozilla plugin.

```
sudo aptitude install mozilla-mplayer
```

No dice. The install worked fine, but still no movie.

---

### Post by Paulmd on 2007-08-21
> **Paulmd said:**
> OK, First I want to thank everybody who has helped me so far.

Realplayer is now  working fine. I've resigned myself that the sis630 3d acceleration is a classic "linux doesn't do that" issue. 

There is only one more thing I want to make my system do everything it has done under Windows: 

Quicktime/Mov files.

I know VLC says it does movs, and it probably does OK for the older versions, but I've been having trouble with a certain set of videos.

[http://marsrovers.jpl.nasa.gov/gallery/press/opportunity/20070720a.html](http://marsrovers.jpl.nasa.gov/gallery/press/opportunity/20070720a.html)

(actually, pretty much anything MOV from nasa). No problems with the MP4s, or the other media. 



The VLC browser plugin does nothing. Or more precisely I get a video player control, but no video.

When the videos are downloaded manually, and attempted to play, VLC tries, but crashes before doing anything.  Totem wants a plugin that doesn't exist. So does Realplayer, and MPlayer. 

Anyone has these working?

I got them at last.  The solutions turns out to be to REMOVE the totem and MPlayer browser plugins, and use the VLC browser plugin. You can't use them both at once.

---

### Post by sdowney717 on 2007-08-27
mplayer provides more video codecs than these others.
I watched all the nasa videos in mplayer plugin on firefox.
The mp4 though wanted to save and open with totem.

---

### Post by Paulmd on 2007-08-28
> **sdowney717 said:**
> mplayer provides more video codecs than these others.
I watched all the nasa videos in mplayer plugin on firefox.
The mp4 though wanted to save and open with totem.

Thanks for replying, but I solved the issue last week. All good now. For whatever reason, mplayer AND totem refused to work. But after *removing* their Mozilla plugins, and installing the VLC mozilla plugin, all is good now. It's Odd that this worked, since VLC actually incorporates MPlayer's codecs for MOVs. )


(Incidentally, Both the Mars rovers survived the dust storm, and are resuming normal operations. But now the dust is settling out of the atmosphere, and settling on the solar panels, so the improved atmospheric conditions aren't helping with the power situation as much as they might.)

---

