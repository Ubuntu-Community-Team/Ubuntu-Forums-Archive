---
title: "Video playback issues vlc/Totem"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by BenyBen on 2007-04-01
I'm using Ubuntu 6.10 - the Edgy Eft, and I downloaded VLC.
It plays any mpeg-4 avi's, however as soon as I play a video in full screen, the video is jumpy, and quite ugly.

I don't have this problem (or at least no where near as bad as) with VLC under windows.

I also tried the gstreamer ffmpeg video plugin to play with totem, same issue.

Is there a playback codec that works best? and how does one tell a player to use the said codecs? I spent some time trying to install Divx and the likes, only to find out that that's a pluggin for encoding, not playback. 

I have an ATI X1600xl using the fglrx drivers, since the built-in drivers did not work at all. I don't know if that has something to do with it. 

Please bear in mind that I am quite the nooblar. :)

---

### Post by Kobalt on 2007-04-01
It's a graphic card drivers related problem, it's not about VLC or Totem... Other ATI cards owners have reported such problems, with various workarounds. You could try to install the latest drivers for you card using Envy script, this will do it all for you. 
[Here]("http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.1-0ubuntu4_all.deb") is the .deb package you need, and [here]("http://www.albertomilone.com/nvidia_scripts1.html") are the info.

---

