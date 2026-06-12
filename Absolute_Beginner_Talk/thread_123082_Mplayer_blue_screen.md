---
title: "Mplayer blue screen??"
date: 2006-01-29
forum: Absolute Beginner Talk
---

### Post by djgenesis on 2006-01-29
I am trying to open an .avi file with mplayer but it just loads up, throws a blue screen (which i find really familiar:P ) and then just hungs.... I have tried changing the video output to different video drivers but none of them work, apart from glx1 anf glx2 that cause the problem i am facing.
Notice that i am using a dual head display...
Can anyone help ?

[edit]
Also note that Totem, is playing the file, but the video is jerky (slow)
[/edit]

---

### Post by Perfect Storm on 2006-01-29
What's the output if you're running the file with mplayer in the terminal?

Try with VLC.

---

### Post by djgenesis on 2006-01-29
This is the output... and the player dosn't even open.. It just hungs there

```

Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0 : No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing /home/genesis/Desktop/alli-pap.xvid.sample.avi.
Cache fill:  0.00% (0 bytes)    AVI file format detected.
VIDEO:  [XVID]  640x272  12bpp  25.000 fps  1287.7 kbps (157.2 kbyte/s)
Clip info:
 Software: Nandub v1.0rc2
==========================================================================
Trying to force audio codec driver family libmad...
Opening audio decoder: [liba52] AC3 decoding with liba52
AC3: 5.1 (3f+2r+lfe)  48000 Hz  448.0 kbit/s
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, 16 bit (0x10), ratio: 56000->192000 (448.0 kbit)
Selected audio codec: [a52] afm:liba52 (AC3-liba52)
==========================================================================
vo: X11 running at 1152x864 with depth 24 and 32 bpp (":0.0" => local display)
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm:ffmpeg (FFmpeg MPEG-4)
==========================================================================
Checking audio filter chain for 48000Hz/2ch/16bit -> 48000Hz/2ch/16bit...
AF_pre: af format: 2 bps, 2 ch, 48000 hz, little endian signed int
AF_pre: 48000Hz 2ch Signed 16-bit (Little-Endian)
alsa-init: got device=0, subdevice=0
alsa-init: 1 soundcard found, using: default


```


I haven't tried vlc, but mplayer plugin for firefox does exactly the same thing...

---

### Post by djgenesis on 2006-01-30
Might there be a problem with the sound?
> ==========================================================================
Checking audio filter chain for 48000Hz/2ch/16bit -> 48000Hz/2ch/16bit...
AF_pre: af format: 2 bps, 2 ch, 48000 hz, little endian signed int
AF_pre: 48000Hz 2ch Signed 16-bit (Little-Endian)
alsa-init: got device=0, subdevice=0
alsa-init: 1 soundcard found, using: default

I tried changing the Audio output but i get an error and mplayer doesn't even care to  start...

---

### Post by Narcelio Filho on 2008-02-29
You can try to change the video output driver with option "-vo" like:

```

mplayer -vo x11 video.avi
mplayer -vo xv video.avi
mplayer -vo gl video.avi
mplayer -vo sdl video.avi

```

...and so on. Use "-vo help" to see all video output drivers.

---

### Post by wolfen69 on 2008-02-29
it is my firm belief that totem conflicts with mplayer. i have noticed this with several installs. removing totem and everything totem related cleared this up for me. besides, vlc is a more than capable replacement. humor me and try it. no guarantees, but worth a try.

---

### Post by anewguy on 2008-02-29
Depending on your video, this can also be an overlay problem.  Such graphics chips as the Via unichrome series used as a built-in on some laptops do not have the driver support needed and hence some of these problems.  I had a Gateway MX3215 laptop with just such a graphics chip, had the same problem you are, and could never get it fixed.  Here's something to try to see if it is an overlay problem:

- start the video in 1 instance of the player

- open another instance of the player and start the video there

Does the video appear blue screen in the first instance but not in the second?  Probably on overlay problem.  Please remember to have both instances running at the same time.

Good luck!  :)

---

### Post by roy.kimbrell on 2008-07-02
Check out the posts to the bug related to "No video overlay on external monitor" ([https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/155157/comments/23](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/155157/comments/23)).  There's possibly a solution there.  The next comment at [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/155157/comments/24](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/155157/comments/24) worked for me.

---

