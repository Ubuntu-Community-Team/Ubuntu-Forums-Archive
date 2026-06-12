---
title: "Totem Problems"
date: 2006-01-22
forum: Absolute Beginner Talk
---

### Post by Heretic Monkey on 2006-01-22
Everytime i try to play a video file using Totem, i always get:

> The video output is in use by another application. Please close other video applications, or select another video output in the Multimedia Systems Selector.

I've tried using VLC as well, and i only get audio.  I'm assuming this is due to the lack of codecs i've installed, but i'll get to that later.  The problem i have is that Totem is not in use (at least not to my knowledge) on any other application.  I've checked the system status, and it's not running.

How do i solve this problem?

---

### Post by wolfmaniac on 2006-01-23
For Totem Install Totem-xine

It Will Play Any Of The Popular Formats


And Vlc Can Play These Witout Installin Ne Of Other Codecs

Try Installin Win32codecs

---

### Post by Heretic Monkey on 2006-01-23
Great, thanx.  Easy fix.  However, i switched to Totem-xine, but there's no sound on any of the videos i've tried.

Also, what sort of codecs do i need to play wmv and windows media files?

Thanx for being patient

---

### Post by Perfect Storm on 2006-01-23
This require universe and multiverse and PLF to work:

```
sudo apt-get install gstreamer0.8-plugins gstreamer0.8-lame gstreamer0.8-ffmpeg w32codecs lame sox ffmpeg mjpegtools vorbis-tools gstreamer0.8-plugins-multiverse avifile-divx-plugin avifile-mad-plugin avifile-mjpeg-plugin libdvdcss2
gst-register-0.8

```

---

