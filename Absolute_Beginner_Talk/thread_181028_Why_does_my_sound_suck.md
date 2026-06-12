---
title: "Why does my sound suck?"
date: 2006-05-23
forum: Absolute Beginner Talk
---

### Post by youthforlinux on 2006-05-23
I installed all of the codecs so i can play mp3 etc.  But my sound sucks when i play my music.  I'm using Amarok.  Via Built in Sound Card.  Any suggestions?

---

### Post by Klaidas on 2006-05-23
What do you mean by sucks? No lound enough? Not enough bass? Anything else? :)

---

### Post by youthforlinux on 2006-05-23
Actually it sounds kinda robotic like and isn't pretty loud either.

---

### Post by Bazon on 2006-05-23
[QUOTE=youthforlinux] Via Built in Sound Card. [/QUOTE]You mean the Via AC97? Oh my god, that must be one of the worst cards for linux, there are many issues!

See this page e.g.:
[http://alsa.opensrc.org/via8233](http://alsa.opensrc.org/via8233)

For me, the only thing helped to get good, undistorted mp3 playback was installing the xmms crossfade plugin and set the sample rate to 48000Hz. (which is also suggested in the guide I linked before...)

I also filed a bug for that:
[https://launchpad.net/distros/ubuntu/+bug/43062](https://launchpad.net/distros/ubuntu/+bug/43062)
which is not yet confirmed... :wink:

but what I really suggest you is: Get another non-Via soundcard (even a cheap one!), you'll be much happier with that!

---

### Post by youthforlinux on 2006-05-23
ok ill try it out but i do have some older computer with different sound cards that i can use

---

