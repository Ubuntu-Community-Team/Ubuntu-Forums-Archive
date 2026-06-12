---
title: "nforce2 no sound"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by Tango_Down on 2007-11-23
Hell, my soundcard (AC97 onboard) is certainly recognized by Linux (shows up on alplay -l) , and I followed a "Comprehensive guide to sound problems" sticky. Everything is unmuted in alsamixer and I ran the GUI alsaconfigurator.  Strikes me as an unlikely hardware problem. I tried to compile the alsa driver for the intel8x0 series, but it gave me errors. Any ideas, suggestions?

---

### Post by dams on 2007-11-23
Hi Tango_Down,

I had similar frustrating problems with onboard nvidia sound. In your mixer you'll find a couple of things that may help:
- Duplicate Front will duplicate the front speakers to all channels, I've got it checked
- Surround Jack mode, I have this as shared
-  Channel Mode I have as 6 Channels
- External Amplifier I have unchecked (read something in a forum that said try this)

Hope that helps.

Good Luck.

---

