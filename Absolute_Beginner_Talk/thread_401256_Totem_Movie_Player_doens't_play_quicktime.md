---
title: "Totem Movie Player doens't play quicktime"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by jej2003 on 2007-04-04
For whatever reason when I attempt to play quicktime movies they don't work.  Right now I am getting an "Internal Data Flow Error" with no other details.  The movie is from apple.com, what can I do to make this work?

Additionally, totem downloaded gstreamer and installed it but this did not fix the issue, and firefox's plugin doesn't seem to play the file either (it just sits there saying transfering data from server).  Any ideas?

---

### Post by zvacet on 2007-04-04
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by JayTheHun on 2007-04-04
I've had great success with all formats so far using VLC media player.

---

### Post by bashologist on 2007-04-04
Maybe use mplayer? It should be able to play most movies. Here's an installation script I made:
```
if sudo apt-get install mplayer; then cd /tmp; wget http://www1.mplayerhq.hu/MPlayer/releases/codecs/all-20061022.tar.bz2 && tar -xvjf all-20061022.tar.bz2; sudo mkdir /usr/lib/win32; sudo mv all-20061022/* /usr/lib/win32/; fi
```Just copy and paste it into a terminal then try to play the movie using mplayer?

---

