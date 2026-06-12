---
title: "Sound Problems - edgy"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by angelsneverdie on 2006-11-14
I upgraded to edgy eft and everything was working fine.  But all of a sudden, I'm having some weird sound problems.  If I play an avi file (like of a tv show or something) it goes fine except i can't hear the dialogue.  The background music comes out fine, just no words.  I tried listening to some .mp3 s and similar problem.  for instance the song 'sorry mrs. jackson' by outkast - the only lyrics i can hear is the chorus.  

Also, on a side note, it seems that the sound has always been 'grainy' since i switched to ubuntu.  It seems like in windows the sound quality was a lot better.  What can i do?  Please note that i know jack about linux, i'm trying to learn but am still a beginner . . . (i built comp myself but don't remember what kind of soundcard i bought and have no idea how to find out in ubuntu).  

any help (in lay-man's terms) would be greatly appreciated.

Thanks,
Mitchell

---

### Post by ReaderRat on 2006-11-14
Please run this in the Terminal (Applications>>Accessories>>Terminal):
```
cat /proc/asound/cards
```
to find out something about your sound card

---

### Post by justifier on 2006-11-14
maybe you have messed about with the equiliser by accident

---

