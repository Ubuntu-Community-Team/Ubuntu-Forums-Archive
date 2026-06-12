---
title: "PLaying Mp3's in exaile causes noise"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by Marianne_S on 2007-11-29
Whenever i try to play mp3's in exaile (haven't tried other fileformats) i get noises . What can cause this? And how can i fix it?

My music plays fine in Amarok, so this isnt a super urgent problem, but i'd rather play my music in Exaile. Plus it is fun to learn how things work.

---

### Post by Marianne_S on 2007-11-29
anyone?

---

### Post by Marianne_S on 2007-11-30
Might there be something i need to install? I have the gnome-media packages?

Or maybe i need to uninstall something? 

Am I the only one with this problem?

---

### Post by LowSky on 2007-11-30
what kind of noise?

what driver are you using for sound ALSA or OSS?

---

### Post by Marianne_S on 2007-11-30
alsa - couldnt make oss work (tried just now)

uhm, it is kinda statick screech noises that goes over the song - did that make any sense?

i tested some more and turns out i get the same noise if i use rythmbox - and if i try to burn cd's with serpentine

it sounds ok in gxine and xmms

those are the players i have

uhm - do you need more info ? i am not sure what is relevant

---

### Post by Marianne_S on 2007-11-30
oh and the noises arn't constant. i can play a song and it sounds ok (not perfect but ok) and then half a minute / one minute into the song the noises come - then its fine for a while, then the noise is back etc

---

### Post by LowSky on 2007-11-30
maybe this link will help

[https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/84774](https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/84774)

[https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)

---

### Post by Marianne_S on 2007-11-30
it worked!  -stupid me - i had searched for almost everything everywhere -cept using the word "crackling" - thank you so much for helping! :)

a nice start to my weekend

---

### Post by LowSky on 2007-11-30
welcome. funny thing was i didnt search for crakling... it was like 3 google pages deep when searching "MP3 Ubuntu Noise"

glad it helped

---

### Post by Marianne_S on 2007-11-30
ha don't i feel silly now - thank you anyways!

---

### Post by MikeJ112 on 2008-03-15
Hi im having the same problem as this, only mp3 playback works fine in Totem, just not in exaile

Any ideas?

---

### Post by MikeJ112 on 2008-03-15
no worry now, the latest version has fixed!

---

### Post by cristiantm on 2008-03-27
Well... 

:confused:

I looket the links, searched the forum, and my sound is still crackling. Where did you found the sollution???

---

### Post by Marianne_S on 2008-03-29
> **cristiantm said:**
> Well... 

:confused:

I looket the links, searched the forum, and my sound is still crackling. Where did you found the sollution???

just a thought are you using alsa? i tried switching to oss - and that worked too (why i do not know)

---

### Post by cristiantm on 2008-03-29
I am using alsa+pulseaudio.

I dont consider moving back to old OSS a sollution, maybe a workaround... ;)

---

### Post by Marianne_S on 2008-03-29
hehe exactly

---

