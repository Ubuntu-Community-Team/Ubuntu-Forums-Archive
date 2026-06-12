---
title: "avidemux 2 encode for ipod"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by gentlemanmasher on 2006-12-22
What should the settings be in avidemux to encode video for my ipod (or can I do it at all)  I have tried a couple different audio and video codecs and can't seem to find a combination.  

Please any help would be appreciated.

---

### Post by koshari on 2006-12-22
OK - this command should do it for the iPod:

ffmpeg -vcodec xvid -b 300 -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 96 -i input.avi -s 320x240 -aspect 4:3 ipod_output.mp4

Change your aspect ratio (4:3 or 16:9) as needed.

---

### Post by gentlemanmasher on 2006-12-22
~$ ffmpeg -vcodec xvid -b 300 -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 96 -i  Autobot Spike.avi -s 320x240 -aspect 4:3 ipod_output.mp4
ffmpeg: error while loading shared libraries: libraw1394.so.5: cannot open shared object file: No such file or directory


Here is what i put in tell me what I am doing wrong please I am really getting used to command line but now sure what I am doing wrong here.

Shoud I put in the name of the movie like above as you can see I am trying to do a transformers movie.

Thanks

---

### Post by dannyboy79 on 2006-12-22
do a search within aptitude to find the lib that is missing, also, you may want to remove the space that you have in your source.avi file, linux doesn't like spaces in filenames. or if you must leave them, i think you need to put quotes around the name maybe. good luck. oh, the output name of the movie doesn't really matter but if you want you can. don't forget, no spaces!

---

### Post by gentlemanmasher on 2006-12-22
ok know I am getting this error.

ffmpeg -vcodec xvid -b 300 -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 96 -i Pt2.avi -s 320x240 -aspect 4:3 ipod_output.mp4
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr 
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Sep 20 2006 00:26:15, gcc: 4.1.2 20060906 (prerelease) (Ubuntu 4.1.1-13ubuntu2)
Unknown codec 'xvid'


seems better.  Also where does the file go to or does it just change the source file.

---

### Post by gentlemanmasher on 2006-12-26
anyone

---

### Post by dannyboy79 on 2006-12-26
the codec issue is because you don't have the codec installed. did you install gstreamer0.10-plugins-ugly (go into synaptic and pick everything relating to the latest gstreamer which is 0.10) package and everything you would need to watch multimedia files. if you can't watch a xvid or divx file than you can encode one, you need the codec. as far as if it creates a new file or modifies the old one, can't tell ya, never have done it. I am only helping you based on common sense. sorry.

---

