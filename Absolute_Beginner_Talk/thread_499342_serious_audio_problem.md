---
title: "serious audio problem?"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by benner on 2007-07-12
i have a fresh install of ubuntu feisty on an asus a8js notebook.  when i log in i get the little audio drumroll and i can hear that.  i use skype and can hear that.  but i can't hear any sound on any vidoes or any audio cd's.  i installed every codec that i could get from the repositories (i think) but it didn't make any difference.  i tried dvd's, audio cd's and videos of various types, including flash videos from youtube.  nothing.  tried the movie player that came with it (mplayer?) and vlc.  the card/driver is soundMAX integrated digital HD audio.

---

### Post by Gen2ly on 2007-07-12
try using alsaconf to configure the sound card once more.  I would guess that a couple of the settings need to be fixed because apperantly alsa is working just not set up correctly.

---

### Post by Inxsible on 2007-07-12
> **benner said:**
> i have a fresh install of ubuntu feisty on an asus a8js notebook.  when i log in i get the little audio drumroll and i can hear that.  i use skype and can hear that.  but i can't hear any sound on any vidoes or any audio cd's.  i installed every codec that i could get from the repositories (i think) but it didn't make any difference.  i tried dvd's, audio cd's and videos of various types, including flash videos from youtube.  nothing.  tried the movie player that came with it (mplayer?) and vlc.  the card/driver is soundMAX integrated digital HD audio.

So are you saying its only with audio and video files? not system sounds?
Applications -->Add/Remove Search for GStreamer and install all of them. Then try again.

---

### Post by Al3xK3aton on 2007-07-12
Make sure your skype settings aren't leeching sound support from other programs.

---

### Post by benner on 2007-07-12
i had already installed the gstreamer codecs.  no go.  and even without skype running there is no sound.  as in, i reboot and don't run skype.  still no sound.  i will try the alsaconf and report back.  thanks.

---

