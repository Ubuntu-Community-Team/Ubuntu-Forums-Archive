---
title: "New to Linux and Ubuntu"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by Inkpot on 2006-12-18
Hi everyone,

I've managed to dual install Ubuntu and WinXP on the same machine with no mushroom clouds resulting! I do, however, have a bit of a problem that I haven't been able to find a solution for on these forums yet. When I try to listen to music via Amarok, Rhythmbox, or Caffeine, I hear nothing and yet I can hear system sounds, DVD's etc. Also, when I navigate to my WinXp partition and look in my "My Music" folder, I see nothing. I've used EasyUbuntu and AutoMatix to install any missing codecs, but still no sound from the music players. What am I missing/doing wrong? 

Thanks in advance for any tips!



Inkpot

---

### Post by BarfBag on 2006-12-18
Check the little volume icon next to the clock, for starters.

Maybe someone else could assist you in finding the volume controls.  I can't seem to remember where they are.

---

### Post by Inkpot on 2006-12-18
Nope, done that. Otherwise, I wouldn't be able to hear ANYTHING. :)


Inkpot

---

### Post by talbain on 2006-12-18
System -> Preferences -> Sound
and set all to ALSA

does it help?

---

### Post by WalmartSniperLX on 2006-12-18
Honestly, checking the little volume control and right clicking it, and messing with the preferences is all I can say :S You might have to select a different driver. Other than that your sound should work out of the box ](*,)  
Thats all I know ;)

EDIT: Oh yeah, ALSA is the driver you want selected

---

### Post by talbain on 2006-12-18
u can also right click the speaker icon and choose "Preferences" device and track to control, make it so it uses an ALSA device

---

### Post by Inkpot on 2006-12-18
Yeah, everything's set to ALSA....man, this has got me stumped.... :(


Inkpot

---

### Post by WalmartSniperLX on 2006-12-18
> **Inkpot said:**
> Yeah, everything's set to ALSA....man, this has got me stumped.... :(


Inkpot

Ok the last thing I can suggest is to go thru the list of devices in the preferences and make sure all (or obvious ones) of the audio is turned up. Maybe you have your CD rom (or something) stream muted ?

---

### Post by Inkpot on 2006-12-18
Ok...I am officially dumber than dirt.

There were several options that were muted that I didn't see earlier. Crisis averted! Thanks for all your help everyone!!


Inkpot

---

### Post by TooRight on 2006-12-18
Have you tried "alsamixer" in the terminal to bring up its GUI? Perhaps some of the volumes in there are muted (marked with MM).

***** lmaoo, nevermind, ya got it, lol :D

---

### Post by WalmartSniperLX on 2006-12-18
> **Inkpot said:**
> Ok...I am officially dumber than dirt.

There were several options that were muted that I didn't see earlier. Crisis averted! Thanks for all your help everyone!!


Inkpot

lol we all learn somehow and sometime in our life. Im glad you got it working :D

---

