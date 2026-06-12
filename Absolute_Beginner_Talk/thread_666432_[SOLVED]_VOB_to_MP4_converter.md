---
title: "[SOLVED] VOB to MP4 converter?"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by fraser_m on 2008-01-13
Are there any good graphical Vob to MP4 converters for Ubuntu?

Thanks.

---

### Post by Matt Yun on 2008-01-13
I know you asked for a graphical vob to mp4 converter, but just in case you are interested, here is my unsophisticated, hacked-together bash script for doing it with transcode and XviD:

```

#!/bin/sh
# /usr/local/bin/vob2avi
# transcode dvd *.VOB files to xvid *.avi
# usage: vob2avi outputfile.avi  

# be in same directory as *.VOB files; 
# there can only be *.VOB files; move non-VOB files into another directory

transcode -H 10 -a 0 -x vob -i ./ -w 900,50 -d -y xvid -o ./$1 --print_status 20 && echo DVDRIP_SUCCESS

```

---

### Post by fraser_m on 2008-01-13
I just found the Transcode Wizard in VLC! Yay!

Sorted

---

### Post by thelatinist on 2008-01-13
> **fraser_m said:**
> I just found the Transcode Wizard in VLC! Yay!

Sorted

Don't forget to mark this thread [Solved] sing thread tools so others don't keep coming here thinking you still need help. :-)

---

### Post by Jose Catre-Vandis on 2008-01-13
Also you can try:

Project X: to convert the vob to an mpg
then
The Video Convert Nautilus Script found here on the forum

---

### Post by QwUo173Hy on 2008-02-06
fraser_m, I'm trying to use VLC to transcode a 4GB VOB file to an mpeg of under 1GB. Can you tell me what settings you used? I used the default MPG-1 but got a very poor quality output file.

---

### Post by fraser_m on 2008-04-04
**The files this outputs are SCREWED! Please use the script below!**

In case anyone is still bothered, I used VLC to File > Open File, checked "Stream / Save", then "Settings" and set:

"Outputs | File" to checked and the end filename (must be .mp4),
"Encapsulation Method" to MP4,
"Video Codec" checked and kept "mp4v",
"Bitrate" for video to 1024,
"Audio Codec" to "mp4a",
"Bitrate" for audio to 128 (it's good enough for me!),
Then OK,
Then start playing your file, it should play, just without video showing.

Or, when you are changing settings for streaming, in the top box put:
```
:sout=#transcode{vcodec=mp4v,vb=1024,scale=1,acodec=mp4a,ab=128,channels=2}:duplicate{dst=std{access=file,mux=mp4,dst="/home/fraser/FileNameHere.mp4"}}
```(Change the FileNameHere to whatever you want though)
And it's done, but if you want iPod compatibility, insert:
```
width=640,canvas-height=480,
```just after ":sout=#transcode{"


K?


[B]Proper way to do it!
[/B]
Get podEncoder from here...
[http://diveintomark.org/archives/2007/06/07/howto-batch-encode-video-for-ipod-under-linux-2007-edition](http://diveintomark.org/archives/2007/06/07/howto-batch-encode-video-for-ipod-under-linux-2007-edition)
Install the dependencies, then get usage from here...
[http://diveintomark.org/archives/2006/08/30/ipod-video-howto](http://diveintomark.org/archives/2006/08/30/ipod-video-howto)

Fixeded.

---

