---
title: "how do i cancel streaming video in firefox?"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by zarbov on 2007-07-26
hi !

although i saw alot of threads asking how to install the plugin that does streaming video in firefox, i wish to cancel it.

i tried to remove the gstreamer-ffmpeg package, but then my videos didn't work at all, and  mplayer demanded this package to be installed in order to make them work again.

any ideas? i know it's probably something very simple that i've missed....

thank you!

---

### Post by kevinlyfellow on 2007-07-26
There are a couple of ways.  If you use totem, you can uninstall the totem plugin
```
sudo apt-get remove totem-mozilla
```

or you can install the extension MediaPlayerConnectivity which prevents embedded movies from playing unless you tell it to (or even open the movie in an external player).

---

### Post by zarbov on 2007-07-26
thank you!!

---

