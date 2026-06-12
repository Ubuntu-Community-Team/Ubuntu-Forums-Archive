---
title: "[SOLVED] Non-adjustable sound on iMac 5,1 with Ubu 8.04"
date: 2008-07-30
forum: Apple Hardware Users
---

### Post by tsr on 2008-07-30
Hi,

I have the reverse problem than many others, my sound works too good in 8.04.

I have somewhat defunkt dual boot (that means that I somehow screwed up my mac partition so I can't easily boot into it, but it's there) iMac5,1.

The thing is I can adjust the master volume by pressing volume-/volume+ on the keyboard, but that doesn't adjust the volume I hear.

If I get into alsamixer I can adjust the other sources (PCM, Front, Surround, Center and LFE) and then the sound gets adjusted accoringly.

It's just a bit cumbersome to fire up a terminal with alsamixer everytime I want to adjust the volume.

Are there other sound-applets, or anything else I can do to fix this?

(I tried changing the default-mixer-channel (my translation from swedish of the last option in the sound-settings dialog second tab) sound-device to chose one with only a master-channel but that didn't really change anything).

/tsr

---

### Post by cyberdork33 on 2008-07-30
In system > Preferences > Sound,
choose the channel that actually adjusts the volume level for you in alsamixer. (You can select more than one if it works better that way. I think I have Master and PCM selected in mine.)

---

### Post by tsr on 2008-07-30
> **cyberdork33 said:**
> In system > Preferences > Sound,
choose the channel that actually adjusts the volume level for you in alsamixer. (You can select more than one if it works better that way. I think I have Master and PCM selected in mine.)

Great thanks, you are the wo/man!

/tsr

---

### Post by cyberdork33 on 2008-07-30
> **tsr said:**
> Great thanks, you are the wo/man!

/tsr
Thanks, Please mark this thread solved (thread tools menu).

---

