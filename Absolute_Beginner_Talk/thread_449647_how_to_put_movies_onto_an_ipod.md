---
title: "how to put movies onto an ipod"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by moredhel on 2007-05-20
I have some AVI files that I would like to put onto my ipod - how would I go about that?

---

### Post by moredhel on 2007-05-20
anyone? I have the files, but I don't think amarok can move them over...

---

### Post by freakavoid on 2007-05-20
If you want to play them on your iPod then you can't. You have to convert them in mov or mp4. You can try ffmpeg for this purpose. If you only want to store the files on the iPod you can drag+drop them using nautilus though.

---

### Post by moredhel on 2007-05-20
are there any graphical frontends to ffmpeg? Or could you explain the commands needed to convert an avi to mov?

---

### Post by freakavoid on 2007-05-20
I don't think it supports mov. It's fairly straight forward with mp4

```

ffmpeg -i inputfile.avi outputfile.mp4

```

Besides that you have whole lot of other options regarding bitrate etc. Use the man page for details.

```

man ffmpeg

```

edit: or you can just look [here]("http://ubuntuforums.org/showthread.php?t=114946")

---

### Post by moredhel on 2007-05-20
It come up with this:

```
ffmpeg -i dreamtheaterbudokan.avi dreamtheaterbudokan.mp4
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr 
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Jan 28 2007 22:48:38, gcc: 4.1.2 20070106 (prerelease) (Ubuntu 4.1.1-21ubuntu7)
Input #0, avi, from 'dreamtheaterbudokan.avi':
  Duration: 02:52:48.0, start: 0.000000, bitrate: 1135 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 416x240, 23.98 fps(r)
  Stream #0.1: Audio: ac3, 48000 Hz, 5:1, 448 kb/s
Output #0, mp4, to 'dreamtheaterbudokan.mp4':
  Stream #0.0: Video: mpeg4, yuv420p, 416x240, q=2-31, 200 kb/s, 23.98 fps(c)
  Stream #0.1: Audio: 0x0000, 48000 Hz, stereo, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[mpeg4 @ 0xb7e72508]removing common factors from framerate
Unsupported codec for output stream #0.1
```

---

### Post by freakavoid on 2007-05-20
OK.. The below command line is taken from that howto. 

```
ffmpeg -i dreamtheaterbudokan.avi -f mp4 -vcodec mpeg4 -maxrate 1000 -b 700 -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192 -s 320x240 -aspect 4:3 dreamtheaterbudokan.mov
```

it works fine by me; but on the other side the first one did too :confused:

---

### Post by moredhel on 2007-05-20
grrr!

```
ffmpeg -i dreamtheaterbudokan.avi -f mp4 -vcodec mpeg4 -maxrate 1000 -b 700 -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192 -s 320x240 -aspect 4:3 dreamtheaterbudokan.mov
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr 
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Jan 28 2007 22:48:38, gcc: 4.1.2 20070106 (prerelease) (Ubuntu 4.1.1-21ubuntu7)
dreamtheaterbudokan.avi: I/O error occured
Usually that means that input file is truncated and/or corrupted.
```

same for .mp4 and .mov

---

### Post by freakavoid on 2007-05-20
are you sure the file names are correct? AVI instead of avi for example? And of course you have to run that command inside the directory where your avi file is located.

---

### Post by moredhel on 2007-05-20
done again and this time:

```
ffmpeg -i dreamtheaterbudokan.avi -f mp4 -vcodec mpeg4 -maxrate 1000 -b 700 -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192 -s 320x240 -aspect 4:3 dreamtheaterbudokan.mov
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr 
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Jan 28 2007 22:48:38, gcc: 4.1.2 20070106 (prerelease) (Ubuntu 4.1.1-21ubuntu7)
Input #0, avi, from 'dreamtheaterbudokan.avi':
  Duration: 02:52:48.0, start: 0.000000, bitrate: 1135 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 416x240, 23.98 fps(r)
  Stream #0.1: Audio: ac3, 48000 Hz, 5:1, 448 kb/s
Unknown codec 'aac'

```

---

### Post by moredhel on 2007-05-20
I also tried doing other files and it says the same thing about it being corrupted or whatever.

and i removed the acodec part of the command you gave me and it gave the old message...

---

### Post by freakavoid on 2007-05-20
The message about the file being corrupted is an I/O error. It can also be produced if ffmpeg cannot find the input file. But the unknown codec problem is easy to solve. Just try installing it:

```

sudo apt-get install libfaac0

```

I know it's a pain in the neck. Have you looked at the howto i suggested before? It uses a gui for ffmpeg. Maybe it would be easier.

---

### Post by moredhel on 2007-05-20
it says the latest version is already installed.

And also - I was looking for a gui, but didn't know one - any ideas? :D

---

### Post by freakavoid on 2007-05-20
OK, i must say I reached the end of my modest knowledge :) Take a look [here]("http://ubuntuforums.org/showthread.php?t=114946").

cheers.

---

