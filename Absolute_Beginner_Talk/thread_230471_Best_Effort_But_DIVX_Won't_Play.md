---
title: "Best Effort But DIVX Won't Play"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by Dana on 2006-08-06
Running a fresh install of Dapper. I've made my best effort to play Divx 5 files. I've tried Gxine, Totem-Xine, Mplayer. Followed numerous guides to no end. The closest I've come is Gxine and Totem-Xine now play the Divx 5 audio but not the video. Mplayer doesn't do anything.

I've installed:
gstreamer0.10-ffmpeg
gstreamer0.10-pitfdll
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse
gstreamer0.10-plugins-good
gstreamer0.10-gnomevfs
gstreamer0.10-plugins-base
gstreamer0.10-plugins-base-apps
gstreamer0.10-tools
libgstreamer0.10-0
gxine
libxine-main1
libxine-extracodecs
w32codecs
libdvdread3
libdvdcss2

Don't know where to turn next. I've got quite a few hours in on this, complicated by repos problems that have now been resolved. I've read a lot of threads and docs without understanding where I've gone wrong.

Any suggestions?

Dana

---

### Post by orb9220 on 2006-08-06
All you have to do is use the search feature in synaptic

XVID encoder plugin for GStreamer
This GStreamer plugin enables encoding/decoding of MPEG4/DivX
compressed video streams

[http://www.xvid.org/](http://www.xvid.org/)

If that dosn't work try vlc has its own codecs I believe.

---

### Post by Jagot on 2006-08-06
You could try vlc - I believe it's in the universe repo - it pretty much plays anything.

---

### Post by Dana on 2006-08-06
The xvid encoder for Gstreamer is v. 0.8 and I've noticed it and w32codecs only mention divx 4, not 5. Thanks guys for the new leads.

Dana

---

### Post by Dana on 2006-08-06
Well, life sucks I guess, xvid did not work... vlc plays sound but no video.
I'll have to try to gain a fresh perspective on this tomorrow... oh, it's already tomorrow.

Dana

---

### Post by OU812 on 2006-08-07
When using mplayer, I always have to change the video driver using preferences. Maybe you need to try the same solution in vlc?

john

---

### Post by Dana on 2006-08-07
You certainly may be correct. I "have" tried to do that but I do not know what I am doing. Also have been trying to parse codecs.conf but again thwarted by lack of knowledge while trying to acquire same. I am taking a day off from this problem, for my sanity. One thing I am going to do is  remove the w32codecs and reinstall them.

Dana




> **OU812 said:**
> When using mplayer, I always have to change the video driver using preferences. Maybe you need to try the same solution in vlc?

john

---

### Post by Dana on 2006-08-09
Still no Divx video, only audio. Tonight I reinstalled the w32codecs. As far as I can tell I've installed everything necessary. Everything else I've tried works. I can play wmv, ra, mp3, DVDs.

Codecs is 20060611-1plf1 from freecontrib.org

Dependencies listed for this:
Depends: libc6 (>=2.3.4-1)
Depends libstdc++5 (>=1.3.3.4-1)
Suggests: mplayer
Suggests: gstreamer0.10-pitfdll
Conflicts:libaviplay
Replaces:libaviplay
Conflicts:divx-codecs
Replaces:divx-codecs
Conflicts:W32codecs-lite
Conflicts:qt6codecs

Soooo, can I safely get rid of W32codecs-lite and qt6codecs? Or is this another blind alley?

Thanks... Dana

---

### Post by Dana on 2006-08-09
Okay, that seems to be a blind alley, neither are installed and the dependencies listed are there.

Dana

---

