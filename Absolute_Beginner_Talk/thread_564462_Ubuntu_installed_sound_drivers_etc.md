---
title: "Ubuntu installed sound drivers etc"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by devosion on 2007-10-01
Im not exactly sure if I can check this now after I performed an update with Ubuntu and also installed alsa-drivers for my sound card, but im trying to find out what Ubuntu comes pre-installed with for sound card recognition. The reason I ask is because my sound worked just fine prior to an update and i'd like to 'rollback' to the previous configuration or redownload the necessary drivers or apps to get it running. I also read somewhere that Gstreamer is a good alternative to alsa-drivers, is this correct?

By the way im using a Creative Labs Audigy 2 Value, and if I remember correctly Ubuntu recognizes my sound card as the Audigy LS. Thanks!

---

### Post by shae on 2007-10-01
Ubuntu comes with ALSA and OSS configured in the kernel IIRC.  If your card is not working under ALSA you should try switching to OSS.

---

