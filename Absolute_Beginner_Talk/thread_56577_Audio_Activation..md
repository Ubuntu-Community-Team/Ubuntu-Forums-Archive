---
title: "Audio Activation."
date: 2005-08-13
forum: Absolute Beginner Talk
---

### Post by MrPockets on 2005-08-13
Im 100% noob on Linux,  just installed Ubuntu last night.  Upon the installation i noticed the audio doesnt work.  when opening Volume controll i activated the Soundblaster Audegy2 as the device, nothings muted and all volumes are full.  Also the Volume Moniter reports sounds when they should be (when sending/receaving messeges in Gaim or listening to MP3s) but still no audio.  A gentleman in #ubuntu on irc.freenodes.net solved the problem with a reasonably short code involving the words "jack on" in it, however that is all of the code i can recall.  Unfortunatly due to a reformat im having the same problems tonight,  If someone could tell me that code or a different solution i'd be very greatfull.
thank you,

---

### Post by phen on 2005-08-13
MAYBE i know your problem:

open a terminal (right click on desktop), and open "alsamixer". Maybe there is a channel called something with jack. try to turn it on. try to play with these settings. i dont remember how to save these alsa setting. somehow with alsactl i think. try man alsactl.

hope it helps!

kai

---

### Post by MrPockets on 2005-08-13
yes that did the trick, thank you much.

---

