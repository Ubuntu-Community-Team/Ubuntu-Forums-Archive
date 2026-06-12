---
title: "[SOLVED] Silence is Golden...but not much fun."
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by DutyDuty on 2007-10-21
I have no sound, ever since I upgraded to 7.10. 

According to lspci, I have Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)

Everything else is great. How are you?:guitar:

Help?

Edit: This Thread saved my life: [http://ubuntuforums.org/showthread.php?t=416207](http://ubuntuforums.org/showthread.php?t=416207)

Well, not my life, but sound anyway. My hero.

---

### Post by DutyDuty on 2007-10-21
Alsamixer has a master volume of 00 and I can't change it...

---

### Post by kellemes on 2007-10-21
Have you tried running alsaconf?
And see if alsmixer isn't muting channels..

---

### Post by Hobo Joe on 2007-10-21
You need to tell it what card to use by default

```

sudo asoundconf list

```
That will show you any sound card(s) that are on your computer, for example, for me, I had two, one was 'nVidia', then other was 'Live', so to make the computer use the 'Live' card, I typed this command:
```

sudo asoundconf set-default-card Live

```
Depending on the name of your card, just replace Live.

---

### Post by DutyDuty on 2007-10-21
Alsamixer has no muted channels, and alsaconf does nothing. Alsactl does something, but I don't know what.

---

### Post by DutyDuty on 2007-10-21
I already had replaced my sound card with asoundthing

The only one was called SB.

---

### Post by DutyDuty on 2007-10-21
[http://ubuntuforums.org/showthread.php?t=416207](http://ubuntuforums.org/showthread.php?t=416207) solved!

---

