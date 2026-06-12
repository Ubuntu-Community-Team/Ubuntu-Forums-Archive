---
title: "[SOLVED] Totem Plugins"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by ExpatPaul on 2007-11-14
I've just tried to play a DVD using the Totem Movie Player and am getting the following message:

> Totem cannot play this type of media (DVD) because it does not have the appropriate plugins to be able to read from the disc.

Can anyone help me with finding and installing the correct plugins?

---

### Post by Inxsible on 2007-11-14
Applications>>Add/Remove. Search for "gstreamer" without the quotes under all applications. Install all of them.

See if that works.

---

### Post by mikewhatever on 2007-11-14
Try this [https://help.ubuntu.com/community/RestrictedFormats?highlight=%28formats%29%7C%28restricted%29#head-ade7b6cc5a280ee943fd7884cf7dc49ebe7e22ca](https://help.ubuntu.com/community/RestrictedFormats?highlight=%28formats%29%7C%28restricted%29#head-ade7b6cc5a280ee943fd7884cf7dc49ebe7e22ca)

---

### Post by ExpatPaul on 2007-11-14
> **mikewhatever said:**
> Try this [https://help.ubuntu.com/community/RestrictedFormats?highlight=%28formats%29%7C%28restricted%29#head-ade7b6cc5a280ee943fd7884cf7dc49ebe7e22ca](https://help.ubuntu.com/community/RestrictedFormats?highlight=%28formats%29%7C%28restricted%29#head-ade7b6cc5a280ee943fd7884cf7dc49ebe7e22ca)


Thanks. I found [this]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")...

> sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine
sudo /usr/share/doc/libdvdread3/install-css.sh

...  which appears to have worked perfectly

:)

---

