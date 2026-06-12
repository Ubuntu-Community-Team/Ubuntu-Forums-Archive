---
title: "Amarok showing signal 11 error"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by poision_heart on 2007-11-08
Hi i ve installed amarok in ubuntu through synaptics.Its not playing mp3 files.I ve gstreamer pluggins installed.Amarok showing signal 11 error and saying no mp3 support installed.While other hand totem playing mp3 files.Same problem is banshee too.Can any one guide me how to play files?

---

### Post by amingv on 2007-11-08
Hi,

Under KDE Amarok usually would install the codecs automatically, since it seems its not the case in Gnome just get these packages:

> libxine-extracodecs

#I think this one is included in the above one, but try it just in case.

libxine1-ffmpeg

Also here's a (very important) quote from [this webpage.]("https://help.ubuntu.com/community/RestrictedFormats/MP3")

> -Amarok folks pay attention to this: if you use **libxine-extracodecs** together with **gstreamer0.10-plugins-ugly** installed, the sound of playing mp3 will become weird. Simply remove **gstreamer0.10-plugins-ugly**.


---

### Post by poision_heart on 2007-11-09
Hi thanks for info.I am going to install those pluggins.

---

### Post by inversekinetix on 2007-11-09
I just installed it a few minutes ago.  It gave an error and then popped a box offering to install necessary mp3 codecs.  This is in gnome

---

### Post by bluknight on 2007-11-09
> **inversekinetix said:**
> I just installed it a few minutes ago.  It gave an error and then popped a box offering to install necessary mp3 codecs.  This is in gnome

Had the same offer from amarok with my newly installed Gutsy. I clicked OK, wait until synaptic autofinished installing the packages it chose then re-launch amarok. That solves it.

However with my m4a (Ipod type AAC) files I had to install other packages such as faad, libfaad, faac, libfaac and libmp4

HTH:lolflag:

---

