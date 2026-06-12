---
title: "[SOLVED] no sound in mednafen"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by kevindubrow on 2008-03-22
Hi, I have Mednafen 0.8.1 and I get this error before a game loads:

Initializing sound...
  Using "ALSA" audio driver with device "default":ALSA Error: snd_pcm_open(&alsa_pcm, id ? id : "hw:0", SND_PCM_STREAM_PLAYBACK, 0) Device or resource busy
Error opening a sound device.

How can I get the sound to work? I have Ubuntu 7.10 64 bit.

Also, how do I configure my game controller? It is recognised, but it wasn't working:

 Initializing joysticks...
  Joystick 0 - Logitech Logitech Dual Action - Unique ID: ce96ea6b9d7ca56a


Thanks a lot!

---

### Post by Darganot on 2008-03-22
You must have had a program running when you started the emulator, maybe firefox with a youtube video up or something.  It could have been a process that hung as well, check the system monitor or just log off or reboot and log back on.  ALSA has problems playing two sounds at once sometimes,  There are workarounds, you can try searching these forums.

As for the controller, it is recognized, you just need to map the buttons.  I can't remember the key to start mapping mode, hit F1 you can find out for sure.

---

### Post by kevindubrow on 2008-03-22
Hah...solved the audio problem. Thanks a lot, I was expecting it to be a huge problem!

---

