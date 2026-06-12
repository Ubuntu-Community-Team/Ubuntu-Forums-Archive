---
title: "[SOLVED] How do you change the ogg lossy bitrate?"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by dimbulb1024 on 2008-03-09
Right now when I rip a CD to ogg lossy it is in 160kbps. I would like to change this to 192-256kbps. I have looked here and google to no avail.
When I look in preferences of Rhythmbox or Sound Juicer and click to edit the ogg lossy profile, I don't see a way to change the bitrate. The only thing that jumps out at me is Gstreamer Pipeline code:
```
audio/x-raw-float,rate=44100,channels=2 ! vorbisenc name=enc quality=0.5 ! oggmux
```
and there is a rate and quality, but I'm not sure what would happen if I messed with that, so I'm not touching it. 
Well Ubuntu Masters, what say you?

:guitar:

---

### Post by eldepeche on 2008-03-09
I don't know how gstreamer translates that quality number into a vorbis quality value, but I do know that the maximum value is 1 and that bigger numbers give better quality.

I would say just experiment with different values between quality=0 and quality=1.

Also, vorbis bitrates are lower than MP3 bitrates for the same quality file, FYI.

---

### Post by dimbulb1024 on 2008-03-09
Thanks eldepeche.

FYI These are  the approximate bitrates associated with the number:

q .1 = 80 kbps
q .2 = 96 kbps
q .3 = 112 kbps
q .4 = 128 kbps
q .5 = 160 kbps
q .6 = 192 kbps
q .7 = 224 kbps
q .8 = 256 kbps
q .9 = 320 kbps
q 1.0 = 499 kbps

that I found via this post  - 
[http://ubuntuforums.org/showthread.php?t=500341]("http://ubuntuforums.org/showthread.php?t=500341")
 - and some of my own toying with the numbers.

Now I feel confident to go in and change the GStreamer Pipeline code.

:guitar:

---

