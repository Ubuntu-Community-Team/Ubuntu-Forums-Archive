---
title: "Making /dev/audio1 the default"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by bill-linux on 2007-05-18
I am just setting up audio on a new system. The board has built-in audio, but it just doesn't seem linux friendly. So, I slapped in an old SBLive card which does the trick just fine. (e.g., cat sample.au > /dev/audio1 produces sound). **The Problem: ** The "second" SB card shows up at /dev/audio1 rather than /dev/audio - the latter is likely assigned to the in-board audio. Most programs, like XMMS, look for /dev/audio. How do I reassign the default audio to /dev/audio1? Or better yet, how do I  make the computer assign /dev/audio to the SB card on startup?

---

### Post by chamberlain2006 on 2007-05-18
You could disable the onboard sound.  There's probably an option in the BIOS.

---

### Post by bill-linux on 2007-05-19
Excellent suggestion. Worked like a charm. (Don't know why I didn't think of that!)

---

