---
title: "microphone does not record"
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by svenno on 2006-06-08
Hi,
my problem is that since i installed ubuntu my microphone does not work at all.
when i make the settings i think the are right, i hear my breathing etc. immidiately, but although i cannot record something. 
i am an absolut linux newb, but i first installed suse linux and there (with is guess the same settings) the microphone worked fine.   :-k 
(sry 4 my english :>)

---

### Post by glesik on 2006-06-08
Try using *alsamixer* (in console) to set up your sound settings. Probably input device is set to "line in" or something else, not "mic". It can be also muted or have zero volume. Playback/capture is switched with Tab, mute with "m" and volume with "up" and "down".

---

