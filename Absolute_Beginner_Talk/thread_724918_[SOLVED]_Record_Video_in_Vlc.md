---
title: "[SOLVED] Record Video in Vlc"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by adi_das on 2008-03-15
How do I record streaming video in VLC or Totem player?

---

### Post by Stevko on 2008-03-15
```
vlc  --sout file/ts:output.mpg *video_stream*
```
output.mpg is name of output file, ts is container format. You can use ts, ps, ogg and some others (if you use ogg, it is good to give ogg extension to output file).. video_stream is the url for your stream.

You can also try to use mplayer -dumpstream *video_stream*

---

