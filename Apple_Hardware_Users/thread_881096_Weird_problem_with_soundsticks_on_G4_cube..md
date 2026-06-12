---
title: "Weird problem with soundsticks on G4 cube."
date: 2008-08-05
forum: Apple Hardware Users
---

### Post by DeltaBCooper on 2008-08-05
From install, the computer had no problem outputting to the right channel, but every time I go into alsa to change the left channel from nil, I'll drag the slider up and it will immediately shoot right back down to nil.  Through hours of playing with it, I have gotten it to output through the left channel as well but only at maybe 50%. I got it to do this through a labyrinth of fooling with the lock and mute buttons below the levels in alsa.  As soon as I change the volume level, it shoots the left channel back to the bottom.  Can anybody shoot me some helpful hints?

---

### Post by stream303 on 2008-08-05
I've been there!  You can try turning off PulseAudio, which will mitigate it somewhat, but the only solution I found was to use alsamixer **in a terminal**:

```
alsamixer
```

Use the arrow keys to find the master, or whatever is used for volume, and hit the B-key, to force a balance.  From then on, use the up/down arrow keys to change volume.

Yes, it's kind of a drag, but my gui volume control didn't want to play nice either.  I have to use Alsamixer as my control so I don't get that weird channel mute.

---

