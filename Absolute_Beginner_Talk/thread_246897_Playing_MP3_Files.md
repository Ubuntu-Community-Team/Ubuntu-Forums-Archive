---
title: "Playing MP3 Files"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by Zully Quirke on 2006-08-29
I have both amaroK and Rhythmbox, but neither seem to recognize/play my mp3 files. VLC does, but only one at a time. I want something with a playlist. Why are these two programs not recognizing mp3s?

---

### Post by reacocard on 2006-08-29
install the following packages:
```
gstreamer0.10-plugins-good
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse
```
now you're ready to play anything :-D

---

### Post by Qrk on 2006-08-29
Vlc has a playlist

---

### Post by deanlinkous on 2006-08-29
there is also the fluendo mp3 gstreamer plugin....

---

### Post by Zully Quirke on 2006-08-30
I can't seem to find any of those gstreamer files in my synaptic package manager. Is something else required first? I dont even see anything that says 0.10.. it's all 0.8.

---

### Post by eternalis on 2006-08-30
You dont use the synaptic manager, but you use the Command Line.

Check here:
[http://www.ubuntuforums.org/forumdisplay.php?f=159](http://www.ubuntuforums.org/forumdisplay.php?f=159)

---

### Post by Jagot on 2006-08-30
You need to enable the universe and multiverse repositories.  See this link:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

