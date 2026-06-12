---
title: "video encoding problems"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by mangurt on 2007-11-02
Greetings, I am trying to us ffmpeg to encode a file and this is the error I get

ed@ed-desktop:~/Videos$ ffmpeg -i nip.tuck.501.dsr.xvid.notv.avi -ab 128 -b1500kb/s niptuck.m4v
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --prefix=/usr --libdir=${prefix}/lib --shlibdir=${prefix}/lib --incdir=${prefix}/include/ffmpeg --enable-shared --enable-mp3lame --enable-gpl --enable-faad --mandir=${prefix}/share/man --enable-vorbis --enable-pthreads --enable-faac --enable-xvid --enable-dts --enable-amr_nb --enable-amr_wb --enable-pp --enable-libogg --enable-libgsm --enable-x264 --enable-a52 --extra-cflags=-Wall -g -fPIC -DPIC 
  libavutil version: 49.0.0
  libavcodec version: 51.11.0
  libavformat version: 50.5.0
  built on Nov  3 2006 21:14:27, gcc: 3.3.5 (Debian 1:3.3.5-13)
Input #0, avi, from 'nip.tuck.501.dsr.xvid.notv.avi':
  Duration: 00:50:49.9, start: 0.000000, bitrate: 963 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 624x352, 23.98 fps(r)
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 128 kb/s
ffmpeg: unrecognized option '-b1500kb/s'
ed@ed-desktop:~/Videos$ 


I am completely clueless on how to use ffmpeg, any idea?  I am trying to convert this file over from avi to mpeg4 to I can put it on my psp
Thanks

---

### Post by Maestro23 on 2007-11-02
Never used it myself, but the website has a Documentation section.
[http://ffmpeg.mplayerhq.hu/documentation.html](http://ffmpeg.mplayerhq.hu/documentation.html)

Good luck.

---

### Post by mangurt on 2007-11-02
I figured it out, I had to get rid of the 15000 b/r in the line.
Thanks!

---

