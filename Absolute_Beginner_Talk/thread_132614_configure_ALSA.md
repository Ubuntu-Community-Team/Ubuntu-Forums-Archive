---
title: "configure ALSA"
date: 2006-02-18
forum: Absolute Beginner Talk
---

### Post by timsch75 on 2006-02-18
I'm running breezy on my athlon system.  I have sound working with OSS, but cannot get it to with ALSA.  I've seen nothing on how to configure it.  Please clue me in.  I've searched, but found nothing that wasn't like wading through mud.  thanks

---

### Post by timsch75 on 2006-02-19
Please help.  What command allows me to configure ALSA.  I know all of my other sound components work

---

### Post by Mustard on 2006-02-19
I'm not exactly sure what your looking for, but I'll take a guess that you might be looking for one of these two apps..

alsamixergui - graphical soundcard mixer for ALSA soundcard driver
gnome-alsamixer - ALSA sound mixer for GNOME

Both are installed via Synaptic Package Manager.

---

### Post by timsch75 on 2006-02-19
In slackware, the configure command was "alsaconf".  This doesn't work in Ubuntu.  I'm looking for this type of command to configure ALSA.  This is different from the Mixer commands.

---

### Post by Mustard on 2006-02-19
I wonder whether you need to use the alsactl command.  What exactly are you going to configure it to do?

---

### Post by timsch75 on 2006-02-19
I'm just looking for some command to get ALSA working.  With Slackware, the only thing to do was "alsaconfig" to configure the sound cards, and then "alsamixer" for playback settings.  Viola, everything worked fine after that with Slack.   Like I said, everything works with the OSS engine.  I've reinstalled all ALSA  components from Synaptic with still no sound.  I've tried to test ALSA through SYSTEM-PREFERENCES-MULTIMEDIA_SYSTEM_SELECTOR in gnome, and I just get the error message:  "Failed to construct test pipeline for 'ALSA - Advanced Linux Sound Architecture'"

---

