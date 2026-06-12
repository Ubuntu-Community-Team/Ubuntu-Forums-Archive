---
title: "Help!"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by jasonchiu on 2007-06-24
hi i just currently switched over to ubuntu last night and i cant hear any sound when i play music .. and i have a SB LIVE and im just wondering whats the solution. please and thanks

---

### Post by EvilBro on 2007-06-24
Do you do hear a sound when it starts up? Or when you go to 'System->Preferences->Sound' and select 'Test'?

---

### Post by jasonchiu on 2007-06-24
nope, all i hear is like white sound. Like when you turn on your a channel that you dont have on tv.

---

### Post by ugm6hr on 2007-06-24
In Terminal:
```
alsamixer
```
And use "M" to mute/unmute (MM/OO respectively) and left/right & up/down to adjust settings.  Best to just unmute everything (OO) and maximise all volumes to see if that works.

On my laptop headphones are "front" speaker, and main speakers are "surround", which made the default setting silent without headphones.

---

