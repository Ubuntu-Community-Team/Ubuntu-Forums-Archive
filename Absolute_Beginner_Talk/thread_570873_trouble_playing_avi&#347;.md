---
title: "trouble playing avi&#347;"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by joot211 on 2007-10-08
I´ve been having some difficulty playing certain avi files. I´ve scoured the board looking for a fix. I´ve installed win32 codecs and a bunch of other stuff but still no luck. there must be something I´m missing.


Could not determine type of stream.

that is what totem tells me and

No demuxer found - stream format not recognised.

is what gxine tells me...

any suggestions would be appreciated

---

### Post by RomeReactor on 2007-10-08
Hi. For totem-gstreamer, try installing:
```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-ugly
```

For totem-xine or gxine:
```
sudo apt-get install libxine1-ffmpeg libxine-extracodecs
```

---

