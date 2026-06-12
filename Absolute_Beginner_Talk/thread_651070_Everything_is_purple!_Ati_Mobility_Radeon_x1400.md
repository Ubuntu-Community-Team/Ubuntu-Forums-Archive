---
title: "Everything is purple! Ati Mobility Radeon x1400"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by nairod on 2007-12-27
I assume the card is working because I can read whats on the desktop but this just tells you how little I understand! Its a dell inspirion1505 with the 256 Ati Mobility Radeon x1400 video card, I´ve installed ubuntu 7.10 ... all is ok (except wireless, will deal with that later), but all my videos look purple/pink! The human characters look pale blue! Is there something I am supposed to configure? Help.

---

### Post by mike555 on 2007-12-27
There is a fix , but I forgot where I read about it , just search and you'll find it ......

---

### Post by mike555 on 2007-12-27
--- found it .....       try this:

launch gstreamer-properties from terminal
change the video output plugin to custom
change the video output pipeline to:

ffmpegcolorspace ! video/x-raw-yuv,format=(fourcc)YV12 ! xvimagesink

Test .....

---

