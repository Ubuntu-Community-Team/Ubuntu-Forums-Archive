---
title: "audigy soundcard no longer working after update"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by toastysquirrel on 2008-01-23
I ran "sudo apt-get update" on my system yesterday and ever since my I've simply lost all audio on my systerm.  I don't get any messages or errors (to my knowledge), I simply don't get any sound :(  I'm running Gutsy (and always have been), but yesterday was the first time I ran the auto-update.  When I play music, the file loads up (in Banshee) and it plays... just without any sound.

I have a Creative Labs Audigy Gamer 1 soundcard (I think it's #1... it's like the first Audigy Gamer that came out 5+ years ago).

---

### Post by toastysquirrel on 2008-01-24
Bump...


[SIZE="1"]Because I miss my music[/SIZE]

---

### Post by forestpixie on 2008-01-24
I would first check that all the levels are ok - alsamixer, if the soundcard has any switches, dbl click vol icon - make sure thats ok

i would then go and check what got updated - synaptic - history and see if anyone else has had similar problems today/yesterday

---

### Post by toastysquirrel on 2008-01-24
Oddly enough the system just sort of fixed itself.  I rebooted into XP, did a few things, rebooted back into Ubuntu, and suddenly the sound was there.  The desktop theme was screwed up for some reason, so I rebooted again back into Ubuntu and everything's been fine.  Very strange.  FYI, all the levels in Alsamixer were good.

Well, whatever it was <shrug> But thanks a ton for the suggestions FP :)

---

### Post by stchman on 2008-01-24
> **toastysquirrel said:**
> I ran "sudo apt-get update" on my system yesterday and ever since my I've simply lost all audio on my systerm.  I don't get any messages or errors (to my knowledge), I simply don't get any sound :(  I'm running Gutsy (and always have been), but yesterday was the first time I ran the auto-update.  When I play music, the file loads up (in Banshee) and it plays... just without any sound.

I have a Creative Labs Audigy Gamer 1 soundcard (I think it's #1... it's like the first Audigy Gamer that came out 5+ years ago).

My Audigy 2 did something similar.  Turns out the PCM slider in Gnome was turned WAY down.

---

### Post by toastysquirrel on 2008-01-24
Strange.... unforunately I spoke too soon.  My system crashed (Banshee was playing a CD and the Add/Remove program menu was open) while I stepped away from my system for five minutes.  When I came back to it the track was stuck, the system unresponsive, and the HDD light was lit.  So I did a hard reboot.  When it loaded back up the sound was gone.  According to alsamixer, the card is now set to "ALi M5455" and I'm not sure how to change it.  Double clicking the speaker icon in the panel shows everything set to the Audigy.

:confused:

**[edit]** - Rebooting *again* seems to have set everything right... for now.  So right now I guess I'm looking for ways to demystify what's been happening.  With Windows there was the Device Manager that displayed all the installed hardware and if it was running.  What does Ubuntu have that does something similar?  I guess what would also help would be where can I go to figure out what caused the system to lock up in the first place?  Is there a place?

---

