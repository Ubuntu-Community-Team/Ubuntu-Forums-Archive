---
title: "Sound default"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by DrkVagrant on 2008-04-15
So, I just installed the KDE desktop for Ubuntu.. and I was messing w/ the mixer. Apparently i messed something up because now i have no sound. My card is fine and i get sound on XP (other partition). I can't seem to figure out what i did. (wasn't really paying attention either ><) Is there a way to set the mixer to its defaults? It was working just fine till i gone and messed it up too.

---

### Post by spiderbatdad on 2008-04-15
This may work...assuming your volume controls are up, but sound is not playing:
```
asoundconf list
```

```
asoundconf set-default-card Parameter
```
Where Parameter is the value returned from the first command.
You will need to reboot.

---

### Post by DrkVagrant on 2008-04-15
Thx alot that worked great. Woot!

---

