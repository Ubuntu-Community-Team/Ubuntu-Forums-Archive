---
title: "vlc, mplayer and totem all have a/v sync issues"
date: 2008-11-03
forum: Arch and derivatives
---

### Post by bp1509 on 2008-11-03
Curious, i just recently came over to archlinux and i'm quite pleased, just one little speed bump to getting completely setup.  I'm using alsa and openbox, and it doesn't seem which application I use, certain videos that i know worked flawlessly in other distributions seem to lag in audio.  It's not all my files.  Most of my avi's seem to be fine, it's more mpegs and wmvs than anything else.   But I can't seem to figure out why vlc and totem would have the exact same problem as they use different codecs all together (or am i wrong about this?)

Never had this problem on ubuntu, suse, fedora, gentoo, or windows for that matter.  Any ideas ?

---

### Post by Toffeeapple on 2008-11-03
I had the same problem, arch64 on duel monitors, it only started a few updates of vlc ago, can't remember exactly.

Having said that I've just finished installing archi686 on the same system and the problem is no longer there, don't know exactly why, maybe there is something wrong somewhere in Arch64.

Have you though tried manually setting the refresh rates in nvidia-settings and Sync to VBlank?

---

### Post by bp1509 on 2008-11-03
I do have it set to VBlank, and I am using i686 version of arch.

---

### Post by handy on 2008-11-03
I'm running 64bit Arch & my video is playing great these days.

It was useless for DVD's prior to the last 2 or 3 ATi GPU driver updates though.

---

### Post by fwojciec on 2008-11-03
Tearing issues are most likely caused by the graphics driver.  Are you using a nvidia card?  This thread on nvidia forums, for example, discusses a similar issue with the latest nvidia driver: [http://www.nvnews.net/vbulletin/showthread.php?t=121931]("http://www.nvnews.net/vbulletin/showthread.php?t=121931")

---

