---
title: "Totem shows no dvd menu's"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by philinux on 2007-08-13
Managed to get Totem playing DVD's. 

Had to install regionset from synaptic, did not run it but it's presence allowed my dvd to playback! 

However there are no subtitles available or any of the dvd's menu's.

VLC plays it fine. 

Totem is the default for ubuntu and regionset is not installed as standard. I've installed all the approprite codecs.

For a novice this would cause them to backoff from ubuntu.

I only found out about regionset by luck.

---

### Post by nvrpunk on 2007-08-13
use totem xine

sudo apt-get install totem-xine libxine1 libxine1-ffmpeg libxine-extracodecs

---

### Post by philinux on 2007-08-13
ok before i do whats the difference between 

1. Totem (already installed)

2. Totem-gstreamer (already installed - gets uninstalled by installing totem-xine. what would this effect?

3. Totem-xine

:confused:

---

### Post by annda on 2007-08-13
from my experience, gstreamer has better sound than xine so if you ever use totem for files where sound quality is important, don't change anything but install kaffeine to play dvds with menus.

if you don't use totem for audio files, go ahead and substitute totem-gstreamer with totem-xine.

---

### Post by philinux on 2007-08-13
If it ain't broke dont fix it  :lolflag:

Might as well just stick with vlc sound is important

I've already got gxine, mplayer, realplayer and also xine.

---

