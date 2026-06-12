---
title: "No LFE/Subwoofer on MacBook 4,1 in Karmic 64-bit"
date: 2009-11-19
forum: Apple Hardware Users
---

### Post by mdgill on 2009-11-19
The sound on my MacBook 4,1 does not work out-of-the-box after upgrade from 64-bit Jaunty to 64-bit Karmic.  The LFE (Center/Subwoofer) speaker does not work.  Karmic has no way to configure LFE or 5.1 sound.  I installed gamix, which provides that capability.  The I installed the Gnome ALSA Mixer instead, which offers the same capability, and the same behavior.  Unfortunately, while toggling the LFE off and then on does enable the LFE, this must be done every time audio is stopped then started again.  I can play a playlist of songs, for example, but I must toggle the LFE if I stop the playback.

I did install the patch that was created for Jaunty for this problem.  My ALSA driver is the most recent (1.0.21).  If I should not have that Jaunty patch in Karmic, I have no idea how to uninstall it.  The problem existed before I installed it, which is why I tried it.

There is a bug report on 5.1 problems - [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/445849](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/445849) - but it includes many configurations and maybe not all the same problem.

---

