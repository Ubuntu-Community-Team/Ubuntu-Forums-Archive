---
title: "mplayer_video_problem"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by jamil_1 on 2007-06-07
I have mplayer on my feisty fawn. However, whenever I try to play video file it gives the following error and plays only audio. What should I do /?


[B]Playing /home/jamil/get_video2.flv.
libavformat file format detected.
VIDEO:  [FLV1]  320x240  0bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
vo_cvidix: No vidix driver name provided, probing available ones (-v option for details)!
[VO_SUB_VIDIX] Couldn't find working VIDIX driver.
[/B]

---

### Post by taurus on 2007-06-07
Applications -> Sound and Video -> MPlayer -> Preferences -> video and pick **xv** as a driver.  Close it and start it up again.  Now, see if you can play your video.

---

### Post by Songwind on 2007-06-07
if you're using the command line, you can specify the video output there, too.

```

mplayer -vo xv /home/jamil/get_video2.flv

```

There is also an mplayer preferences file you can set up so you don't have to do that every time.  It's not too complicated.  The format is in the documentation and at their website.

Good luck! :)

---

### Post by jamil_1 on 2007-06-07
well  the 
```
mplayer -vo xv /home/jamil/get_video2.flv
```

produces the following response


[B]jamil@jamil-desktop:~$ mplayer -vo xv /home/jamil/get_video2.flv
MPlayer 1.0rc1-4.1.2 (C) 2000-2006 MPlayer Team
CPU: Intel Celeron 2/Pentium III Coppermine,Geyserville (Family: 6, Model: 8, Stepping: 10)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX MMX2 SSE

Playing /home/jamil/get_video2.flv.
libavformat file format detected.
VIDEO:  [FLV1]  320x240  0bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
Error opening/initializing the selected video_out (-vo) device.
[/B]

Exiting... (End of file)

---

### Post by jamil_1 on 2007-06-07
However if if I specify xv as as the output video driver through the GUI then it does play the video
but pc get stuck after some time or if when I try to minimize the video window.
(My pc has crashed three times while playing this file)

---

### Post by taurus on 2007-06-07
Have you tried playing the same video with vlc?  VLC should be in the repos so you can install it with synaptic, apt-get, or aptitude.

---

### Post by jamil_1 on 2007-06-07
vlc  will take very long time to download as I have a 31-41 kbps internet connection.
let alone the flv file I am also getting trouble playing avi file format. Video is quite absurd as if chopped.

---

### Post by taurus on 2007-06-07
Could it have to do with your graphic card?  What graphic card do you have and have you installed a driver for it?

```
lspci
```

---

### Post by jamil_1 on 2007-06-07
lspci returns the following text about graphics card


[B]01:0a.0 VGA compatible controller: Trident Microsystems TGUI 9660/938x/968x (rev d3) (prog-if 00 [VGA])
        Flags: medium devsel, IRQ 11
        Memory at ff400000 (32-bit, non-prefetchable) [size=4M]
        Memory at ff8f0000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at f6900000 [disabled] [size=64K][/B]

---

### Post by jamil_1 on 2007-06-07
As far as I remember mplayer does support my graphics card   (I read this in mplayer's documentation)

---

