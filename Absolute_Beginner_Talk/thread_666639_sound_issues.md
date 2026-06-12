---
title: "sound issues"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by alan_18 on 2008-01-13
I'm completely new to Ubuntu, just installed 7.10 Gutsy on my Packard Bell Easynote today.  I'm having a few problems though.

First - I have no sounds of any kind.  I don't know if there are drivers I need to install or how to check any of this stuff.  As I said, complete Ubuntu n00b.

Second - Perhaps even more annoying than the sound problem is being locked into 800x600 resolution.  I have an SiS Mirage 3 integrated graphics card, so I don't know if there are drivers that work on Linux or what I have to do to get things working properly.

Any help at all would be appreciated; I really don't want to go back to Vista.

---

### Post by nikoPSK on 2008-01-13
does this show up your card (if you do have a card)?
```

asoundconf list
```

If so, then set the one you want like this

asoundconf set-default-card xxx

where xxx is the name of the card. You might also need to unmute some channels in alsamixer

```
alsamixer
```

Regards,
nikoPSK

---

### Post by alan_18 on 2008-01-14
Didn't work.  It says my sound card is an SIS966 though.  Is it possible that there's a problem with my Alsa or something like that?  I don't even get system beeps right now.

---

### Post by nikoPSK on 2008-01-14
> **alan_18 said:**
> Didn't work. It says my sound card is an SIS966 though. Is it possible that there's a problem with my Alsa or something like that? I don't even get system beeps right now.
 
it didn't work? What did you do, give me the exact steps, you might needed to have unmuted the card in alsamixer.
 
nikoPSK

---

### Post by alan_18 on 2008-01-14
I used asoundconf list to find out what card I have, and then I set it as default.  I checked Alsamixer and I don't think any channels are muted.

---

### Post by nikoPSK on 2008-01-14
hrm, can I ahve screenshots please? (of alsamixer?)
 
nikoPSK

---

### Post by alan_18 on 2008-01-14
There's a screenshot of my alsamixer [here.]("http://i19.tinypic.com/8f5fwbl.png")  Sorry it took so long.

---

### Post by snkiz on 2008-01-14
I couldn't see too well in the screen shot but from what i can see ASLA can see your card so max out all the outputs in ASLA and check your conections some times the simple things are the hardest to spot

---

### Post by alan_18 on 2008-01-14
What do you mean check my connections?  It's an SIS966 sound card on my laptop.

---

### Post by nikoPSK on 2008-01-14
> **alan_18 said:**
> There's a screenshot of my alsamixer [here.]("http://i19.tinypic.com/8f5fwbl.png")  Sorry it took so long.

well, you set the card right, you might need to mute some channels too. I muted my onboard.

nikoPSK

---

### Post by alan_18 on 2008-01-15
I double clicked on my sound icon, and under the "Switches" tab there doesn't seem to be a checkbox for Speakers, only Headphones.  Does this maybe have anything to do with things?

---

