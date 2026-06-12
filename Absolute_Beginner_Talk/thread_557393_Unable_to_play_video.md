---
title: "Unable to play video?"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by fiskking on 2007-09-22
I recently tried to play a Quicktime video ( using Totem movie player ) where a unsuccessful search  for the required codec promptly displayed this message:

 Quicktime demuxer plugin which is not installed.

Are there any movie players for Feisty Fawn better than Totem, and can handle the different types of formats?

---

### Post by mysticmatrix on 2007-09-22
> **fiskking said:**
> I recently tried to play a Quicktime video ( using Totem movie player ) where a unsuccessful search  for the required codec promptly displayed this message:

 Quicktime demuxer plugin which is not installed.

Are there any movie players for Feisty Fawn better than Totem, and can handle the different types of formats?

Mplayer( with the w32codecs) can play virtually any file.(Atleast all that I encountered WMV9, RMVB, Quicktime)

Install Mplayer by add/remove.

For w32codecs, you might refer here. [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by n3tfury on 2007-09-22
vlc will handle quicktime and most everything else right "out of the box"

---

### Post by RomeReactor on 2007-09-22
Hi. If you're using **totem-gstreamer**, try installing these packages:
```
sudo apt-get install gstreamer0.10-fluendo-mpegdemux gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libquicktime0 mplayer
```
Totem should be able to play Quicktime files then. If you have **totem-xine** instead, make sure you have the extracodecs package installed:
```
sudo apt-get install libxine1 libxine1-ffmpeg libxine-extracodecs mplayer
```

I added Mplayer to the packages to install since totem sometimes has trouble with matroska videos, especially those with the h264 codec, and mplayer plays those just fine; otherwise, totem plays every format very well for me.

---

### Post by fiskking on 2007-09-22
thanks guys for the help!


:popcorn:

---

