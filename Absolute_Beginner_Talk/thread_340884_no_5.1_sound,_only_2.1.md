---
title: "no 5.1 sound, only 2.1"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by benbuzz on 2007-01-17
Hello to all, 

installed Ubuntu 6.06 and am surprised how easy this went, pretty much everything works!  can't seem to get 5.1 sound working, though 2.1 works splendid on Rhythmbox and Xine.  System is Athlon 64 with SB Audigy LS and Logitech X-530 spkrs.  read some previous threads about sound problems but haven't found anything that could solve this.  any ideas anyone?  your help will be most appreciated

many thanks

---

### Post by crispy_420 on 2007-01-18
make sure that those channels are turned on in alsa.

---

### Post by mcduck on 2007-01-18
Have you tried if it works with some sound source that has real 5.1 sound? Like a DVD movie or something?

It only makes sense that you only get 2 channel sound from sound source that only has 2 channels ;) I suppose there is some way to copy sound from front channels to rear channels but that's still only 2 channel sound, not real 5.1..

---

### Post by benbuzz on 2007-01-18
good point, mcduck. the DVD movie does have 5.1 sound and I get sound on all speakers in XP.

also, crispy, not sure if that's what you mean, but when I went into alsamixer, I got some sliders in there (8, I think - I'm at work, now, so can't confirm exact number), two of which were approx half-way up and had 2 colours in their bottom half, all others blank. I could not move or change any of the sliders. also read in another thread about MM tags in alsamixer, well there were none of those in the alsamixer that popped up on my screen.

other: sound module is snd-ca0106 and is detected by system.

---

### Post by crispy_420 on 2007-01-18
Granted I don't have don't have a set of 5.1 speakers on my linux box (sorry it's on my Win box, gotta have surround for games) but I do have a Soundblaster Live 5.1.

Back to the point. If you right click on the Gnome volume control on your panel you get a few options, you can also double click it too. You will now have a window come up. Select "Preferences" under edit, It's the only option anyway. Now you'll want to activate those switches that apply to surround sound. I'm just guessing here but I would go with: Front, surround, center and LFE. Each will control the relative volume level of each channel so you can set up each to your liking.

Hope that helps you out.

---

### Post by benbuzz on 2007-01-19
ah, games!  that is the idea for the 5.1 spkrs here too!

... interesting!  the gnome volume control in the panel does not control anything!  it does not mute and when I right click on it, the 'Preferences' shows a list that I cannot do anything with.  however, when I click on 'open volume control', I get the alsamixer gui, where I can mute and where I also see switches.  although I have enabled them all, only the 'analog front' and its mute work and control volume on the 2.1.  the others are and stay non-operational even if I move the cursors or click on their mute switches.  on the 'switches' tab in alsamixer gui, there is only one checkbox labeled  SPDIF out.  if I click that checkbox, the sound goes mute.

I've noticed that there is also a forum for multimedia and video where some sound issues are addressed.  I'll move the post in there...

---

