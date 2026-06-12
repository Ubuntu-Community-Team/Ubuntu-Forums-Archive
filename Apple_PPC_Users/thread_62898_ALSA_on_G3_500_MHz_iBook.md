---
title: "ALSA on G3 500 MHz iBook?"
date: 2005-09-06
forum: Apple PPC Users
---

### Post by anechoic on 2005-09-06
has anyone been sucessful at getting ALSA drivers working on a G3 iBook?
I have tried with no luck whatsoever
when testing sound with the XMMS player I have Esound passing audio but not OSS or ALSA...
I'm running 5.0.4 with the latest kernel update 
thanks!
KIM

---

### Post by lixus on 2005-09-06
I just fixed my alsa  on a Titanium PowerBook G4 by disabling DRC (whatever DRC is)

1) amixer controls | grep DRC
  numid=8,iface=MIXER,name='DRC Range'
  numid=12,iface=MIXER,name='DRC Switch'


2) amixer cset numid=12 off
3) alsactl store 0

The other solution is not to use alsa at all but the OSS sound module
dmasound_pmac instead of snd-powermac.

good luck with ubuntu.

(i am personaly a bit disapointed from ubuntu
because currently some things are not working like pcmcia, sleeping ,
monitor mode for the airport card etc. Took me two days of reading to get alsa fixed. My debian 2.4.22 benh worked much better but I thought it was time 
to go for a 2.6 kernel, what ever i am just a slightly frustated guy ;-)

---

### Post by anechoic on 2005-09-07
thanks for this advice but it didn't work...also my OSS is hosed as well...any time I try to play a file via XMMS with the output set to OSS the app freezes and I have to force quit...and if I start XMMS again it doesn't work until I reboot the machine...
:(
anyone else know how to get ALSA working on a G3 iBook?

---

### Post by gumara on 2005-09-08
amixer cset numid=12 off

work with my ibook. thank you

---

