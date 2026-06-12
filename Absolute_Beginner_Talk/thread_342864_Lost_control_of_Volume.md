---
title: "Lost control of Volume"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by tknee on 2007-01-20
Hi

I have lost control of the volume of my sound card. I cannot control it fron the volume icon in the top panel of from my keyboard. I can control it from my speakers but the minimum volume is still quite loud!

CA0106 ALSA Mixer is my default sound card (it is actually a Sound Blaster Card). What should I do to taike back control. I have played around with the Preferences on the volume icon but with no luck.

Thanks for your help.

Terry

---

### Post by xpod on 2007-01-20
Try "alsamixer" in the terminal instead possibly?

---

### Post by tknee on 2007-01-20
You mean adjust the volume using Alsamixer in the terminal^ Sorry, but how can I do that?

Thanks

---

### Post by xpod on 2007-01-20
Just by typing "alsamixer" into the terminal which brings up......alsamixer contorls:D 
Then you can try adjust your volume much the same as you would have via the volume icon.

Not sure if it`ll make much difference if it`s not working via the volume icon though.
Check your sound settings via sys>prefs>sound too.

Cant really tell you much more than that other than searching for the "comprehensive sound thread"and seeing if that helps

---

### Post by burek on 2007-01-20
for the mega sound attack : 
(attention cuaation beware of these commands & danger for noobs )
> 
alsaconf
alsaconf
alsactl store

/etc/init.d/alsa reload

apt-get install aumix alsa
apt-get install aumix alsamixer

aumix  -d /dev/mixer  -v 100 -w 100 
aumix  -d /dev/mixer1  -v 100 -w 100 
aumix  -d /dev/mixer2  -v 100 -w 100 

apt-get install gnome-volume-control
alsamixer

---

### Post by tknee on 2007-01-21
HI

Just typing alsamixer in the terminal window and adjusting the volume using the tab and arrow keys worked perfectly. 

Thanks Guys

---

