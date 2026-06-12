---
title: "[SOLVED] No sound HP laptop"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by lover_of_sc on 2008-03-14
I think I may have filled this forum up by myself by now.

I have a problem with my sound, I have read a few treads, downloaded some ALSA drivers. Tried to follow the manual of how to install it but it does not work. have anyone got instructions for getting them to work? Many thx. Anders

---

### Post by spiderbatdad on 2008-03-14
Have you tried the workarounds in this wiki?[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

What have you tried?
Is your sound card detected? You would know by right clicking volume control>>open volume control. Does alsamixer open, or does it say no sound card detected?

---

### Post by lover_of_sc on 2008-03-14
Hmmm good question, when I try to open the volume control, I get an error message saying: No volume control Gstreamer plugins and or devices found.

Dont know if I installed the alsa drivers correctly.

---

### Post by kwacka on 2008-03-14
For some reason the default setting is for 'external amp' - I had big problems before I realised this, and it didn't seem to appear in any of the docs.

Install something like gnome-alsamixer and ensure that the external amplifier box is clear.

---

### Post by lover_of_sc on 2008-03-14
I have checked and I have no soundcard detected...

---

### Post by superprash2003 on 2008-03-14
hope this helps [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

### Post by lover_of_sc on 2008-03-15
Ended up reinstalling entire ubuntu - worked like a charm. :-) Thx for your help anyway.

---

