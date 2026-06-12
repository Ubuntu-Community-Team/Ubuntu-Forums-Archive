---
title: "ffmpeg jpeg animation"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by NESFreak on 2006-07-17
i know ffmpeg is capable of creating animations from jpeg files, just wanna know how.
i tried "ffmpeg -i *.jpg -r 15 -s cif -aspect 4:3 -vcodec xvid -sameq -pass 2 -f avi movie.avi" but it returns "
FFmpeg version CVS, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --prefix=/usr --libdir=${prefix}/lib --incdir=${prefix}/include/ffmpeg --enable-shared --enable-mp3lame --enable-gpl --enable-faad --mandir=${prefix}/share/man --enable-vorbis --enable-pthreads --enable-faac --enable-xvid --enable-dts --enable-amr_nb --enable-amr_wb --enable-pp --enable-libogg --enable-a52 --enable-theora --enable-libgsm --enable-x264 --enable-a52bin
  libavutil version: 49.0.0
  libavcodec version: 51.9.0
  libavformat version: 50.4.0
  built on Jun  4 2006 15:08:12, gcc: 4.0.3 (Ubuntu 4.0.3-1ubuntu5)
000001.jpg: Unknown format
"

any help please NESFreak

---

