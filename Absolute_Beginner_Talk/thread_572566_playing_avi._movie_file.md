---
title: "playing avi. movie file"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by abu-fatu on 2007-10-10
i installed gutsy beta on a amd 950mhz machine 256ram 32 ram videocard.
when itry to play a avi file movie i get this. tried it on vlc, movieplayer, gzineplayern  but the movie will not play.

---

### Post by Joeb454 on 2007-10-10
do you have the xine extra plugins and such?

should work if you have xine and xine extra plugins installed, definitely with ubuntu restricted extras - I have all 3 and haven't yet come into contact with an avi file I can't play

---

### Post by RomeReactor on 2007-10-10
Hi. I've had that happen to me every now and then with Gutsy; I have the same set of gstreamer libraries as in previous versions, and only in Gutsy have I encountered this problem. Disabling desktop effects doesn't correct the issue, so at least it's not Fusion. You might want to try a restart--that usually solves it for me--but I couldn't say what's causing it. You also might want to check the Xorg log (I forget to do that when it happens):
```
cat /var/log/Xorg.0.log
```

Or check the system log (System->Administration->System Log).

---

