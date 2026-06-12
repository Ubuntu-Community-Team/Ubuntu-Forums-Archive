---
title: "Defualt Sound Card Problem"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by gentix on 2008-04-01
I have two sound cards on my computer.  One (called nForce2) is integrated to my MB, and therefore isn't very good, so I use my other (Audigy).  When I first installed 7.04, I had to switch my default card from nForce2 to Audigy using the asoundconf utility.

Now for some reason (I now have 7.10), frequently my computer starts up with the nForce2 card as default.  I can simply use asoundconf to change the default card, but this requires a restart, and it takes time.  Does anyone know know a more permanent fix to this problem?

Much thanks.

---

### Post by bumanie on 2008-04-01
Sometimes it is possible to disable onboard cards from within the bios controls. It depends on your motherboard manufacturer and user changeable bios oprions, but it's worth a look.

---

### Post by taavikko on 2008-04-01
> **gentix said:**
> 
Now for some reason (I now have 7.10), frequently my computer starts up with the nForce2 card as default.  I can simply use asoundconf to change the default card, but this requires a restart, and it takes time.  Does anyone know know a more permanent fix to this problem?


```
asoundconf list
```
and
```
asoundconf set-default-card XXX
```
should make the change permanently.

But I agree, disabling the onboard soundcard is the easiest way.

---

### Post by gentix on 2008-04-01
Yes, I've actually tried to disable the on board sound card in BIOS before, and it doesn't seem to be possible.  My guess is that there might be a jumper on the MB itself (is that possible?)... I might be able to find that if a softer solution doesn't present itself.

Unfortunately my problem is that the command "asoundconf set-default-card" doesn't seem to be working in a permanent fashion.  I can't imagine why that would be though...

---

### Post by stchman on 2008-04-01
> **gentix said:**
> I have two sound cards on my computer.  One (called nForce2) is integrated to my MB, and therefore isn't very good, so I use my other (Audigy).  When I first installed 7.04, I had to switch my default card from nForce2 to Audigy using the asoundconf utility.

Now for some reason (I now have 7.10), frequently my computer starts up with the nForce2 card as default.  I can simply use asoundconf to change the default card, but this requires a restart, and it takes time.  Does anyone know know a more permanent fix to this problem?

Much thanks.

My VIA based mobo has a VT8237 AC97 sound card that I disabled in my BIOS.  For some reason Ubuntu still sees this sound card.  I used the asoundconf and it worked well.

---

