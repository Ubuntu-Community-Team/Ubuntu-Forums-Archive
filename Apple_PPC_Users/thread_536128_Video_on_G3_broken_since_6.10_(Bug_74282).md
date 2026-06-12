---
title: "Video on G3 broken since 6.10 (Bug 74282)"
date: 2007-08-27
forum: Apple PPC Users
---

### Post by andi666 on 2007-08-27
Does anyone know if there is any effort to fix the long standing bug 74282?
Or any unofficial repository that hosts G3 packages?

[https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/74282](https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/74282)

This bug affects nearly every application that has video playback. Unfortunately it is not enough to rebuild ffmpeg (libavcodec & libavformat) since many appication have their own copy linked in.

I rebuilt nearly all them once on 6.10 and 7.04 - completely without altivec support on my Pismo 400Mhz, which took ages. But every time some update comes in I have build everything again.

The bug should really be fixed in ubuntu :-( But when I look at the discussions in launchpad I do not have much hope.

andi

---

### Post by stmiller on 2007-08-27
Ah crap what a bug. Most programs link to the gstreamer-x-ffmpeg so that package is most likely the culprit. If you compile ffmpeg to force altivec, it will crash on cpus without altivec. This is perhaps what the package maintainer did for the ppc gstreamer package.

You should try contacting the gstreamer team, or make a new bug report alerting them directly about a bug in the gstreamer-x-ffmpeg package. B/c this bug report has not been assigned to anyone so no one is ever going to see it... :(

---

### Post by andi666 on 2007-08-27
It is not only only the gstreamer package, it is basically everything that uses ffmpegs libraries in any way. The CPU runtime detection is broken.
Daniel Gimpelevich notes somes details and even proposed a patch for mplayer in a releated bug report. Nobody seems to listen.


[https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/78426](https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/78426)

[http://launchpadlibrarian.net/6880533/mplayer-feisty-fix.diff](http://launchpadlibrarian.net/6880533/mplayer-feisty-fix.diff)

andi

---

### Post by stmiller on 2007-08-28
You might want to file a bug with gstreamer, which will trigger it to be noticed by the gstreamer team. Those are the people who could fix this, or who would at least care.

---

### Post by andi666 on 2007-09-19
I just evaluated video playback on G3 in gutsy (7.10). I tested a wmv file containg windows media 9 video codec to be sure that libavcodec is used.
These are my results:

vlc: ok 
xine: ok
ffplay: ok

totem-gstreamer: still broken 
gnash (uses gstreamer-ffmpeg): still broken

A workaround for these two is to remove altivec support from both liboil and gstreamer-ffmpeg. Yay, youtube works. If you need the .deb files just drop me a line. 

Oh and last but not least:

mplayer: still broken (I didnt do a workaround for this yet).

---

