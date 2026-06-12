---
title: "soundcard"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by chris200x9 on 2008-02-02
Hi, I upgraded my kernel but now when I click the volume control to turn my volume on it says "No volume control GStreamer plugins and/or devices found"

---

### Post by jan quark on 2008-02-02
go to synaptic packet manager and check if gnome-applets and gstreamer is installed

---

### Post by chris200x9 on 2008-02-02
gnome applets is but what gstreamer am I looking for there are a bunch some are checked some arn't

---

### Post by xc3RnbFO8P on 2008-02-02
You have to recompile alsa drivers in /usr/src/alsa/alsa-driver-1.0.?
and if you have snd-hda-intel.ko in /lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel, delete it before you recompile the driver.

---

