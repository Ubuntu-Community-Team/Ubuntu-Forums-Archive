---
title: "Playing AVI's"
date: 2005-09-21
forum: Absolute Beginner Talk
---

### Post by Alpha_Cluster on 2005-09-21
How do i get totem or anther program to play AVI files i got XMMS to play audio files but nothing will play video files.

---

### Post by mustang on 2005-09-21
Can you be a bit more specific? Have you tried using totem to open an AVI file? Like

```
totem videofile.avi
```

If that doesn't work, try xine, mplayer2, or VLC. I personally find VLC the best. More info if needed is [here](http://www.frankandjacq.com/ubuntuguide/5.04/index.html) on how to install those video players.

edit: be sure to install the codecs as well. I believe the package is called win32codecs or something like that---it is on the link I posted above.

---

### Post by Alpha_Cluster on 2005-09-21
Well that is kindof what im asking is where can i find the codecs since for some crazy reason Totem comes without a codec.
And thanks for the link.

---

### Post by doclivingston on 2005-09-21
The [Restricted Formats](https://wiki.ubuntu.com/RestrictedFormats?action=show) page of the wiki contains information on how to install the plugins so that GStreamer (which totem uses) can play other formats.

---

