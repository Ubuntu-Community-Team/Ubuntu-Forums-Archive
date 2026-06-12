---
title: "audigy 4"
date: 2005-11-29
forum: Absolute Beginner Talk
---

### Post by buspital on 2005-11-29
My machine has an audigy 4 sound card in it, but i can't get ubuntu to use it. 
I changed the default sound card to Audigy 2 Value (unknown) in System>Preferences>sounds, but the sound in xmms is still coming from the onboard nvidia sound card. 
I also had a look in the device manager and i couldn't see anything that seemed to be the card.
Does anyone have any idea how to get these cards working?

---

### Post by raublekick on 2005-11-29
it might be too new for ubuntu (or the linux kernel) to recognize fully. 

but, having your onboard sound on could be a problem. try turning it off in the BIOS. do you have the speakers plugged into the onboard sound?

---

### Post by buspital on 2005-11-29
I thought that might be the case.

I have one amplifier plugged into the onboard and one into the audigy so i could tell which, if either, was making sound.

I'll try your bios suggestion, thanks

---

### Post by buspital on 2005-11-29
Doesn't seem to work. Never mind, thanks for the help.

---

### Post by delsdog on 2005-12-02
Have you had any joy doing this yet? I also have an audigy 4 and am considering just re-enabling the crappy onboard sound just now, as I just can't seem to get any sound out the Audigy card in Breezy.

---

### Post by brownen on 2005-12-05
Just goy my Audigy 4 (non-pro) working in Breezy. I had to download the alsa-driver 1.0.10 from alsa-project.org and build the driver from source. Once you do this and turn on the Analog/Digital Output Jack in alsamixer, your sound should work (you may need to tweak some of the other settings, I believe Front and the PCM options need to be turned up). I decided to download the driver after I installed Suse and my sound worked perfectly. I think there is a problem with alsa 1.0.9 or the way it was compiled in Breezy. Anyway, good luck.

---

