---
title: "configuring sound"
date: 2006-04-24
forum: Absolute Beginner Talk
---

### Post by cptjaben on 2006-04-24
hi, i'm new to ubuntu and i'm wondering if there is a way to change your speaker setup from 2 speakers to 4 speakers. i've looked through system>preferences>sound and there doesn't appear to be an option for 4 speakers instead of 2. 

Thanks

---

### Post by therunnyman on 2006-04-25
I'm assuming you have one soundcard/device; it doesn't really matter, but I'll be operating on that assumption.

First, make sure you're using ALSA.  You do this by either right-clicking on the little speaker icon next to the time (the easy way) or getting into Applications-->Sound & Video-->Volume control.  If you did the former, and I know that you did, select your soundcard with the (ALSA Mixer) next to it, as opposed to the (OSS Mixer) option.

Next, launch a terminal, and type:

```
alsamixer -V all
```

After that, things get pretty self-explanatory.  Use the arrow keys to move left and right through your inputs and outputs, and use "Q" "W" "E" (left channel up, both channels up, right channel up, respectively) and "Z" "X" "C" (left channel down, both channels down, right channel down).

My mystical powers tell me you have a SoundBlaster Live!  All speakers are there, in Alsa Mixer.  Play a ditty, and fiddle in Alsa Mixer until you're happy.  When happy, hit Esc.  Close terminal. Donezo.

therunnyman

---

### Post by cptjaben on 2006-04-25
ahh it worked. Thanks much Sir

---

