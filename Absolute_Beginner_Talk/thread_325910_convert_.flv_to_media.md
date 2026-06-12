---
title: "convert .flv to media"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by bloody_tears on 2006-12-26
Hi! 
How can I convert flash(.flv) file to normal video file?

---

### Post by divague on 2006-12-26
use this in a terminal

 ffmpeg -i video.flv -ab 56 -ar 22050 -b 500  -s 320x240 video.mpg

you have to have ffmpeg installed

---

