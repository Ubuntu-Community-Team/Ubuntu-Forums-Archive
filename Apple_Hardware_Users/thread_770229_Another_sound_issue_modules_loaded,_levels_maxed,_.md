---
title: "Another sound issue: modules loaded, levels maxed, everything silent"
date: 2008-04-27
forum: Apple Hardware Users
---

### Post by taavi on 2008-04-27
Hi,

First of all thanks for 8.04 to all community... 

Macbook is the latest early 2008 model.

Problems are with fresh install of 8.04. Followed steps described here: [https://help.ubuntu.com/community/MacBook#head-d374bb9e1b7183c133759a8c6877a34c50c4ba7d](https://help.ubuntu.com/community/MacBook#head-d374bb9e1b7183c133759a8c6877a34c50c4ba7d)

Volume levels are all maxed with alsamixer, in Sound Preferences all options are set for ALSA and device is HDA Intel. According to that link, I think I've installed 1.0.16 version of alsa.

I've tweaked /etc/modprobe.d/alsa-base also and added these lines:
```

install snd-hda-intel position_fix=1 /sbin/modprobe --ignore-install snd-hda-intel $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-hda-intel

options snd-hda-intel model=auto
```

So there is no sound coming from inbuilt speakers nor headphones. Please ask further questions, I'll happily answer.

---

### Post by taavi on 2008-05-05
You may add information here, but it's not a topic anymore right now, since this girl uninstalled Ubuntu. Sad it may be...

---

