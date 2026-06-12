---
title: "Video Acceleration"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by TehMark on 2007-01-31
Hey guys,

I was wondering what my options for video acceleration/codecs were.  Seems to me that my videos kind of look like crap when compared to my xp machine.  I'm using the nvidia pure dvd decoder on that one but I'm admittedly completely lost when it comes to linux.  Any recommendations would be greatly appreciated.  Thanks!!!

Specs
4800+ X2
Nvidia 7900GT
2.5gb ram

---

### Post by r4ik on 2007-01-31
Try,

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

for the drivers.

Good luck !

---

### Post by TehMark on 2007-01-31
Thats what I was thinking but I'm already running the "official" nvidia driver :(

my guess is that this xfmedia player doesn't have good codecs yet.

---

### Post by psyne on 2007-01-31
Have you considered trying vlc player I use it and it looks beautiful even compared to my Windows PC. 

It is really easy to use if you have the Universal repository selected you can install it through the Synaptic manager or you can use Automatix. Or you can visit page below for apt get method.

[http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

The bonus to using VLC is that it will play most of the formats popular on windows. Including divx, xvid so on.

---

### Post by TehMark on 2007-01-31
hmm I might try vlc.  use it from time to time on my xp machine

I've found a temp fix of sorts for the "ugly video" problem.  After searching these forums I decided I needed to get the w32 codecs and the dvdlibcss2 packages.  Installed those and am using Kaffeine to play the vids.  (tried mplayer but got strange error on prog launch)  I have the video codec set to opengl and it looks 1000% better than it did.

Opengl is kinda slow though when theres high speed motion.  I get the blocky effect as stuff tries to catch up.  Any other ideas?

---

### Post by psyne on 2007-02-01
You could try reducing the resolution for the monitor to one that preserves the aspect ratio 1280x768.

You could also try reducing the colors from Millions of colors to thousands which will reduce the overal video quality. If that works then you should consider updating your video drivers as they should easily be able to render at that level.

Also are you running Beryl? This could be causing the problem if you are I would reccomend switching your session to gnome then trying the video.

---

