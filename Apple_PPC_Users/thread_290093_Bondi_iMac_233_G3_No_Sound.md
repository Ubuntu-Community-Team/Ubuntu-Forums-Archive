---
title: "Bondi iMac 233 G3: No Sound"
date: 2006-10-31
forum: Apple PPC Users
---

### Post by RhoXS on 2006-10-31
Bondi iMac 233, 196Mb RAM, 20Gb HD

Xubuntu 6.10 alternate install.

Everything appears to be working except sound on internal speakers...

Sound chip shows up in lsmod (Power Mac Burgundy)

Checked to see if it was muted in alsamixer...it's not.

I'm not getting any errors....just no sound.

I had this problem before on a PC and ran alsaconfig to fix it. That doesn't seem to be available in Xubuntu.

Ideas?

---

### Post by RhoXS on 2006-11-01
Problem solved.

I muted, then unmuted the Headphone channel in alsamixer and sound magically started playing.

---

