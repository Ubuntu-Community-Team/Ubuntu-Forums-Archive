---
title: "SoundCards, Sound Settings and Wine"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by ROUBOS on 2007-06-25
Hi all.
What sound settings do people use in Wine?

I've seen alot about getting graphics cards to work but not for SoundCards.

How do we know if our Creative SoundBlaster cards are working correctly. And why we only see ALSA drivers etc?

---

### Post by cogadh on 2007-06-25
Change the sound driver to ALSA. If you get popping or crackling noises, run regedit and add the following string:

HKCU/Software/Wine/Alsa Driver/UseDirectHW=y

See attached screenshot if that doesn't make sense.

---

### Post by ROUBOS on 2007-06-25
Hi
I did select ALSA, but in regedit > HKCU/Software/Wine/  I don't have an ALSA Driver folder

---

### Post by cogadh on 2007-06-25
You have to create it yourself. Just navigate to the Wine folder, right-click in the right pane and select New > Key.

---

