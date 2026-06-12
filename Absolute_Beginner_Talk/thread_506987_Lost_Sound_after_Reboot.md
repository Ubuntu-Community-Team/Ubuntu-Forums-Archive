---
title: "Lost Sound after Reboot"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by ace214 on 2007-07-22
I am using Ubuntu Studio with an old Creative Soundblast Audigy 1 card. I had sound going and then I rebooted and now I have no sound. I have checked the mixer and everything is ok. One odd thing is that when I reboot the mixer goes back to my onboard sound. But even after I switch it back, I still have no sound. In Sound Preferences, I hear the tests on Standard PCM Playback but still the events do not work and XMMS, etc. produces no sound. Can't think of anything that I changed. The card shows up under "aplay -l" Thanks for any help.

ADD: Ok, I'm starting to get some of the programs to work. I got XMMS to work by configuring the audio output plugin but the system sounds still do not work.

---

### Post by ayenack on 2007-07-23
You need to turn off the on-board sound card in BIOS. Then go to Systems>Preferences>Sound and chose your Creative card probably Ensonic Audio (ALSA mixer) then test the output with sound playback tab Test etc. You could also just leave the on-board on and change it every time you boot but this may well cause the sound to be split i.e. flash player goes through one card and and your music app plays through another.

---

### Post by ace214 on 2007-07-23
Well turning off the onboard in the bios worked, thanks.

---

### Post by ayenack on 2007-07-23
No probs.

---

