---
title: "Audio Extractor"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by oscarthefish on 2007-11-27
Looking for an "audio extractor" compatible with Ubuntu, Gutsy Gibbon for extracting audio from video file "youtube". Would appreciate any help. Thanks

---

### Post by Keith Hedger on 2007-11-27
In a terminal type:
ffmpeg -i "NAME OF YOUR FLASH VIDEO" -ac 2 -ar 48000 -ab 128 OUTPUTNAME.wav
And then to convert to mp3:
lame -m j -h -b 128 --resample 48 OUTPUTNAME.wav OUTPUTNAME.mp3
Hope this helps

---

