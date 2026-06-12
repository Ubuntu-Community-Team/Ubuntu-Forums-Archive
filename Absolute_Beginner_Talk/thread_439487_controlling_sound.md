---
title: "controlling sound"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by Julian Lewis on 2007-05-10
Hi
   I have managed to get Skype to work on my USB headset by setting Audio In and Out devices in the skype preferences to be Logitek USB headset and (ALSA -2 devices found) is indicated in the "Audio system to use".
However I never managed to find any setting that could use the microphone on my laptop, but, the speakers do work.There seems to be another OSS - 2devices found available in "Audio system to use"

When I use Flash player the sound always comes out of the laptop speaker even though in the preferences Sound settings USB Audio is set for all devices.

So it seems that the settings I set in various options are not taken into account at all times by all applications, but in others like "Movie player" all is just fine.

Ideally I would like to just plug in my head set and have all programs do the right thing, unplug it and have the sound devices change to the built in lap top speakers and mike.

Is there a way to have the devices set up correctly on a plug/play basis ?
If not, what are the settings I need in the two cases, USB mic/headphones - or - laptop mic/speakers.

I am using ubuntu 7 on a NEC laptop with what seems to be, according to the hardware information utility an 82801G High def audio device.

Thanks

---

### Post by gilgongo on 2007-05-13
Did you try running alsamixer from a command line and alter a few things from there?

---

### Post by Julian Lewis on 2007-05-24
I tried that, very primitive, but better than nothing. Later I found GNOME ALSA Mixer, and now i am starting to understand whats going on with the sound. This program is much better, so try it if you use the older version.

---

