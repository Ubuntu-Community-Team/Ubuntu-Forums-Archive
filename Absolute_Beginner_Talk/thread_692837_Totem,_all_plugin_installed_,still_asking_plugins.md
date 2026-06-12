---
title: "Totem, all plugin installed ,still asking plugins"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by sunseeker888 on 2008-02-10
HI I am a newbie

I have installed all the plug-ins for totem, and it is still asking for plug-ins when I try to play a DVD.




# gst-plugins-base
the basic and essential plug-ins for GStreamer
# gst-plugins-good
the plug-ins for most Open formats
# gst-plugins-ugly
good-quality plug-ins that might pose distribution problems, needed for DVD playback
# gst-plugins-bad
a set of plug-ins that need more work
# gst-ffmpeg
FFmpeg-based plug-in, contains all the basic decoders for popular codecs, such as DivX and WMV
# Pitfdll


Also, I have done this, and added libdvdread3 from synaptic package manager 
sudo /usr/share/doc/libdvdread3/install-css.sh


I have added all plug-ins from synaptic package managee

Please help [:confused:

---

### Post by jan quark on 2008-02-10
to watch encrypted dvds I had to do the following
```

sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot
```

and then

```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

now you can run gxine from applications > sound and video

it should work

---

### Post by sunseeker888 on 2008-02-10
> **jan quark said:**
> to watch encrypted dvds I had to do the following
```

sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot
```

and then

```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

now you can run gxine from applications > sound and video

it should work





Thanks a lot it worked, | was doing my nuts in. Do you know if I can play DIvX by any chance or need some other package?
 I am a newbie

Kind regards


:lolflag:

---

### Post by sunseeker888 on 2008-02-10
A little problem the display is ok, but the movie is running at slower frame,  any idea?

---

