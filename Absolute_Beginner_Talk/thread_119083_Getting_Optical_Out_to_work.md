---
title: "Getting Optical Out to work"
date: 2006-01-18
forum: Absolute Beginner Talk
---

### Post by karter74 on 2006-01-18
Hey guys, I have an MSI K8N Neo Platinum motherboard based on the Nforce3 chipset, and right now everything seems to be working fine right out of the box, except my optical output. I have searched for this but haven't found a definite answer it seems. Is it possible to get this to work?

---

### Post by mcduck on 2006-01-18
I've got nForce2 motherboard (with SoundStorm) and to use digital output I have to set programs to use hw:0,2 as audio device.

For example, in XMMS, I choose ALSA as output plugin, and then click the 'Configure'-button, and type 'hw:0,2' to 'Audio Device'. 'hw:0,0' is the default analog output.

---

### Post by karter74 on 2006-01-18
thanks, that works for xmms, but how do i get everything to use it?

---

### Post by mcduck on 2006-01-18
Honestly, I have no idea. Most programs have option to set hw like xmms does, and I myself rather like to have the rest of sound from analog outputs so that no system sound interferes with my music/movies :D

---

