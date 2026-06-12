---
title: "MP3 and AVI"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by Ryan H on 2007-02-15
I'm trying to merge a video and audio file together into one AVI. The files:
```
Input #0, avi, from 'movie.avi':
  Duration: 00:02:27.7, start: 0.000000, bitrate: 745 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 320x240, 24.00 fps(r)
Input #1, mp3, from 'audio.mp3':
  Duration: 00:06:36.5, start: 0.000000, bitrate: 32 kb/s
  Stream #1.0: Audio: mp3, 12000 Hz, mono, 32 kb/s

```

I was using the command ```
ffmpeg -i movie.avi -i audio.mp3 -b 200 -ac 1 -ab 12 -map 0.0 -map 1.0 problem-webs.avi
```

The problem is it wants to output the video using the mp2 codec, which apparently doesn't support the sample rate of 12000, how do I output it as mp3?

Thank you in advance.

-Ryan H

---

### Post by Ryan H on 2007-02-15
Is it possible?

-Ryan H

---

