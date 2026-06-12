---
title: "[SOLVED] ffmpeg"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by RadiationHazard on 2008-04-20
how do i convert a .ogg to a .mpg? what would be the code when i use ffmpeg?

---

### Post by spiderbatdad on 2008-04-20
```
ffmpeg -i file.ogg file.mpg
```

---

### Post by RadiationHazard on 2008-04-20
thank you!! :)

---

### Post by spiderbatdad on 2008-04-20
check out ```
man ffmpeg
```

---

### Post by RadiationHazard on 2008-04-20
nevermind
i got a error...
```
jordan@jordan-laptop:~$ ffmpeg -i /home/jordan/Desktop/out.ogg /home/jordan/Desktop/out.mpg
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jun  3 2007 20:59:25, gcc: 4.1.3 20070528 (prerelease) (Ubuntu 4.1.2-9ubuntu2)
[theora @ 0xb7ec3ac8]Theora bitstream version 30201
[theora @ 0xb7ec3ac8]544 bits left in packet 81
[theora @ 0xb7ec3ac8]7 bits left in packet 82
Input #0, ogg, from '/home/jordan/Desktop/out.ogg':
  Duration: 00:00:47.0, start: 0.066667, bitrate: 2225 kb/s
  Stream #0.0: Video: theora, yuv420p, 1280x800, 15.00 fps(r)
  Stream #0.1: Audio: vorbis, 44100 Hz, stereo, 499 kb/s
Output #0, mpeg, to '/home/jordan/Desktop/out.mpg':
  Stream #0.0: Video: mpeg1video, yuv420p, 1280x800, q=2-31, 200 kb/s, 15.00 fps(c)
  Stream #0.1: Audio: mp2, 44100 Hz, stereo, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[mpeg1video @ 0xb7ec3ac8]MPEG1/2 does not support 15/1 fps
Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height
jordan@jordan-laptop:~$ 

```

---

### Post by spiderbatdad on 2008-04-20
```
  ffmpeg -r 1 -i input.ogg -r 24 output.mpg

```
Didn't know it was a video. This might do it.

---

### Post by RadiationHazard on 2008-04-20
it worked!!
first thing that's worked for me on this computer today!
thank you so much :)

---

