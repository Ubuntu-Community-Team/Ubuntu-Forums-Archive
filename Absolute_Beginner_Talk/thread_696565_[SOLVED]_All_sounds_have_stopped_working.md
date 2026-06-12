---
title: "[SOLVED] All sounds have stopped working"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by NEUR0M4NCER on 2008-02-14
I've been running Ubuntu for about six months, with no sound problems at all, worked perfectly with no setup. Yesterday sound just stopped working. All sounds (apart from PC Speaker beep). I've tried different speakers, so I know the issue's not there, and as far as I can tell audio set-up is so simple... well I just can't see what could have happened, aside from some sort of hardware failure (it's an on-board sound chip, so doesn't seem likely to me). Is there something glaringly obvious i'm missing (no, it's not on mute ;))? I've had a search through the forums, but there doesn't seem to be anything relevent.

Thanks in advance.

---

### Post by kesman on 2008-02-14
Check alsamixer in terminal and hit tab a few times to see all channels. If there's an M below the channel bar, that means the channel is muted. I had my PCM muted for some reason after some updates, and unmuting it with M did the trick.

---

### Post by NEUR0M4NCER on 2008-02-14
Perfect Kesman - that was exactly what it was. Thing is, i'd already been through all of the GUI sound settings, and that did nothing. Terminal wins again!

Thanks again, I was really worried I might have a hardware issue (old 'puter).

---

### Post by kesman on 2008-02-14
Glad I could help you out. Maybe mark the thread solved now?

---

### Post by indiana_crook on 2008-03-22
> **kesman said:**
> Check alsamixer in terminal and hit tab a few times to see all channels. If there's an M below the channel bar, that means the channel is muted. I had my PCM muted for some reason after some updates, and unmuting it with M did the trick.

My PCM wasn't muted, it was just turned all the way down for some odd reason.  U think 8.04 will be better about this kind of stuff???

---

