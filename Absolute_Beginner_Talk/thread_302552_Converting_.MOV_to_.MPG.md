---
title: "Converting .MOV to .MPG?"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by kbsuperstar on 2006-11-18
What program(s) can I use to convert a .MOV to a .MPG (MPEG) file?

Thanks.

---

### Post by MrFSL on 2006-11-18
short answer use ffmpeg.
from the terminal

ffmpeg -i input.mov output.mpg

This is very basic. You probably want to read the man page and google around a bit. Don't be surprised if you end up with something that looks more like:

ffmpeg -i input.mov -acodec mp2 -abitrate 128 -ac 2 -vcodec mpeg1video -qscale 3 -vbitrate 2048 -mbd 2 outfile.mpg

hope this gets you where you need to go.

MrFSL

---

### Post by kbsuperstar on 2006-11-18
Is there anyway program that can convert certain movie file types to something smaller in memory?

Thanks!

---

### Post by snoopyq on 2007-12-07
so i do this:
$ffmpeg -i A002-175.DEMO.mov 1.mpg

and get this


FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jun  3 2007 20:59:25, gcc: 4.1.3 20070528 (prerelease) (Ubuntu 4.1.2-9ubuntu2)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'A002-175.DEMO.mov':
  Duration: 00:00:13.6, start: 0.000000, bitrate: 170 kb/s
  Stream #0.0(eng): Video: svq3, yuv420p, 192x144, 14.98 fps(r)
Output #0, mpeg, to '1.mpg':
  Stream #0.0: Video: mpeg1video, yuv420p, 192x144, q=2-31, 200 kb/s, 15.00 fps(c)
Stream mapping:
  Stream #0.0 -> #0.0
[mpeg1video @ 0xb7e40ac8]MPEG1/2 does not support 15/1 fps
Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height

is there something that just works without errors first time every time?

---

### Post by stooshbunutu on 2008-03-11
try the ffmpeg GUI winff

[http://www.biggmatt.com/winff](http://www.biggmatt.com/winff)

---

