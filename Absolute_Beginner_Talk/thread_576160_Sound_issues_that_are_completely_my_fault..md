---
title: "Sound issues that are completely my fault."
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by Otokoneko on 2007-10-14
Hi;
I installed Ubuntu Feisty Fawn on my DV9000z about a month back and have been LOVING it. It makes an exceptional media operating system, and the free software everywhere only sweetens the deal.

However, I've been having problems lately. I did some tough installations such as Beryl already, but ePSXe just baffled me. I followed another guide on the forum for installing it and it worked with ISOs, but I never got any sound. I noticed it had an OSS sound plugin, and, not knowing what I was doing, downloaded what OSS got me on google.
Now I get no sound in FF and a few other programs, and attempting to change my volume gets me "No volume control GStreamer devices and/or plugins found".

Any help will be appreciated.

Thanks
~Will

---

### Post by haldean on 2007-10-15
Try going to System > Preferences > Sound, change the device under "Music and Movies" to something else (ALSA, probably), and click test... if there's no sound, try the other options in the menu.

If that doesn't work, I would recommend reinstalling ALSA, which you can do through Synaptic.

---

