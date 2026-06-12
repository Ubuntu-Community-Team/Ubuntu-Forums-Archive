---
title: "ultra noobish video converting"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by Falc7 on 2008-02-17
I am following this guide [http://www.ubuntugeek.com/convert-flv-google-videos-to-mpg-using-ffmpeg.html](http://www.ubuntugeek.com/convert-flv-google-videos-to-mpg-using-ffmpeg.html)
and my ultra noobish question is this, when it says open a terminal and go to the folder with the flv file, how do i do that? 

His was this:
ffmpeg -i jokes.flv -ab 56 -ar 22050 -b 500 -s 320×240 jokes.mpg

mine is this 
ffmpeg -i TS chinese documentary.flv -ab 56 -ar 22050 -b 500 -s 320×240 TS chinese documentary.mpg

but the terminal says this is wrong.

EDIT: another question, i am using pitivi video editor to edit some stuff, but how to i pause a frame, and cut it in half at the frame?

---

### Post by timbounceback on 2008-02-17
surround the filenames with quotes, and if it still doesn't work; post the output

---

### Post by Falc7 on 2008-02-17
TS chinese documentary.flv: I/O error occured
Usually that means that input file is truncated and/or corrupted.

I think the problem is that i do not know how to tell the terminal where the file i want to convert is

---

### Post by markharding557 on 2008-02-17
> **Falc7 said:**
> I am following this guide [http://www.ubuntugeek.com/convert-flv-google-videos-to-mpg-using-ffmpeg.html](http://www.ubuntugeek.com/convert-flv-google-videos-to-mpg-using-ffmpeg.html)
and my ultra noobish question is this, when it says open a terminal and go to the folder with the flv file, how do i do that? 

His was this:
ffmpeg -i jokes.flv -ab 56 -ar 22050 -b 500 -s 320×240 jokes.mpg

mine is this 
ffmpeg -i TS chinese documentary.flv -ab 56 -ar 22050 -b 500 -s 320×240 TS chinese documentary.mpg

but the terminal says this is wrong.

EDIT: another question, i am using pitivi video editor to edit some stuff, but how to i pause a frame, and cut it in half at the frame?

in a terminal type> cd /folder(where your file is)
cd means change directory
more info on command line use here
[https://help.ubuntu.com/7.10/basic-commands/C/]("https://help.ubuntu.com/7.10/basic-commands/C/")

---

### Post by Falc7 on 2008-02-17
thanks for that link, i'm sure it will be useful
i entered cd ~/Desktop
because the file is on the desktop, this is what happened:
wer@wer-laptop:~/Desktop$ ffmpeg -i TS chinese documentary.flv -ab 56 -ar 22050 -b 500 -s 320×240 TS chinese documentary.flv
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jun  3 2007 20:59:25, gcc: 4.1.3 20070528 (prerelease) (Ubuntu 4.1.2-9ubuntu2)
TS: I/O error occured
Usually that means that input file is truncated and/or corrupted.

---

