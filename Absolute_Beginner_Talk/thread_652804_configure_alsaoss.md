---
title: "configure alsa/oss"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by darkline on 2007-12-29
Hi, at the moment I dont get sound from things like firefox/totem and some other programs. I believe it is something to do with alsa and oss not being configured to use my soundcard properly. I have checked on System > preferences > sound, and when testing autodetect, alsa and oss i do not geget any sound. What i use is cmi8738 - my sound card. 
how do i set alsa and oss to use my soundcard by default ?? I have  the drivers for it on a disc and it is supported by alsa.

Thanks

---

### Post by TidusBlade on 2007-12-29
I didnt have sound, so I removed OSS and installed ALSA, and it detected my sound card.
Try running this command?
```
sudo apt-get install alsa-base alsa-oss alsa-utils
```
Should install ALSA, the required package to emulate OSS and the "alsamixergui"
Good luck ;) Those sound things are really annoying :p

---

### Post by darkline on 2007-12-29
I have now tried that but unfortuanatly not luck, I am getting sound through my soundcard, but only when i tell each app to use my soundcard not alsa or oss - what i need to do is to ::-
(a) tell all apps to use my soundcar (but i dont know how to do that with things like flash)
or 
(b) get alsa and oss to use my soundcard by default

i think thats what i need anyway - as when i test them they say testing but no sound comes.

ty

---

### Post by ugm6hr on 2007-12-29
Do you get any sound from Ubuntu at all?  Or is it just specific programs?

If the former - it might be just an alsa volume issue:
[http://ubuntuforums.org/showpost.php?p=4009147&postcount=5](http://ubuntuforums.org/showpost.php?p=4009147&postcount=5)

---

### Post by darkline on 2007-12-30
The only program i can get sound on is VLC, however  the only way i get sound from it is by telling it to use my soundcard in vlc's preferences > audio > output modules > alsa.
No other programs give me sound. 
I have put the volumes up to full on all channels, but i did notice that at the top it said "Card: SiS SI7012" which is not my sound card, it is the onboard sound on my motherboard - is this the propblem then?, if so how can i change it?

---

### Post by darkline on 2007-12-31
bump.

---

