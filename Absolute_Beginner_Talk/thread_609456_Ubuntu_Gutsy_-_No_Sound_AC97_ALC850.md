---
title: "Ubuntu Gutsy - No Sound AC97 ALC850"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by Berserk87 on 2007-11-11
im completely new to ubuntu, this is the first day ive had it installed.

ive got all the basics that i wanted working exept for.... SOUND the most important thing...

i downloaded the realtek drivers and installed those and my sound still dosnt work, when i checked it  all it said was "FATAL : module ac97 not found"

:S

ive browsed the other posts on the forums and didnt find a solution that worked for me.

---

### Post by Partyboi2 on 2007-11-11
```
aplay -l
```Does the result u get list all the soundcards that are installed? Or do you get a error message? If it lists your soundcard you may just need to unmute it.

```
lspci -v
```What does this command return? Ubuntu may have detected your soundcard but the drivers may not be installed/working.

---

### Post by flosoft on 2008-02-03
I just get no soundcard found. Same soundcard :S

I tried to compile the driver from realtek, but I get missing alsaconf or so?

---

