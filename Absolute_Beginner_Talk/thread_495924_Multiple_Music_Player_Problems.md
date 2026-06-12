---
title: "Multiple Music Player Problems"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by snwbord2456 on 2007-07-08
I just re-installed ubuntu, and every music player I try to use either doesnt start at all (Banshee, got the loading screen which just hung and was white due to firefox when I actually looked at it) or wont play such as Amarok or Rhythmbox. g, it&#347; 56 gigs, but should the size affect everything like this? Amarok will seemingly load everything but when I try to play a song it just hangs with the loading cursor. Rhythmbox hasnt even successfully loaded my entire library (which my be a little biAll my music is in at external fat32 drive which I have mounted using 

sudo mount /dev/sdb1 /media/seagate/ -t vfat -o iocharset=utf8,umask=000

because when I tried to mount it other ways I couldnt get the permission thing to work, even when giving myself 1000. What do I do to fix this?

Also when trying to use any kind of wav editor (Audacity, GNUsound, rosegarden) none of them can detect my output device. I can hear my music on startup and when I play wavs online.

---

### Post by duffrecords on 2007-08-14
> Also when trying to use any kind of wav editor (Audacity, GNUsound, rosegarden) none of them can detect my output device. I can hear my music on startup and when I play wavs online.
Use [JACK]("http://jackaudio.org/") to connect these programs to your output device or to each other.

---

