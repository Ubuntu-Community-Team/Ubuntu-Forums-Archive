---
title: "no sound, 5.10, nvidia CK8"
date: 2006-05-05
forum: Absolute Beginner Talk
---

### Post by qpackard on 2006-05-05
I have no sound except for system sounds (boot, bongos and various error beeps). I tried CD Player, the disk plays but no sound comes out.

Using 5.10
Nvidia CK8
motherboard msi K7NGM2
amd athalon 2500+

When I go to System/Preferences/Sounds it shows Active: Enable sound server setup and sounds for events.

System/Preferences/Multimedia Systems Selector:
Default Sink: Output: ALSA
Pipeline: alasink
Tests OK

Default Source: Input: OSS (I've tried them all)
Pipeline: osssrc
Test: no sound

Tried various suggestions on this forum but still no sound.
This machine is dual-boot and sound is present on the win side.

Do you have any suggestions to make the sound active? Have I left out any information?

---

### Post by zerhacke on 2006-05-05
Try changing the sound source type from whatever it is to something else, ie, go from OSS to ALSA.  You'll probably have to change it on a per application basis; changing it in one application won't change it for all applications.

---

### Post by qpackard on 2006-05-06
This is a little bizarre. I was prepared to follow your advice and slipped a cd into the drive and then a program called sound juicer popped up and started playing the disk. Got sound. I then tried CD Player but no sound, but since Juicer does the job I'm happy. Thanks for taking the time to respond.
:KS

---

