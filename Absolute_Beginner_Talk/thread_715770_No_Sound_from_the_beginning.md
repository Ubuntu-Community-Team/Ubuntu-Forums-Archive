---
title: "No Sound from the beginning"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by sarah.love on 2008-03-05
I've just uploaded ubuntu 7.10 onto my dell vostro 1400. I have a HDA Intel sound card, which shows as working properly. I've checked every option to see whether it might be muted. nothing is. 
Please please can somebody point me in the right direction

---

### Post by buckeyered80 on 2008-03-05
Are you able to see the exact specs of your card in the hardware info?  An HDA Intel is probably a high definition onboard audio card.  Make sure your speakers are plugged into the green port of course.  Make sure nothing is muted and master volume is turned up.  If it still does not work, you may have a driver issue, in which there are a few guides posted in the forums on troubleshooting those hda intel cards.

---

### Post by mormor on 2008-03-05
I am guessing you have a realtek alc268 card, if you do this might be of interest:

[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/]("http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/")

Just scroll down a bit, follow the guide, and upgrade your alsa-drivers.

Worked like a charm on my acer 6291 travelmate.

---

### Post by wheredidrealitygo on 2008-03-05
try installing the linux-backports-modules package for your particular kernel if you haven't already.

---

