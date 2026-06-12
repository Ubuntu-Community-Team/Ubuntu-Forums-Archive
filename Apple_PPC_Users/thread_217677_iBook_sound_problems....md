---
title: "iBook sound problems... ????"
date: 2006-07-17
forum: Apple PPC Users
---

### Post by Da_Panther on 2006-07-17
Hey. I have a problem with my linux sound. it distorts alot, like when there are loud noises, they will be too loud, and softer noises will be too soft. And also, another glitch I found, say I'm in terminal, and I want to erase a line completely, I just keep backspace down until I reach the end of the line. If you keep it down to long, the machine beeps, right? well the first beep is always louder than the others. this is not normal is it? if it is, then its annoying!!!! 
thanks in advance for the help!
Swordfish

---

### Post by Da_Panther on 2006-07-17
By the way... iBook G4 1gb ram 1.33gHz

---

### Post by noahjb on 2006-08-27
I had the same problem with a 1.42gHz iBook g4. Go into terminal and type ```
 alsamixer 
``` Right arrow (there are more choices off of the screen) to  "DRC Rang" and increase it a bit. With music playing, fool around with some of the other settings. I have improved my sound quality a lot just by doing that. (It's still not perfect, but it's much better.)

---

