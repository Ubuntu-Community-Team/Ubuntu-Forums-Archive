---
title: "sound"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by mindworm on 2006-10-16
i recently switched to linux, and i've noticed music plays so much quieter,i've turned everything up to the max level i think, but it's still not that loud
 
i'm thinking maybe i need to find the right driver, but i wouldn't know how to

any suggestions

---

### Post by Bloch on 2006-10-16
So you have tried double-clicking on the volume control to get all the Playback controls, and set PCM to the max?
The command 
alsamixer
at the terminal gives you a more primitive interface to the same settings.

Beyond that, there's not much you can do. My sound is also quieter in ubuntu than in windows.

You should fill in the test wizard on the "Ubuntu Device Database"  (install it if you don't have it in the System Tools menu). Your comments will be sent to the ubuntu team along with the internal hardware data. 
It might get fixed in an update!

---

