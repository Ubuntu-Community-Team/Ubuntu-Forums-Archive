---
title: "Mplayer play ERROR"
date: 2006-01-30
forum: Absolute Beginner Talk
---

### Post by PENG on 2006-01-30
Whenever I play movie with mplayer, 
it report ERROR: Cannot find codec matching selected -vo and video format 0*30345652
How could I do?
Thank you.

---

### Post by saubz on 2006-02-01
try this

```

sudo apt-get install gstreamer0.8-plugins
sudo apt-get install gstreamer0.8-lame
sudo apt-get install gstreamer0.8-ffmpeg
sudo apt-get install lame
sudo apt-get install sox
sudo apt-get install ffmpeg
sudo apt-get install mjpegtools
sudo apt-get install vorbis-tools
sudo apt-get install w32codecs
gst-register-0.8

```

then try playing your movie

---

### Post by Stinger on 2006-02-01
My best guess would be that you are missing an unsuported codec.
Try installing [Automatix]("http://ubuntuforums.org/showthread.php?t=66563")

"Capabilities:
 1) Installs multimedia codecs"
and a lot of other nice things.
Please read the instructions carefully before installing and using Automatix.
;)

---

