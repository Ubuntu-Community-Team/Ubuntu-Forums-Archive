---
title: "Audio Problem with Xine"
date: 2006-05-05
forum: Absolute Beginner Talk
---

### Post by TheFourElements on 2006-05-05
I am trying to play a movie in xine that I ripped off a DVD and then converted to .avi. I can get video but audio won't play I get a message that says:
------------------------------------------------------------------------
the stream (filepath) uses an unsupported codec:

Audio Codec: MPEG layer 2/3 (0x55)

Do you want to start playback anyway?

yes/no
------------------------------------------------------------------------
Any help with this would be greatly appreciated.

---

### Post by yabbadabbadont on 2006-05-05
Read through this: [https://wiki.ubuntu.com/RestrictedFormats?highlight=%28restricted%29](https://wiki.ubuntu.com/RestrictedFormats?highlight=%28restricted%29)

You need mp3 support most likely.

---

### Post by zerhacke on 2006-05-05
To get sound on that video, and mp3 in general, in a terminal type ```
sudo apt-get install  gstreamer0.8-mad
``` and hit enter.

---

### Post by TheFourElements on 2006-05-05
awesome guys. Thanks. It worked.

---

