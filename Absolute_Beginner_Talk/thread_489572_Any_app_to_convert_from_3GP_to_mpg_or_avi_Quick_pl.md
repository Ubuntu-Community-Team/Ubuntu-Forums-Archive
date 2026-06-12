---
title: "Any app to convert from 3GP to mpg or avi? Quick please!:-("
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by Kosimo on 2007-07-01
As the tittle...
I really need to convert a 3GP file into a AVI or MPG....

Any easy app to use in feisty?

Thanks!

---

### Post by Kosimo on 2007-07-01
plz...  :'-(

---

### Post by chili555 on 2007-07-01
Sure, there is *ffmpeg.* Check here: [http://feeds.goa-india.org/mypapit__gnu_linux__blog/2007/01/?media=rss](http://feeds.goa-india.org/mypapit__gnu_linux__blog/2007/01/?media=rss)

This suggests the command would be:```
ffmpeg -i clip.3gp -f avi -vcodec xvid -acodec mp3 -ar 22050 file.avi
```You can find out what the various options do with *man ffmpeg*.

---

### Post by Kosimo on 2007-07-01
> **chili555 said:**
> Sure, there is *ffmpeg.* Check here: [http://feeds.goa-india.org/mypapit__gnu_linux__blog/2007/01/?media=rss](http://feeds.goa-india.org/mypapit__gnu_linux__blog/2007/01/?media=rss)

This suggests the command would be:```
ffmpeg -i clip.3gp -f avi -vcodec xvid -acodec mp3 -ar 22050 file.avi
```You can find out what the various options do with *man ffmpeg*.

Thank you so much!!
I got an error

> -laptop:~/Desktop$ ffmpeg -i 1.3gp -f avi -vcodec xvid -acodec mp3 -ar 22050 file.avi
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr 
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Jan 28 2007 22:48:38, gcc: 4.1.2 20070106 (prerelease) (Ubuntu 4.1.1-21ubuntu7)

Seems that stream 0 comes from film source: 250.00 (1000/4) -> 10.00 (10/1)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '1.3gp':
  Duration: 00:08:52.8, start: 0.000000, bitrate: 121 kb/s
  Stream #0.0(jpn): Video: h263, yuv420p, 176x144, 10.00 fps(r)
  Stream #0.1(jpn): Audio: samr / 0x726D6173, 8000 Hz, mono
Unknown codec 'xvid'


Do I have to install some codec as well?

Thanks again! ;)

---

### Post by chili555 on 2007-07-01
You might try *sudo apt-get install libxvidcore4* or try another vcodec, like mpeg4. I don't really know, since I don't have any 3gp file to experiment with.

---

### Post by kalon33 on 2007-07-08
I've a clue for you ! I found a nice app to do this job, from and to 3GP, AMR... Here is the link [http://www.miksoft.net/mobileMediaConverter.htm](http://www.miksoft.net/mobileMediaConverter.htm)

Hope that it helps you.

--kalon33

---

