---
title: "Rip CD with Sound Juicer and LAME"
date: 2005-11-02
forum: Absolute Beginner Talk
---

### Post by thinhlegolas on 2005-11-02
I followed the instruction here
[http://ubuntuforums.org/archive/index.php/t-957.html](http://ubuntuforums.org/archive/index.php/t-957.html)

However, when I click "Extract", it gives the error "Can't create Gstreamer encoders for LAME"

Please help :(

---

### Post by John.Michael.Kane on 2005-11-02
[http://www.emcken.dk/weblog/archives/99-MP3-encoding-with-Sound-Juicer.html](http://www.emcken.dk/weblog/archives/99-MP3-encoding-with-Sound-Juicer.html)
[http://www.ubuntuforums.org/showthread.php?t=22010](http://www.ubuntuforums.org/showthread.php?t=22010)
this may help

---

### Post by thinhlegolas on 2005-11-02
thanks SD, 

My problem now is it can rip fine with 

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc

However, if I use this

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc preset=1001

It will give error :(

---

### Post by thinhlegolas on 2005-11-03
Installed Grip, working with perfectly with LAME as external encoder...

---

