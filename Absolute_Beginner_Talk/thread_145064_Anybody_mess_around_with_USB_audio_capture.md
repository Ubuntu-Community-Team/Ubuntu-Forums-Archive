---
title: "Anybody mess around with USB audio capture?"
date: 2006-03-15
forum: Absolute Beginner Talk
---

### Post by therunnyman on 2006-03-15
Hi All,

I don't intend to restore any analog audio with my Ubuntu box (although Audacity looks fantastic), but I'm curious (yellow): has anyone out there attempted audio capture with a USB device on Ubuntu?  As I understand the USB codec spec, it'll work, but I haven't tried it yet.

If nobody responds, I'll try it, and report.

Thanks!

therunnyman

---

### Post by halfvolle melk on 2006-03-15
I haven't but wouldn't you get way too much latency? (for recording multiple tracks that should be synchronous anyway)

---

### Post by therunnyman on 2006-03-15
Hi halfvolle melk,

A lot of people were concerned about latency as they moved their capture hardware outside their machines.  The industry responded pretty well; anymore, with even consumer USB audio capture devices, it's really low, or well below 11ms anyway.  I've found capture over USB much better than capture through a PCI device, just because my USB device is shielded, and far away from stray machine electrons.  Latency never really became an issue for me.

Funny thing is, ALSA is showing to be the best API where latency is concerned.  I may end up moving here for capture and restoration after all.

Still haven't tried capture though...let's see what happens.

therunnyman

---

