---
title: "XMMS playing through wrong output"
date: 2005-09-22
forum: Absolute Beginner Talk
---

### Post by holiday on 2005-09-22
My system sounds come through my SBLive USB sound card, but XMMS is playing through my squeaky laptop speakers. 

And Rhythmbox and Sound Juicer play through the SBLive. 

I

---

### Post by holiday on 2005-09-22
[QUOTE=holiday]My system sounds come through my SBLive USB sound card, but XMMS is playing through my squeaky laptop speakers. 

And Rhythmbox and Sound Juicer play through the SBLive. 

I[/QUOTE]
 Figured it out.For others who have googled here:

Looked in Device Manager for the SBLive, saw it was using ALSA

XMMS - Options/preferences/OutputPlugin
set it to alsa, then under the 'configure' button set the audio device to SBLive

---

