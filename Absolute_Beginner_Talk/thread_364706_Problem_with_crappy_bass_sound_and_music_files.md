---
title: "Problem with crappy bass sound and music files"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by crazyfan_metal on 2007-02-18
Hello there. I've been using Ubuntu for a couple of weeks now and recently installed all the gstreamer and w32 codecs. And after several days my sound was really crappy - the higher sounds were just fine but the bass sounds awful. The interesting thing is that only music files seem to be affected - both mp3 and ogg, but with video files the sound is perfect. And in the beginning all was normal. I hope you can help me solve my problem :).

---

### Post by atihimself on 2007-02-20
what do you use to listen music... in the beginning I had same kind of problems... if I remember correctly then its gstreamers fault... uninstall it and use libs only... I might be wrong... sorry can't help more

---

### Post by energiya on 2007-02-20
I had the same bass problem. Don't know if it was gstreamer or something else. To resolve mine I entered alsamixer and lower to 70 the first VIA DXS (I have a VIA'97). You could adapt to your audio card, and see if it works.

---

### Post by crazyfan_metal on 2007-02-20
Thank you, energiya :) . It worked :) . It's strange how GNOME handles sound from different programs.
Btw I used Rhythmbox, XMMS and Audacious and the result was the same. I also tried to uninstall the gstreamer codecs but in vain. Well, thanks to energiya everything is fine now :).

---

### Post by energiya on 2007-02-20
> **crazyfan_metal said:**
> Thank you, energiya :) . It worked :) . It's strange how GNOME handles sound from different programs.
Btw I used Rhythmbox, XMMS and Audacious and the result was the same. I also tried to uninstall the gstreamer codecs but in vain. Well, thanks to energiya everything is fine now :).

You're wellcome!

Actually, I don't think it has anything to do with Gnome. I encountered the same problem in Ubuntu 5.10, 6.06, 6.10, Xubuntu 6.10 (uses XFCE) and now in Zenwalk Linux (uses XFCE). This problem is quite weird (and irritating).

---

### Post by hiding-in-a-tree on 2007-03-18
It's called "PCM" on my (nforce2) control. Lowering to 70% did indeed fix the distorted/bad/fuzzy bass sounds. I'd like to know why it was a problem though... ?

---

