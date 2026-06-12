---
title: "Video Streaming - Playback terrible?"
date: 2005-12-16
forum: Absolute Beginner Talk
---

### Post by Rackerz on 2005-12-16
In Windows the playback is brilliant for the particular file i want to stream, but Mplayer's playback is terrible, the picture is terrible also, when it shouldn't be. How can i improve it? Is there a better choice of player?

Thanks

---

### Post by shof2k on 2005-12-16
Microsoft Codecs are flaky in linux, not surprising as microsoft don't want to share thier details.  Things to try are:
1) Using Totem or gxine instead (both available through synaptic)
2) Installing the w32codecs from the penguin liberation front. Search for them on Google as I can't give any more information without getting my lawyer upset.
3) Follow [http://www.ubuntuforums.org/showthread.php?t=78037](http://www.ubuntuforums.org/showthread.php?t=78037) to get a recompiled mplayer.

Hope that helps,

---

### Post by Rackerz on 2005-12-16
[http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf) Im guessing that's the correct info on PLF. Thanks for your help!

EDIT: Konqueror and Firefox don't seem to want to use either totem or gxine :( What's going on there?

---

### Post by Rackerz on 2005-12-16
Anybody?

---

### Post by Dr. Nick on 2005-12-16
If you still have mplayer plugin installed it will override the new ones. Have you changed the video output in mplayer? Right click to prefrences and change the video output option. You may not be using the best one for your setup

Mplayer has always worked the best for me, and after using the w32codecs I dont really notice any difference in quality.

---

### Post by Jingo on 2006-04-23
Having poor quality playback here.

This media as demonstration:
mms://wms.dr.dk/storage/forbrug/Livsstil/dolph/dw5.wmv

Windows bitrate: ~500kbit/s
Ubuntu: ~45kbit/s

Using mplayer/totem-xine !

---

