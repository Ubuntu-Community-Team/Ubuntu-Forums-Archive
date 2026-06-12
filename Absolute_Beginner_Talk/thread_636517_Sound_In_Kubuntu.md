---
title: "Sound In Kubuntu"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by jonward690 on 2007-12-09
I am so tired of this.Ok on my kubuntu system the sounds volume does not stay the same.I installed recompiled and went through the hell of instaling the alsa driver and yes it fixed my problem but it just started back.It is like it is some sort of runtime error or something.Oh yea and my alsa driver is hda-intel if you need to no that.I am so tired of this crap.

---

### Post by nikoPSK on 2007-12-09
just a guess but it worked with my audigy card:

```
asoundconf set-default-card had-intel
```

should work. If it doesn't do this:

```
asoundconf list
```

and give me the output.

---

### Post by jonward690 on 2007-12-09
Yea I did but it is still doing that thing.Ok the sound plays properly but it will just get real soft for no reason.

---

### Post by jonward690 on 2007-12-09
Oh yea here is the output 
```
jon@jon-desktop:~$ asoundconf list
Names of available sound cards:
Intel

```

---

### Post by nikoPSK on 2007-12-09
then do this:

```
asoundconf set-default-card Intel
```

then unmute the card in alsamixer, you might need to play with different channels as well. just start an mp3 then work on alsamixer, when you can hear it, your good;).

to open alsamixer:
```
alsamixer
```

---

### Post by jonward690 on 2007-12-09
I already set Intel as my default card.But I will try messing with the alsa mixer and see what I can do but I donno what it is.

---

