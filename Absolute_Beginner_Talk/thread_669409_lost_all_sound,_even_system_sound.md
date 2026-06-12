---
title: "lost all sound, even system sound"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by arnicainthemembrane on 2008-01-16
I think this is a hardware problem because my IBM Thinkpad T40 won't make any sounds at all, not at startup, not when I unplug it, nothing. I put my computer (Gutsy) on hibernate then closed the lid and went to bed. Suddenly there was a loud feedback sounding noise coming from the computer. I opened the lid, and the sound stopped. I closed the lid and went to sleep. I wake up this morning to discover that I don't have any sound at all! I've put this problem out to the thinkpad forum, but I'm curious if there's some way I can troubleshoot the problem through gutsy.

---

### Post by rexxxlo on 2008-01-18
this probably isn't it but try 

system>preferences>sound

and try alsa in the drop down menus and you can test them there too

---

### Post by x02flash on 2008-01-18
Run alsamixer in a terminal or double click the speaker in the upper toolbar and make sure your PCM value is on, or turn it up more.  That's what was screwing my computer up the other day

---

### Post by TheMemphisExperience on 2008-01-18
PCM volume does nothing for my Acer. I had to go into the alsamixer right click drop down menu->  volume control-> edit. There are some radio buttons there and I selected surround in addition to the ones already there. I then went back to volume controls, unmuted everything , and cranked it up.

For better or for worse(worse) I also opened up a terminal with alsamixer and crnak everything up as high as it would go.....including the microphone. So I heard a wonderful piercing screech as music played softly at max volume.

Maybe you did succeed in killing you speakers, maybe the problem is fixable without replacing the hardware. Good luck.

---

