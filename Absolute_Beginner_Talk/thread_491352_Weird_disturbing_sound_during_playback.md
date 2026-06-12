---
title: "Weird disturbing sound during playback"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by bartkl on 2007-07-03
Hi,

When I playback MP3's using Totem, Exaile or Listen, I hear this weird 'eletronic breeze' at a low but very audible volume level. 
What could possibly be the case?

I'm using an onboard soundcard and haven't installed different drivers from what Ubuntu had used from the start.

Thanks.

---

### Post by Jacemg on 2007-07-03
is this only with totem? or is all sound played back with the extra noise? (i.e. games or movies)

---

### Post by bartkl on 2007-07-03
I checked a movie in Xine.
There the sound also is very deformed.

---

### Post by forestpixie on 2007-07-03
Just a maybe - I read a thread a while back where someone had odd noises - it turned out to be feedback from the mic

---

### Post by bartkl on 2007-07-03
> **forestpixie said:**
> Just a maybe - I read a thread a while back where someone had odd noises - it turned out to be feedback from the mic

No mics here, but you have inspired me to at least check some channel settings in alsamixer.
Are there more suited places than alsamixer to check for sound settings?

And ehm.. Is it possible to find suited audio drivers for onboard chips?

---

### Post by Jacemg on 2007-07-03
> **bartkl said:**
> No mics here, but you have inspired me to at least check some channel settings in alsamixer.
Are there more suited places than alsamixer to check for sound settings?

And ehm.. Is it possible to find suited audio drivers for onboard chips?

Happen to use AC '97 onboard chip?

---

### Post by Redeyes_Gambit on 2007-07-03
You might have your PCM (Pulse Code Modulation) set too high. Right-click on your speaker icon on the menu bar and click the "open volume control" option. Now, all you have to do is adjust the PCM sliders and you're set!

...Unless it's some other problem ;-)

---

### Post by bartkl on 2007-07-03
> **Redeyes_Gambit said:**
> You might have your PCM (Pulse Code Modulation) set too high. Right-click on your speaker icon on the menu bar and click the "open volume control" option. Now, all you have to do is adjust the PCM sliders and you're set!

...Unless it's some other problem ;-)

Funny... I tried choosing a different Device in there , no changes. Then changed back and had low volume. Maximized level of PCM and now it seems to be fine :S

Well... If anything weird happens again I'll let you guys know. Thanks!

---

### Post by bartkl on 2007-07-05
I had to totally reinstall Ubuntu and now the exact problem is back :(
I have upgraded alsa to the newest version, but that doesn't do the trick.

The problem is terrible, I would really appreciate help. My earlier lucky trick doesn't work this time.

---

### Post by moredhel on 2007-07-05
I had the same problem. I resolved it by simply not having any volume on max. As in volume on your pc, not the actualy speakers. I have it at about 85% on everything, then just turn the speakers up. Try it :D

(remember to do gnome and the individual programs volumes.)

EDIT: Getting a cheap soundcard from creative meant it could go to 100% BTW

---

### Post by bartkl on 2007-07-05
Thanks for your reaction, but if I lower the volume level to about 50% it disappears, but even on max of my speaker volume my sounds volume  level is very low.

Btw. I can switch from devices Realtek ACL885 (I actually have 889 btw) and HDA-Intel.
Both it's volume sliders make audible differences! Are they in use simultanuously?


[edit]  It works now. Had to install gstreamer-0.8-mad    . Already had gstreamer 0.10 but apparently that didn't do. Thanks! [/edit]

---

### Post by moredhel on 2007-07-05
Perhaps try putting the individual applications volume high and gnome's low? And perhaps you need louder speakers? >=)

---

