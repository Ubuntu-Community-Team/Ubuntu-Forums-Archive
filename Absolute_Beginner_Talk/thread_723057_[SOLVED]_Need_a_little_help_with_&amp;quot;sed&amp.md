---
title: "[SOLVED] Need a little help with &amp;quot;sed&amp;quot;"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by descentspb on 2008-03-13
I need to get a video stream's resolution into stdout.

I want to make it like this:

```
ffmpeg -i input.avi | sed ...something...
```

because in a large output of "ffmpeg -i input.avi" there is a resolution looking like this "123x123". I need to get only this resoluton and remove everything else, preferably 2 commands to get each of them (x and y).

---

### Post by descentspb on 2008-03-13
the output looks approx. like this:

> FFmpeg version SVN-r11870, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --
enable-liba52 --enable-avisynth --enable-libfaac --enable-libfaad --enable-libgs
m --enable-libmp3lame --enable-libnut --enable-libtheora --enable-libvorbis --en
able-libx264 --enable-libxvid --cpu=i686 --enable-memalign-hack --extra-ldflags=
-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Feb  5 2008 23:46:38, gcc: 4.2.3

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000
/1) -> 14.99 (15000/1001)
Input #0, flv, from 'd:/compiz.flv':
  Duration: 00:04:59.3, start: 0.000000, bitrate: 56 kb/s
    Stream #0.0: Video: flv, yuv420p, 320x240 [PAR 0:1 DAR 0:1], 14.99 tb(r)
    Stream #0.1: Audio: mp3, 22050 Hz, mono, 56 kb/s
Must supply at least one output file

---

### Post by pix_ on 2008-03-13
there is probably a better way to do this, but:

```

ffmpeg -i input.avi | sed -n 's/.*[^0-9]\([0-9]\+x[0-9]\+\).*/\1/p'

```

the output of ```
mplayer -identify
``` would probably be easier to parse reliably.

pix.

---

