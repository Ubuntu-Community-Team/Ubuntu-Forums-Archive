---
title: "tried converting these .avi files to ipod videos but"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by hanzj on 2006-08-17
Hello, I've followed the syntax for ffmpeg on [https://help.ubuntu.com/community/iPodVideoEncoding#head-34d699f8506a9acf5be9c4743c812f0ee1bf3df4](https://help.ubuntu.com/community/iPodVideoEncoding#head-34d699f8506a9acf5be9c4743c812f0ee1bf3df4), but I removed the "-acodec aac" part, because
1) doing so gave me this error "Unknown codec 'aac'"
2) these videos don't have sound anyway

So the command I used was

> ffmpeg -i wpegg.avi -f mp4 -vcodec mpeg4 -maxrate 1000 -b 700 -qmin 3 -qmax 5 -bufsize 4096 -g 300 -ab 192 -s 320x240 -aspect 4:3 wpegg.mov

The resulting wpegg.mov file works fine. But the other avi files can't convert.

For example,
I ran the same command for wpsv2.avi 
 > ffmpeg -i wpsv2.avi -f mp4 -vcodec mpeg4 -maxrate 1000 -b 700 -qmin 3 -qmax 5 -bufsize 4096 -g 300 -ab 192 -s 320x240 -aspect 4:3 wpsv2.mov


But an error message:
> ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --extra-cflags=-fomit-frame-pointer -DRUNTIME_CPUDETECT --build i486-linux-gnu --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --prefix=/usr
  built on Nov 24 2005 10:19:02, gcc: 4.0.3 20051121 (prerelease) (Ubuntu 4.0.2-4ubuntu3)
Input #0, avi, from 'wpsv2.avi':
  Duration: 00:00:08.8, start: 0.000000, bitrate: 5499 kb/s
  Stream #0.0: Video: msmpeg4v2, yuv420p, 720x480, 29.97 fps
  Stream #0.1: Audio: pcm_s16le, 48000 Hz, stereo, 1536 kb/s
File 'output_file.mov' already exists. Overwrite ? [y/N] y
Output #0, mp4, to 'output_file.mov':
  Stream #0.0: Video: mpeg4, yuv420p, 320x240, 29.97 fps, q=3-5, 700 kb/s
  Stream #0.1: Audio: 0x0000, 48000 Hz, stereo, 192 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Unsupported codec for output stream #0.1


The videos I'm trying to encode into iPod video format are:

[LIST]
[*][http://coachesinfo.com/movies/articles/waterpolo/wpfv2.avi](http://coachesinfo.com/movies/articles/waterpolo/wpfv2.avi)

[*][http://coachesinfo.com/movies/articles/waterpolo/wpsv2.avi](http://coachesinfo.com/movies/articles/waterpolo/wpsv2.avi)

[*][http://coachesinfo.com/movies/articles/waterpolo/wpfv1.avi](http://coachesinfo.com/movies/articles/waterpolo/wpfv1.avi)

[*][http://coachesinfo.com/movies/articles/waterpolo/wpsv1.avi](http://coachesinfo.com/movies/articles/waterpolo/wpsv1.avi)

[*][http://coachesinfo.com/movies/articles/waterpolo/wpegg.avi](http://coachesinfo.com/movies/articles/waterpolo/wpegg.avi)
[/LIST]

---

### Post by hanzomon4 on 2006-08-17
you need to compile ffmpeg from source to enable other formats that the repo version lacks. Their's also a gui app for converting videos to the "ipod format" [ HowTo: Encode Video for iPod Video]("http://www.ubuntuforums.org/showthread.php?t=114946&highlight=ipod+video") 
If I knew how to post an attachment I could post a deb you could try.

---

### Post by hanzj on 2006-08-17
What I don't understand is how come it worked for wpegg.avi, but none of the other avi's. They are all from the same website.

---

### Post by hanzomon4 on 2006-08-18
Not sure... I encoded 1, but I'll try the rest to see if it's a bug with ffmpeg or the video files

Try this line ```
ffmpeg -vcodec xvid -b 2000 -g 300 -acodec aac -ac 2 -ab 96 -i INPUT_VIDEO -aspect 4:3 -s 320x240 OUTPUT_VIDEO.mp4 or mov
```
replace INPUT and OUTPUT video with the names of the input file and the name you want the output file to called.

---

### Post by hanzomon4 on 2006-08-18
Delete

---

### Post by hanzomon4 on 2006-08-18
They all encoded fine here. 
Try this .deb I compiled it with all the formats (The ones that are no include in the ffmpeg from the repos) If you have a p 1,2,3,4 it should work for you. 

EDIT: Crap it's to big to upload. Follow that howto I posted a link to "you just need the ffmpeg part"

---

