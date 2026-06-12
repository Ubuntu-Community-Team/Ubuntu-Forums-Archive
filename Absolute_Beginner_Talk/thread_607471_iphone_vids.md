---
title: "iphone vids"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by IISpII on 2007-11-09
does anyone know how to change aXXo's divx-avi's to regular avi's for iphone use. I have a windows computer to upload them to my iphone so my only problem is converting them to regular avi's.

(p.s. if you do not know who aXXo is then u do not deserve to own a computer.)

([http://torrentfreak.com/interview-axxo-the-most-popular-dvd-ripper-on-bittorrent/]("http://torrentfreak.com/interview-axxo-the-most-popular-dvd-ripper-on-bittorrent/"))

---

### Post by MrFSL on 2007-11-09
> (p.s. if you do not know who aXXo is then u do not deserve to own a computer.)


And if you don't know that there is no such thing as "regular avi's" then you shouldn't criticize! Here goes - AVI is the container format. It does not define the video nor the audio.

For instance - I can encode Mpeg4 Video and MP3 Audio and wrap it in an AVI (this is DIVX!) and the combinations are endless...

So the question is what is the audio/video requirements for the iPhone? Does it support B-Frames? Interlacing? Max FPS? Max aspect ratio? Max Bitrate? 

For more information you might want to read up on mplayer, mencoder, and ffmpeg.

---

### Post by TheScrutinist on 2007-11-09
I believe the iPhone, like the iPod, needs video files to be in mp4 or one of the Quicktime formats. Since you're familiar with Axxo (and therefor, fit to own a computer) then I'm assuming you can use similar methods to get Video Converter for Windows. Or, you could always download Videora, which is a free iPod/iPhone converer utility. 

VLC Player also has a few transcoding utilities, and a few plugins. That is usually my application of choice for video conversion.

---

### Post by tyfius on 2007-11-09
Use the [Medibuntu]("http://www.medibuntu.org/") repositories to install a custom ffmpeg compile and use [WinFF]("http://biggmatt.com/winff/") to convert video to mp4 (select ipod output).

Note: if you are using Hardy you will need to force the gutsy version to be used (can be done with synaptic) but each time you do a dist-upgrade it will remove this downgraded version.

---

### Post by 3rdalbum on 2007-11-09
Give this a go; it's actually for Sony Walkmans, but the file format is probably very similar. If it doesn't work, at least you'll be able to edit this command to make it work rather than have to construct one from scratch:

ffmpeg -i *inputfile* -b 576k -s 320x240 -vcodec mpeg4 -ab 220k -ar 44100 -acodec libfaac *outputfile.mp4*

**Replace inputfile and outputfile with the actual source and destination, of course.**

If ffmpeg tells you that "libfaac" is an "unknown encoder", try just "faac" or "aac" instead.

---

