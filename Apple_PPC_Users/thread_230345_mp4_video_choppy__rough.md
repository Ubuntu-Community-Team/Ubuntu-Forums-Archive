---
title: "mp4 video choppy / rough"
date: 2006-08-05
forum: Apple PPC Users
---

### Post by stmiller on 2006-08-05
I'm trying to playback a dl.tv mp4 episode. The video is distored by vertical lines, and is mostly black. Audio is fine. I have gstreamer and faac faad associated plugins, etc all installed.

It plays back this bad in vlc, totem, mplayer, everything. 


```
root@mahler:~# uname -a
Linux mahler 2.6.15-23-powerpc #1 Tue May 23 13:46:54 UTC 2006 ppc GNU/Linux
root@mahler:~#

```

```
root@mahler:~# cat /proc/cpuinfo
processor       : 0
cpu             : 7447A, altivec supported
clock           : 533.333000MHz
revision        : 0.1 (pvr 8003 0101)
bogomips        : 36.73
timebase        : 18432000
machine         : PowerBook6,5
motherboard     : PowerBook6,5 MacRISC3 Power Macintosh
detected as     : 287 (iBook G4)
pmac flags      : 0000001b
L2 cache        : 512K unified
pmac-generation : NewWorld
root@mahler:~#

```

---

### Post by sleepkreep on 2006-08-06
How well does it work with Totem?  I've never been to fond of gstreamer personally.  Try it with xine and make sure you have the w32codecs installed.  Get them here: [http://seigo.cs.mtsu.edu/~carl/essential-20060611.tar.bz2](http://seigo.cs.mtsu.edu/~carl/essential-20060611.tar.bz2)

and untar them in the /usr/lib/win32 and then create a symlink from /usr/lib/codecs to /usr/lib/win32

Cheers!

---

### Post by rasec on 2006-08-06
The win32 codecs won't work on a powerpc. 

stmiller, you might want to try ffmpeg, but I kind of doubt that it will make any difference because mplayer already uses it.

---

