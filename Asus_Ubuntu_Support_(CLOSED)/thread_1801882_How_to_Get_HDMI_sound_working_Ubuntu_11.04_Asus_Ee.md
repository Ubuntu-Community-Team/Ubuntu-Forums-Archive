---
title: "How to: Get HDMI sound working Ubuntu 11.04 Asus EeeBox EB1501U"
date: 2011-07-11
forum: Asus Ubuntu Support (CLOSED)
---

### Post by FryinRyan on 2011-07-11
I just wanted to write this "how to" for my own memory and if anyone else is interested.  I installed
Ubuntu 11.04 Natty yesturday and everything worked great except HDMI sound *sigh*. I googled around
and found all the bits and pieces on how to do it scattred around the web so I thought I would place them all here in one post. 

1. Go to system preferences - > sound - > Hardware -> select "Digital stereo (HDMI) Output. 
Now any normal person would think that that would be enough right? WRONG! Wel, no sound yet, at least not for me. 
But I think you still have to do this first step.

2. Fire up ye old terminal! Write: > alsamixer hit that returnkey like you never hit it before and behold some alsamixer interface! For reasons only known to the higher powers of the universe
not all of the "S/PDIF":s are active. Using arrowkeys move to them and activate pressing the "M"-key. 
If I remember correctly my so called "S/PDIF D" was not active so I just activated that one. Press esc to
exit alsamixer.
Fantastic! Now there should be sound comming through the HDMI cable!:guitar:
3. If there is no sound when playing Flash videos, go back to terminal, write > sudo nano .asoundrc (dont forget the dot infront of asoundrc). Now put this info in that sucker:

> 
pcm.!default {
type hw
card 0
device 3
}
ctrl+o to save the file, ctrl+x to exit. Open Firefox and your favourite youtube video and you should have sound through HDMI. 

Hope this was usefull to someone, it sure was to me. :P

---

### Post by am bodach on 2011-10-05
Thanks FR. I've had the same issue with the Emachine ER1401. Followed steps 1 & 2 and bingo! Sound through the TV.

Cheers

Del

---

