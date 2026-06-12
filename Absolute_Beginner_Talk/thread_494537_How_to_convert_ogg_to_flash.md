---
title: "How to convert ogg to flash?"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by tarek on 2007-07-07
Hi, I recorded a video using recordmydesktop, the output is an ogg file, is there a way to convert it to flash?

cuz I want to post it on a web page.

Thanks,
tk

---

### Post by eternalsword on 2007-07-07
I'm not sure but I believe you can just upload it to google video and it will convert it to google video format for you .  Then you can link to the video on your page.  I'm not sure of any other way to accomplish this except maybe mencoder's experimental flash output

---

### Post by Kingsley on 2007-07-07
Zamzar.com is the best solution I can think of.

---

### Post by tarek on 2007-07-07
> **Kingsley said:**
> Zamzar.com is the best solution I can think of.

It doesn't have support for ogg :(

---

### Post by gvartser on 2008-02-26
This is one way of converting .ogg files into a flash movie format: (using: ffmpeg)

```
ffmpeg -i <infile>.ogg -b 384000 -s 640x480 -pass 1 -passlogfile log-file <outfile>.flv
```

Play arround with the bit rate and size to get it to your wishes.

/g

---

### Post by lattice on 2008-06-12
Hi,

I recorded something by recordmydesktop and used ffmpeg with the command line which was mentioned by gvartser.

It works almost fine, but audio and video have a delay. That means, the audio is a little earlier than the corresponding video such that I first say something and after that point to it while saying the next thing.

Did this happen to anyone else, too?

Do you know, what could be the reason and how I can convert from ogg to flash (or mp4) without the delay?

Thank you very much for an answer!
lattice

---

### Post by yyka on 2008-06-12
Hi Tarek for convert ogg to swf, you can use a site like mediaconvert,

[http://media-convert.com/convert/]("http://media-convert.com/convert/")

I have test it, that's ok :D :)

---

### Post by rscarriere on 2008-07-14
SOLVED - apparently the ffmpeg package has mp3 disabled and you are required to compile from source. ([https://wiki.ubuntu.com/ffmpeg](https://wiki.ubuntu.com/ffmpeg)) I only had luck using the compile from upstream svn instructions

Sorry - just another "me too" post. I've tried a number of things to get from ogg to flv including:

```

ffmpeg -i <infile>.ogg -b 384000 -s 640x480 -pass 1 -passlogfile log-file <outfile>.flv

```

Overall I'm able to get the video portion to work fine but I get no audio.  The ogg file is from gtk-recordMyDesktop.  Would appreciate any suggestions which don't involve uploading to a 3rd party site.

I'm using Hardy.

Here is the output I get:
```

$ ffmpeg -i in.ogg -b 384000 -s 640x480 -pass 1 -passlogfile log-file out.flv
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 12 2008 14:31:53, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu4)
[theora @ 0xb7ea06e8]Theora bitstream version 30201
[theora @ 0xb7ea06e8]544 bits left in packet 81
[theora @ 0xb7ea06e8]7 bits left in packet 82
Input #0, ogg, from 'in.ogg':
  Duration: 00:01:57.6, start: 0.066667, bitrate: 715 kb/s
  Stream #0.0: Video: theora, yuv420p, 800x624, 15.00 fps(r)
  Stream #0.1: Audio: vorbis, 48000 Hz, stereo, 499 kb/s
Output #0, flv, to 'out.flv':
  Stream #0.0: Video: flv, yuv420p, 640x480, q=2-31, pass 1, 384 kb/s, 15.00 fps(c)
Stream mapping:
  Stream #0.0 -> #0.0
[flv @ 0xb7ea06e8]removing common factors from framerate
[theora @ 0xb7ea06e8]Theora bitstream version 30201
[theora @ 0xb7ea06e8]544 bits left in packet 81
[theora @ 0xb7ea06e8]7 bits left in packet 82
Press [q] to stop encoding
frame= 1765 q=6.8 Lsize=    6000kB time=117.7 bitrate= 417.7kbits/s    
video:5972kB audio:0kB global headers:0kB muxing overhead 0.464821%

```

---

