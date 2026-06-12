---
title: "Increasing the volume more?"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by davidY on 2006-07-30
Hi, I am currently using Banshee to play my music on ubuntu. However, the volume control is pitiful - the maximum volume is not as loud as the system can go, so i always need a high volume. I try on windows, and I can get a much more respectable max volume on winamp.

Is there any way to increase the ovlume above the current maximum. preferably makingt he max volume for the system even higher?

---

### Post by nalmeth on 2006-07-30
Open the volume-control, and turn up PCM.

I can't remember where it is in gnome, but it should be quite easy to find.

Turn the PCM reasonably high, and fine-tune with MASTER

---

### Post by Rich3077 on 2006-07-30
Well.. perhaps your alsa mixer is not turned up enough.. open a terminal and type alsamixer to get at the settings. Type m to turn a setting on or off and the arrow keys to navigate. Some people (myself included) get fuzzy sound if the mixer is turned up past 75-80%.

---

### Post by davidY on 2006-07-30
THanks the alsamixer worked!

---

