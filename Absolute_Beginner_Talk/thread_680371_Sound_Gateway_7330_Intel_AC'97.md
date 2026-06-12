---
title: "Sound? Gateway 7330 Intel AC'97"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by ridgeback on 2008-01-27
I cannot, for the life of me, get my sound to work.

My onboard sound card is recognized.

Intel 82801DB AC'97 card
Gutsy Gibbon
Gateway 7330GZ

Any help, including a link to a good guide, would be much appreciated.

Thanks!!

Jerod

---

### Post by forrestcupp on 2008-01-28
If it is recognized, have you tried checking the volumes?  Right click the speaker icon by the clock and choose Open Volume Control.  Make sure the applicable volumes are turned up.  Or you could type ```
alsamixer
``` in a terminal and make sure the PCM volume is up. 

Also just make sure your speakers are plugged in to your sound card and into the wall if they need to be.  I know it's simple stuff, but you wouldn't believe how many times people miss the simple things because they are looking for a complex answer.

Edit:
If none of that is the problem, try [this thread](http://ubuntuforums.org/showthread.php?t=680960)

---

