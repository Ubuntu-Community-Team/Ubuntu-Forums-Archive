---
title: "Medibuntu Amarok"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by Want A Pie on 2007-12-14
Hi, I have been told that to play mp3's, I need to download MediBuntu Amarok.
I searched the MediBuntu site, but found no downloads.
If someone could direct me to the site, it would be appreciated :D

---

### Post by FuturePilot on 2007-12-14
See here for installing codecs
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")
You also might need w32codecs. For that see here
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")
```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```
```
sudo apt-get install w32codecs
```

---

### Post by Want A Pie on 2007-12-14
thanks, only problem is, my sound isn't working...

---

### Post by aquavitae on 2007-12-14
I've got mp3s working in amarok without using anything from the medibuntu site. Make sure you've got the universe repository active (I think - but it might be multiverse that you need, I can't remember offhand) and install the libmad package.  IIRC this is all you need.  Not at my ubuntu pc right now so I can't check, but if that doesn't work do a search in synaptic for mp3 and install anything that looks likely - a bit clumsy, I know, but you can go and selectively remove the unused libs later if you want. In case it helps, amarok uses the xine engine (package is libxine) so if you see something that adds mp3 support to xine its probably it.  But try libmad first, I'm pretty sure thats the one you need.

---

