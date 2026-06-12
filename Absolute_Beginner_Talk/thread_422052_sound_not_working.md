---
title: "sound not working"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by cchidamb on 2007-04-24
audio/sound not working
I just installed ubuntu 7.04 on my sony vaio laptop. I couldn't get get my sound working. Looks like the driver is loaded successfully, and the sound card is correctly recognized.

aplay -l returns

**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
Subdevices: 1/1
Subdevice #0: subdevice

Part of 'lsmod' returns

snd_intel8x0 34204 2
snd_ac97_codec 98336 1 snd_intel8x0
ac97_bus 3200 1 snd_ac97_codec
snd_pcm_oss 44544 0
snd_mixer_oss 17408 1 snd_pcm_oss
snd_pcm 79876 3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss

In /etc/modules I've added the following entry at the bottom

intel-8x0 , and rebooted. Still no luck, I would appreciate if you anyone could help to get my sound workin on the latest ubuntu I've installed.

P.S: Sound card is working fine, bcz if I boot it on windows, I can hear the sound.

I went to 'alsamixer' and made sure volume is up, and unmuted.

---

### Post by zvacet on 2007-04-25
**system>settings>sound** or **system>settings >multimedia system menu**

---

