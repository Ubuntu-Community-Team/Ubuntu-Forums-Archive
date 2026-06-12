---
title: "Video to audio?"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by xzin on 2008-01-29
I got video FLV file, that I would like to convert to audio file, preferably mp3 or wav. What is the easiest way to do this with Ubuntu?

---

### Post by chris200x9 on 2008-01-29
probably media-convert.com


that would be the *easiest* but I'm pretty sure you could use Avidemux and choose the video to input then put mp3 output with no video output


edit: no I don't see an option for no video output on Avidemux, sorry try media-convert.com, I'm 99% sure it'll work :)

---

### Post by xzin on 2008-01-29
Thanks for that site, added it to bookmarks also :popcorn:

---

### Post by mridkash on 2008-01-29
in terminal run this command,
```
ffmpeg -i /path/to/video.flv /path/to/audio.mp3
```

If you see command not found error,

install ffmpeg first
run 
```
sudo apt-get install ffmpeg
```
in terminal

---

### Post by stooshbunutu on 2008-01-31
for .flv files there is a realy easy porgram for converting to .wav files of just sound I use [winff]("http://biggmatt.com/files/winff-0.33-i386.deb") that uses the [ffmpeg]("http://packages.ubuntu.com/gutsy/graphics/ffmpeg") codec to covert the file. From there you can switch it about simply using [sound converter]("http://packages.ubuntu.com/gutsy/sound/soundconverter")

hope this helps you, it works great for me.:)

---

### Post by stoodleysnow on 2008-01-31
stooshbunutu?
Almost sounds as daft as stoodleysnow!
As for FLV to wave, there's always a way. Whether it works is another matter... :-k

---

