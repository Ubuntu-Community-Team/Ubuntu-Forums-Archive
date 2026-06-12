---
title: "AVI Files Won't Play..."
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by nzk on 2007-04-04
I tried playing AVI files after I reformatted, and it wouldn't work. I tried VLC, Mplayer, and Totem, I tried installing every codec I could, and it still wouldn't work. What can I do?

---

### Post by irwa82 on 2007-04-04
Hi,

Have you tried installing the win32 codecs for mplayer. There are a lot of codecs in there for popular formats.

Also some avi files are divx but I believe that mplayer has divx in there by default not 100% sure.

---

### Post by nzk on 2007-04-04
Whats the package name for the win32 codecs?

---

### Post by irwa82 on 2007-04-04
Hi,

I don't think there is a ubuntu package for due to patent issues and all that. Download the linux binary codecs for the site below.

[http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html)

I can't remember the path where you put the codecs but in the readme last time I did it ubuntu puts the codecs in the old location so if in the readme or install fille it mentions and old path put it there.

If you can't find the correct place to put them then I will have to go to my ubuntu machine which is at home.

---

### Post by Maestro23 on 2007-04-04
> **nzk said:**
> Whats the package name for the win32 codecs?

w32codecs

---

### Post by pistcivet on 2007-04-04
.deb can be found here:
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs)
:)

---

### Post by nzk on 2007-04-04
I don't have any of the folders described in the readme!

---

### Post by nzk on 2007-04-04
Alright. The sound works but not the video.

---

### Post by Maestro23 on 2007-04-04
> **nzk said:**
> Alright. The sound works but not the video.

Are you getting any type of error?  What video player?

---

### Post by nzk on 2007-04-04
I dont believe I'm getting any errors, I'm using Totem.

---

### Post by irwa82 on 2007-04-05
Hi,

Try loading the avi with mplayer from the command line (terminal) and see what happens.

to do this bring up a terminal and type 'gmplayer' then try playing the file and see if any errors appear in the terminal window.

You could also try doing this with totem.

It is also possible that you don't have the codecs in the right spot for the video players to detect and use them.

---

### Post by nzk on 2007-04-05
When I ran gmplayer, I got this output:
```
MPlayer 2:1.0~rc1-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 3.40GHz (Family: 15, Model: 3, Stepping: 4)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/USER/Desktop/test.avi.
AVI file format detected.
VIDEO:  [DX50]  596x246  12bpp  23.976 fps  778.2 kbps (95.0 kbyte/s)
Clip info:
 Software: VirtualDubMod 1.5.10.1 (build 2366/release)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
Error opening/initializing the selected video_out (-vo) device.


Exiting... (Quit)

```

VLC works perfectly except there is **no video...**

Also, what is the 'right spot' for the codecs so that I can check if they are there? I installed the win32 ones using the .deb

---

### Post by irwa82 on 2007-04-05
hi,

On my Ubuntu 6.10 machine the location for mplayer is /usr/lib/win32/

---

