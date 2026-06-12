---
title: "Can't play sound."
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by ChunkOFunk on 2007-11-05
I'm sure this gets asked a lot around here, but I'm trying my best to search through forums and can't find anything exactly pertaining to my situation. 

So, I installed my Realtek HD Audio Manager Codecs/Drivers *Not sure witch* which is what I used on my vista, and everything was peachy, so, I tried doing the same with the Linux drivers, but, near as I can tell, they don't quite install. Anyway, I can hear sound when I play it in the Prefrences "Test Sound" thing, it's just a monotone, but I can't hear sound anywhere else. Anybody got any ideas on why that's the only place I can hear anything?

UPDATE: The only place I can't play sound is in Firefox. 
:/

---

### Post by magli on 2007-11-05
oops

---

### Post by magli on 2007-11-05
What other programs are you using which you are not getting sound in?

Try opening gnome-volume-control by right clicking on the speaker icon in the top-left of the screen, and selecting "Open Volume Control". Make sure nothing is muted.

---

### Post by ChunkOFunk on 2007-11-05
So far I've only tried Firefox and Pidgin.Scratch that, Pidgin works... >.>

---

### Post by Seti on 2007-11-05
You tried to INSTALL drivers for your soundcard like in Vista?? That's unusual, with ubuntu you shouldn't have to go installing drivers for your soundcard, afaik.
Now if you can hear the test bell it seems something is working, so I would suggest opening a terminal and typing:```
alsamixer
```

You should get a colourful mixer that will enable you to control various sound channels. The controls are pretty self-explanatory, just see if something isn't muted for some reason.

---

### Post by ChunkOFunk on 2007-11-05
Oops

---

### Post by magli on 2007-11-05
What type of web pages are you trying to play sound on? I do not think firefox itself plays sounds.. I think it uses plugins, like flash for places like youtube.

---

### Post by ChunkOFunk on 2007-11-05
Yeah, I've been trying to play all sorts of media, I'll check my plugins I guess
>_>

---

