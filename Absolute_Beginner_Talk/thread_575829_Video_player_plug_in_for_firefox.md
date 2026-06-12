---
title: "Video player plug in for firefox?"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by cubetriangle on 2007-10-14
I'm running firefox in xubuntu. And I have Mplayer which appears to work for apple trailers and game trailers but certain websites don't work. What's the best plugin to use for firefox for video?

---

### Post by Pumalite on 2007-10-14
vlc?

---

### Post by skipbarker on 2007-10-14
I second VLC.

---

### Post by strabes on 2007-10-14
If you want something inside firefox, you need to remove the totem firefox plugin (cuz it sucks) and install the gstreamer one:```
sudo rm /usr/lib/firefox/plugins/libtotem* 
sudo apt-get install mplayer mozilla-mplayer -y
```Then restart firefox.

---

### Post by Frak on 2007-10-14
> **strabes said:**
> If you want something inside firefox, you need to remove the totem firefox plugin (cuz it sucks) and install the gstreamer one:```
sudo rm /usr/lib/firefox/plugins/libtotem* 
sudo apt-get install mplayer mozilla-mplayer -y
```Then restart firefox.
+1, this is one of the better choices, I prefer it over VLC.

---

