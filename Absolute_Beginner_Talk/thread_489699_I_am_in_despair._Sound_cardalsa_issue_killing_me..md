---
title: "I am in despair. Sound card/alsa issue killing me."
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by samuraiCat on 2007-07-01
Guys, you've all been so great, but my time is almost up. I have installed Ubuntu twice, and I have not been able to get ALSA and my M-Audio revolution card to work. I can hear media when I click a WAV on my desktop, but no streaming. And my sound card isn't even being recognized -- it's not even appearing when I do lsmod!

I only have a few hours left before I have to abandon ship and go back to XP. My wife starts an online course tomorrow, and she needs the audio to work. 

I have spent all day on the chat rooms (mostly #alsa), but everyone is baffled. I've tried all the great howto's here, and there have been some changes, but it keeps coming back to this: When ALSA is loaded fresh, I get no sound. When I try to load my drivers, I get horrible distorted noise. When I abandon ship and downgrade to OSS, as I have now, I get no streaming audio (but at least mp3s work). When I try to reload ALSA, it gives me insane errors. It won't even let me reinstall the drivers.

What should I do? Fork over $200 for paid tech support? Rend my garments? 

Ugh. I love Linux, but I absolutely need that card to work. It may be what drives me away.

---

### Post by wolfen69 on 2007-07-01
open synaptic and install every "gstreamer" codec you see. if that doesnt work, you could download automatix2  [http://www.getautomatix.com/](http://www.getautomatix.com/)     and install codecs that way. it should work.

---

