---
title: "Macbook sound quality - STATIC"
date: 2007-08-15
forum: Apple Intel Users
---

### Post by davidsiegel on 2007-08-15
Playing CDs, mp3s, FLAC files, etc - any audio output - on Feisty produces static in the left channel only! This is crazy and bugging me so much. I've played with levels, different headsets and speakers, etc., but I always get this static in the left channel. Do any other Macbook users notice this? How can I fix it? Is it a problem with Alsa? Everything sounds peachy when booted in OS X.

---

### Post by cyberdork33 on 2007-08-15
I believe there were some other posts about static in the forum, but I can't seem to find them now. I am going to guess it is an alsa issue.

---

### Post by davidsiegel on 2007-08-15
cyberdork33, thank you for your response but I've already searched the forums and I've already guessed this is an alsa issue. I really don't mean to offend, but responses for the sake of responding only make threads that would otherwise be flagged as unanswered seem resolved to the casual peruser.

---

### Post by cyberdork33 on 2007-08-15
> **davidsiegel said:**
> cyberdork33, thank you for your response but I've already searched the forums and I've already guessed this is an alsa issue. I really don't mean to offend, but responses for the sake of responding only make threads that would otherwise be flagged as unanswered seem resolved to the casual peruser.

You asked whether it was an ALSA issue, I responded to your question. I was going to link to the thread where this was discussed (and if I remember correctly, partially resolved) but I could not find it. I am still looking for it. Most of the remaining audio issues remaining are dealing with Mac Pro.

EDIT: I don't know if 'distortion' is the same as 'static' in this regard, but it is the same speaker:
[http://ubuntuforums.org/showthread.php?t=489700](http://ubuntuforums.org/showthread.php?t=489700)
[http://ubuntuforums.org/showthread.php?t=371047](http://ubuntuforums.org/showthread.php?t=371047)

This one mentioned some static, but I don't think it is your problem. Here for completeness:
[http://ubuntuforums.org/showthread.php?t=376246](http://ubuntuforums.org/showthread.php?t=376246)

Can you say what the levels are set to in alsamixer? I have noticed on other cards, that having a certain (uneeded) level up can cause static, usually a digital output.

---

### Post by benanzo on 2007-08-16
I have a first gen MacBook and have never experienced this problem.  Does it happen from a fresh Feisty install?  Or is this something that has happened since installing.  Audio output (speakers,headphones) work great out of the box for me, but I have heard of others having a similar problem.  Just speculating, but I wonder if it has something to do with the audio levels set in OS X before reboot?  For instance, if you turn the audio volume all the way down or mute in OS X before rebooting you won't hear the chime sound when the machine turns on.  That leads me to wonder if there's a firmware bit that gets set that could be conflicting with ALSA.  I don't dual boot, so I can't test this myself.  (That would also explain why I've never had any problems(?))

---

### Post by ronocdh on 2007-08-18
Cyberdork's posts are excellent and I think they'll solve the problem nicely. Please post back with more explicit details if they don't, but this has indeed, as Cyberdork noted, popped up a lot here, and I think the fixes documented here should serve you well. Let us know if they don't!

---

### Post by davidsiegel on 2007-08-18
Yes, Cyberdork's post was very helpful but there are just too many inconsistencies and variables pertaining to my problem that I'm having a tough time finding a solution. Sometimes I have static, sometimes I don't - the best solutions seem to be reloading the snd_hda_intel module and restarting the alsa deamon.

Cyberdork, my alsamixer levels are all 100, but I've tried many combinations of levels looking for sweet spots and I get static no matter what.

---

### Post by bonestonne on 2007-08-19
i suggest [if possible] changing power settings and see if if that helps. i've seen power management cause playback issues with laptops before...its worth trying, its not OS specific or even hardware specific.

---

### Post by russo.mic on 2007-08-21
I've found that I sometimes get the static thing if the MBP starts with the sound muted.  i've noticed that as long as I don't shut it down muted, it isn't an issue.  see if you find that as well...

---

