---
title: "How do I uninstall a hardware device?"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by ROUBOS on 2007-09-15
Hi people.
I have some sound issues. I have disabled the Realtek AC'97 on board sound card, but I still get it as default on the alsamixer.
What I would like to do is uninstall both my soundcards Realtek and Audigy 2, and get Ubuntu to detect them again.
Or if at least just uninstall the Realtek card which I have disabled in BIOS.

How do I go about uninstalling hardware like that?

---

### Post by Maestro23 on 2007-09-15
> **ROUBOS said:**
> Hi people.
I have some sound issues. I have disabled the Realtek AC'97 on board sound card, but I still get it as default on the alsamixer.
What I would like to do is uninstall both my soundcards Realtek and Audigy 2, and get Ubuntu to detect them again.
Or if at least just uninstall the Realtek card which I have disabled in BIOS.

How do I go about uninstalling hardware like that?

Check your other post.  Someone chimed in with some possible help.

---

### Post by colo on 2007-09-15
First, you need to find out what kernel module is driving the device you want to "remove" from your configuration. `lsmod` and the file /proc/modules may help you on that; I suspect `fgrep snd /proc/modules` should yield you something useable.

Once you located the module most probably in charge of your device, you add a line like "blacklist modulename" to /etc/modprobe.d/blacklist - that ensures it won't be loaded automagically again.

Hth.

---

### Post by ROUBOS on 2007-09-15
do the following make any sense?

snd_ac97_codec
ac97_bus
97_codec,snd_pcm_oss

These are what have the bane ac97 which is the onboard Realtek card. So what would be the entry in the blacklist file?

---

### Post by ROUBOS on 2007-09-15
When entering the command

aplay -l 

I get card 0: V8237

and 

card 1: Audigy2

So does that mean that I blacklist V8237 ??????????

---

### Post by ROUBOS on 2007-09-15
did that. No luck :(

---

### Post by ROUBOS on 2007-09-15
I uninstalled the following from Synaptic:

alsa-base
alsa-firmware-loaders
ld10kl

I restarted and the sound works fine.
Should I re-install them?

---

### Post by ROUBOS on 2007-09-15
This is crap :mad:

No matter what I do it does not work. The problem gets fixed, the sound works, I restart and the same crap again :mad:

I'm going to re-install ubuntu from scratch. If this time around it does not work for me... gonna go and put on window$ again :(

---

### Post by ROUBOS on 2007-09-15
just did a restart again just to double check. And it works now.
I DON'T GET IT

---

### Post by bodley on 2007-12-27
I had the same problem when I installed an Audigy sound card. Linux would randomly set either the onboard sound chip or the Audigy card as the default sound device. Despite the former being disabled in the BIOS.

I did the following to disable my onboard Realtek sound chip (via VT8237R Plus chip set).

Add the following line to the /etc/modprobe.d/blacklist file:

blacklist snd-via82xx

Make sure you save the file and do a restart.

---

### Post by jonmartin on 2007-12-27
> **bodley said:**
> I had the same problem when I installed an Audigy sound card. Linux would randomly set either the onboard sound chip or the Audigy card as the default sound device. Despite the former being disabled in the BIOS.

I did the following to disable my onboard Realtek sound chip (via VT8237R Plus chip set).

Add the following line to the /etc/modprobe.d/blacklist file:

blacklist snd-via82xx

Make sure you save the file and do a restart.

How on earth would that help when he doesn't have that card?

Here is output from lsmod

snd_ac97_codec
ac97_bus
97_codec,snd_pcm_oss

so I would try with

blacklist snd_ac97_codec
blacklist ac97_bus
blacklist 97_codec

not sure about the last one though ... maybe it won't load when the others are blacklisted already.

---

### Post by c0met on 2007-12-27
You can also select the appropriate audio driver by right clicking on the volume control in the system tray and then choosing "preferences". That will take you to a drop-down list of recognised drivers. Audigy is supported by ALSA.

---

### Post by cookieforyou on 2007-12-27
I have an Audigy soundcard> 02:01.0 Multimedia audio controller: Creative Labs SB Audigy LSwhich I recently removed for some reason and went back to the onboard soundcard and the only problem I had was the selection of the correct fader for volume adjustment (I use 'analog front') for controlling the volume, plus another setting regarding recording input/monitor as I use a FM tuner connected to the input.  After inserting the Audigy back into the PC (the audio quality from the Audigy is considerably better than the onboard audio) the above had to be done again....nothing major. ;)

---

