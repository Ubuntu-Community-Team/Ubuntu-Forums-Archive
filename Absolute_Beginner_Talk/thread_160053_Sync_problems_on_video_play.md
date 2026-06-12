---
title: "Sync problems on video play"
date: 2006-04-14
forum: Absolute Beginner Talk
---

### Post by zugu on 2006-04-14
Whenever I try to see a movie (usually .avi files) in VLC and Totem I experience choppy playback. The audio works well, but the video lags. VLC kid of makes my life easier though, by trying to synchronize audio with the video, by jumping frames though, while Totem plays the file with very small jumps, but enough to drive me crazy.

What can I do?

---

### Post by Perfect Storm on 2006-04-14
Make sure you have the right libs installed, but Totem is far from perfect. The best thing is to use Mplayer or VLC in my opinion.

Make sure that universe and multiverse is enable in your universe.

You can use this: [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic) also make sure you have PLF added.

and replace it with
```
sudo gedit /etc/apt/sources.list
```

Then
```
sudo apt-get update
sudo apt-get install w32codecs libdvdcss2 libdvdread3 gstreamer0.8-plugins gstreamer0.8-lame gstreamer0.8-ffmpeg lame sox ffmpeg mjpegtools vorbis-tools gstreamer0.8-plugins-multiverse avifile-divx-plugin avifile-mad-plugin avifile-mjpeg-plugin libdvdnav4 libdvdplay0
gst-register-0.8

```

---

### Post by zugu on 2006-04-14
Thank you for the reply, but isn't VLC natively supporting the media it supports on its Windows port (such as DivX etc.)?

---

### Post by Perfect Storm on 2006-04-14
You might go into VLC's Preferences and pick another audio driver also try messing VLC's video settings they might be incorrect for your computer. (just remember to enable advanced option in the lower right corner).

---

