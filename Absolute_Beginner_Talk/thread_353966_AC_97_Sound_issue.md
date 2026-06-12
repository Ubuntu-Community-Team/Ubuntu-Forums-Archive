---
title: "AC 97 Sound issue"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by falcons7 on 2007-02-05
Hello. Im currently running Ubuntu 6.10 and seem to be having a problem with my intel ac97 ich4 sound card. When the speakers are fully turned up the volume is really low. i have the pcm volume settings full. It doesn't seem that it is a driver issue since my card is found and gives me minimal volume out of my speakers. Any help?

---

### Post by laidback on 2007-02-05
Run alsamixer from a terminal to check the settings of input lines etc.

I had a problem with sound a few months ago and couldn't get any volume at all. In the end I discovered that I had set the mute on in Kaffeine. Now that shouldn't kill the sound everywhere else, or so I'm told, but it did. But I had had sound, then it stopped. Maybe not exactly your problem. But it might be worth checking that your Sound and Video apps all have mute off.

If you resolve this please put up a solution as I know that there is at least one other with the same problem. He disabled the onboard sound and installed a PCI card, now he has sound but it's not the best solution on a mATX board.

Have you tried System>Preferences>Sound, and then the test sound options, do you get anything? There are other settings here that can be worth checking.

---

### Post by ComplexNumber on 2007-02-05
> When the speakers are fully turned up the volume is really low.
which volume control are you referring to?

---

### Post by laidback on 2007-02-05
deleted..sorry

---

