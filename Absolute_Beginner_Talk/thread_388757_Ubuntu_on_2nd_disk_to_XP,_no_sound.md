---
title: "Ubuntu on 2nd disk to XP, no sound"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by AkiraBergman on 2007-03-19
I now got Ubuntu installed on the second disk from the downloaded ISO image burnt onto CD. I got XP on the 1st one.

The problem is that there is no sound. I got two sound cards. One is system's and the other is SBLive. XP has no probs using the system sound but Ubuntu does not give any sound from the audio CDs or Web.

The System-Preferences-Sound_Preferences window tests successfully only on Multichannel_Playback but NOT on Autodetect or any other option. I had a similar problem with Debian/Linux I tried before.

Could it be due to having another sound card (SBLive)?  The same panel's (Sound_Preferences) Sound selection has SBLive as default but does not give any other option. Why doesn't it give the system's own card as an option?

---

### Post by nudnik on 2007-03-19
> **AkiraBergman said:**
> I now got Ubuntu installed on the second disk from the downloaded ISO image burnt onto CD. I got XP on the 1st one.

The problem is that there is no sound. I got two sound cards. One is system's and the other is SBLive. XP has no probs using the system sound but Ubuntu does not give any sound from the audio CDs or Web.

The System-Preferences-Sound_Preferences window tests successfully only on Multichannel_Playback but NOT on Autodetect or any other option. I had a similar problem with Debian/Linux I tried before.

Could it be due to having another sound card (SBLive)?  The same panel's (Sound_Preferences) Sound selection has SBLive as default but does not give any other option. Why doesn't it give the system's own card as an option?

The volume may be down too far:-$ 

Make sure alsamixergui is installed. Open the mixer and check the levels, turn the master all the way up and see what happens. If this doesnt work feel free to beat me, I'm use to it.

---

### Post by AkiraBergman on 2007-03-19
Thanks I got it now, alsamixergui was missing as you said, so no beating this time ;-) But a bit weird. Master switch has no control, but Wave_LFE does. The system sound chip SigmaTel has a 4_spkr_streo button has also control. Go figure. Something to do with SBLive being deafault?

---

