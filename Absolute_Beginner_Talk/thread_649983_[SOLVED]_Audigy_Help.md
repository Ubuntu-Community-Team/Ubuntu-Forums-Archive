---
title: "[SOLVED] Audigy Help"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by Epic Plecostomus on 2007-12-25
I have an older Audigy card.   It's not working with this install.   Any suggestions aside from replacing it?  ;)   I tried a fix suggested in the wiki but no luck with it.

---

### Post by linuxwizard on 2007-12-26
Have you tried this
check that your switches are set correctly - for instance that if you use the analog output the analog switch is set ON or that the digital or S/PDIF switch is set OFF.

To get to the switches > right click speaker icon on gnome panel > open volume control > click on switch tab > you could have 3 or 4 settings there look for the one analog/digital unmark it > try playing something

---

### Post by Epic Plecostomus on 2007-12-26
Nothing.

No system sounds, no audio from the players, nothing at all.  I suspect its a configuration error somewhere and I have no idea how to go about troubleshooting it.

I've tried various combinations of ALSA and OSS settings and nothing happens.  I tried reinstalling ALSA, removing it in favor of OSS, putting ALSA back on...    Again nothing.

I log out and log back into windows the sound works, so it's a Linux issuse.

---

### Post by kpkeerthi on 2007-12-26
You may want to double check if all the channels are "unmuted' (Press 'M' to mute/unmute) and sliders raised in **alsamixer** (open a terminal and type **alsamixer**)

---

### Post by Epic Plecostomus on 2007-12-26
> **kpkeerthi said:**
> You may want to double check if all the channels are "unmuted' (Press 'M' to mute/unmute) and sliders raised in **alsamixer** (open a terminal and type **alsamixer**)

[SIZE="6"]HOORAY![/SIZE]  That got 'er.   PCM was muted.  :guitar:

---

### Post by kpkeerthi on 2007-12-26
So it is not a linux issue now :)

---

### Post by Epic Plecostomus on 2007-12-26
> **kpkeerthi said:**
> So it is not a linux issue now :)

No it appears to be an operator issue.  Ahem.  Yes.  Move along now.  good day... :redface:  :p

---

