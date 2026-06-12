---
title: "devede slow?"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by fedex1993 on 2008-01-13
okay i am trying to make a video dvd and its is very slow i left it on for an hour and it was onl 15% done why is it so slow?

---

### Post by oldos2er on 2008-01-13
What are your system specs? I have a Core 2 Duo with 2GB RAM, and it takes anywhere from an hour fifteen minutes to an hour and a half to encode an avi file, depending on the file size.

---

### Post by fedex1993 on 2008-01-15
well i am running on 1.8ghz dual core 1gb of ram this is on a laptop and it took me an hour to get to 50% which i think is way to long.

---

### Post by sstusick on 2008-02-25
I experience this issue too. Why is devede so slow? IIRC on Windows using WinAVI, it took about 30 minutes tops to convert to DVD (700 MB file). Anyone know of a faster program, that is similiar to Devede?

---

### Post by halitech on 2008-02-25
I have a P4 1.8 with 896 meg of ram, IDE 160 gig drive and it takes me about 3 hours to do a conversion from a 700meg avi file to a ready to burn dvd ISO which is about the same as what Nero used to take on the same machine (but only 512meg of ram) so you are about on par with what I'm doing. What can make a difference is what video output options you select which will determine the overall file size of the completed file (I aim for close to 4gig finished files)

---

### Post by sstusick on 2008-02-25
Well I did some further research here on the forums, and I've come to the conclusion that devede is the best I'm going to find, and the time it takes is about the same it takes everyone else, so I guess I'll have to deal with it.

---

### Post by halitech on 2008-02-25
there is another program called manDVD that I use as well but it is still about the same speed but it is good for when you have multiple files (like tv shows) and you want to put them on a single dvd with a menu. devede is about the best you will find for a gui application.

---

### Post by yabbadabbadont on 2008-02-25
There is a howto thread around here somewhere for tovid.  It has both command line tools and a gui (or two).  One of the options that you can set with tovid tells it to use ffmpeg for the conversion when possible.  This tends to speed things up considerably.  I found it reduced encode times by about a third.  Devede is using mencoder for the conversion, so it is really mencoder that is slow, not devede.  :)

---

