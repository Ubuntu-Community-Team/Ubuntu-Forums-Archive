---
title: "Audio Problems"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by oscabat on 2007-11-09
Something is seriously wrong with my sound drivers or something, because only certain sounds work. I had Ubuntu installed yesterday and Ventrilo, Steam, etc. were working fine. I reformatted and reinstalled 7.10 again today, only certain sounds work, occasionally.

I tried playing some music in Amarok, and it gives me the following error message: "Audio output unavailable: the device is busy.

I've gone through and tried all of the different outputs from the "Sound Preferences" window.

Any ideas?

It's the Realtek audio controller on a Gigabyte P965 motherboard.

---

### Post by kvonb on 2007-11-09
-

---

### Post by oscabat on 2007-11-09
Well I had ALSA Mixing disabled, so I enabled that and now music works in Amarok.  I tried your lines, and did the best I could following that thread, but I still don't have sound in TeamSpeak or Steam.  When I join TeamSpeak, I am immediately muted (microphone and speaker) and cannot change it.

---

### Post by kvonb on 2007-11-09
-

---

### Post by oscabat on 2007-11-12
I've messed with the Wine config some, and I noticed that in Terminal when I opened the audio tab, this shows up:

```
ALSA lib conf.c:3949:(snd_config_expand) Unknown parameters 0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:0
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
ALSA lib conf.c:3949:(snd_config_expand) Unknown parameters 1
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:1
ALSA lib pcm_dsnoop.c:558:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib conf.c:3949:(snd_config_expand) Unknown parameters 0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:0
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
ALSA lib conf.c:3949:(snd_config_expand) Unknown parameters 1
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:1
ALSA lib pcm_dsnoop.c:558:(snd_pcm_dsnoop_open) unable to open slave
```

Also, when I'm actually in the Audio Config, no matter which driver I try, it tells me "Audio Test Failed!"  And when I right-click on one of the drivers to configure it, I receive (for ALSA) "ALSA MultiMedia Driver!"

I'm not a scientist, but I don't think that it's from a specific application, because when I try to play music in XMMS, I receive the message "Couldn't Open Audio.   Please check that: Your soundcard is configured properly, you have the correct output plugin selected, [and] no other program is blocking the soundcard."

If I knew more about Ubuntu, I would be more adventurous, but I'm completely out of regular ideas.  Something is different between those two installations (on the first time, it worked completely, then I reformatted and installed again and now this is happening), but I can't find anything that I did differently.

---

### Post by oscabat on 2007-11-15
If I tried buying a cheap external sound card, would that help?  I'm all out of other ideas...

---

### Post by karoliina on 2007-12-19
I have been trying to run X-Plane 9 (Windows version because they haven't done Linux-version yet) on wine on Ubuntu, and I am having trouble because the audio does not work. Startup of X-plane breaks because of this. With wine version that comes with Gutsy, loading stopped when it was initializing lights. I found from Internet a message that someone got it working with newer wine. I tried that out (downloaded from winehq) and after that audio test started failing, no sound, and breakage with X-plane even earlier than before.

---

