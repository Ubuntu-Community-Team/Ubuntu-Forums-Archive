---
title: "mplayer /xfmedia closes after one milliisecond of playback"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by hanzj on 2006-08-16
hanzj@ubuntu:$ mplayer wpegg.avi
> MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel Pentium III Katmai/Pentium III Xeon Tanner (Family: 6, Stepping: 3)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
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
Playing wpegg.avi.
AVI file format detected.
AVI_NI: No audio stream found -> no sound.
AVI: No audio stream found -> no sound.
VIDEO:  [MP42]  720x480  24bpp  29.970 fps  3520.9 kbps (429.8 kbyte/s)
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffmp42] vfm: ffmpeg (FFmpeg M$ MPEG-4 v2)
==========================================================================
Audio: no sound
Starting playback...
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 720x480 => 720x480 Planar YV12
X11 error: BadAlloc (insufficient resources for operation)


MPlayer interrupted by signal 6 in module: vo_check_events
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.


[COLOR="White"][SIZE="1"]http://paste.ubuntu-nl.org/20834[/SIZE][/COLOR]

Please help.

---

### Post by hanzj on 2006-08-16
I have just installed w32codecs
> wget -c [http://packages.freecontrib.org/ubuntu/plf/pool/dapper/i386/non-free/w32codecs/w32codecs_20060611-1plf1_i386.deb](http://packages.freecontrib.org/ubuntu/plf/pool/dapper/i386/non-free/w32codecs/w32codecs_20060611-1plf1_i386.deb)

sudo dpkg -i w32codecs_20060611-1plf1_i386.deb 


but I still can't view the avi files that I've downloaded.

> hanzj@ubuntu:~/$ mplayer wpegg.avi 
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team CPU: Intel Pentium III Katmai/Pentium III Xeon Tanner (Family: 6, Stepping: 3)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
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
Playing wpegg.avi.
AVI file format detected.
AVI_NI: No audio stream found -> no sound.
AVI: No audio stream found -> no sound.
VIDEO:  [MP42]  720x480  24bpp  29.970 fps  3520.9 kbps (429.8 kbyte/s)
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffmp42] vfm: ffmpeg (FFmpeg M$ MPEG-4 v2)
==========================================================================
Audio: no sound
Starting playback...
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 720x480 => 720x480 Planar YV12
X11 error: BadAlloc (insufficient resources for operation)


MPlayer interrupted by signal 6 in module: vo_check_events
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.

Can anyone help?

[COLOR="White"][SIZE="1"]http://paste.ubuntu-nl.org/20836[/SIZE][/COLOR]

---

### Post by mrazster on 2006-08-16
How did you install mplayer and all codecs..??

Have you tried installing it thru automatix ..?

---

### Post by hanzj on 2006-08-16
I installed them via "sudo aptitude install mplayer", etc. See above.

No, I haven't tried installing via automatix.

---

### Post by mrazster on 2006-08-16
> **hanzj said:**
> No, I haven't tried installing via automatix.

Well...I have installed it thru automatix everytime....and got it working that way everytime. 
Why not give it a go. But before you do that...unistall everything that has to do with mplayer and its codecs.

---

### Post by hanzj on 2006-08-16
okay. if i do install via automatix, how do we do so? 
and will it be easy to uninstall the packages that automatix has installed, plus automatix itself?

---

### Post by hanzj on 2006-08-16
does automatix exist in dapper?

---

### Post by hanzj on 2006-08-17
Well, the problem is fixed. 
Doesn't seem to be a problem with the codec. 

xv video output doesn't work well on my comp. so i changed it to x11 my "gmplayer" and then Settings/Video Tab

---

### Post by hanzj on 2006-08-17
But I can't find "x11" under xfmedia/Preferences/Video.

It's currently at "auto" What should I choose?

---

### Post by mrazster on 2006-08-17
> **hanzj said:**
> But I can't find "x11" under xfmedia/Preferences/Video.

It's currently at "auto" What should I choose?

Good to hear you got it fixed with gmplayer.

About xfmedia, I really don't know m8..tried it for a couple of minutes and didn't liked it at all....removed it as soon as I got mplayer installed.

Why do you need xfmedia when you got mplayer doing it all for you..?

---

