---
title: "Quirky sound!"
date: 2006-05-14
forum: Absolute Beginner Talk
---

### Post by shurguywutt on 2006-05-14
I have one of the dreaded Soundblaster Live 24 bit sound cards.  I have been messing around with this thing for about a week and I almost feel as if I have written the drivers myself.  I have finally gotten it to work but it is being really quirky and strange.  First, at the ubuntu login screen, I always hear the drums over the speakers.  Next I get to the desktop and don't hear any sound.  So I go System>>>Preferences>>>Sound and I change the sound from "CA0106" to "Intel ICH5" and plug the speakers into the motherboard.  I hear sound.  I have a splitter hooked up to my soundcard my headphones and speakers plug into it.  Both are plugged into the soundcard, I only hear sound out of the headphones! So I pull the speakers out and stick them into the motherboard, then back into the soundcard...  and wtf sound starts coming out...  Does anyone have any idea what is going on or is my computer just posessed and I should just give up all hope for a normally operating sound system? :-k   Thanks.

---

### Post by therunnyman on 2006-05-14
[QUOTE=shurguywutt]I have one of the dreaded Soundblaster Live 24 bit sound cards.  I have been messing around with this thing for about a week and I almost feel as if I have written the drivers myself.  I have finally gotten it to work but it is being really quirky and strange.  First, at the ubuntu login screen, I always hear the drums over the speakers.  Next I get to the desktop and don't hear any sound.  So I go System>>>Preferences>>>Sound and I change the sound from "CA0106" to "Intel ICH5" and plug the speakers into the motherboard.  I hear sound.  I have a splitter hooked up to my soundcard my headphones and speakers plug into it.  Both are plugged into the soundcard, I only hear sound out of the headphones! So I pull the speakers out and stick them into the motherboard, then back into the soundcard...  and wtf sound starts coming out...  Does anyone have any idea what is going on or is my computer just posessed and I should just give up all hope for a normally operating sound system? :-k   Thanks.[/QUOTE]


Strange rig.  Most powered speakers have a headphone jack anymore; yours don't?

I guess for a suggestion, I'd start with plugging your speakers into the soundcard, and plugging your headphones into your mainboard (I'm assuming from your post you have two output devices, the card and the onboard sound).  When you want to listen through speakers, make a quick software change, selecting the SB as your output device, and when you want to go headphone, make that same software change, only this time select the onboard device.  You can do this in a number of ways: right-click the little speaker icon next to the time, hit file-->change device, get into Volume Control under applications (apps-->sound&video-->volume control), or mess around in alsamixer (launch a terminal and type "alsamixer" (assuming your using ALSA).

Let us know what happens.

therunnyman

---

