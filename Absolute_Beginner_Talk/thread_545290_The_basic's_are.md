---
title: "The basic's are"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by Heliose on 2007-09-07
ok, I'm not new at this but im new at this, knopics and fidora have been my choses so far but now im on ubuntu and i have to ask, why are my speakers not working at all?

from the big noob

---

### Post by jnorthr on 2007-09-07
missing some bits ? maybe looking here will provide several ideas : [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) or [https://launchpad.net/medibuntu/+bugs](https://launchpad.net/medibuntu/+bugs)

---

### Post by Heliose on 2007-09-07
thank you

---

### Post by steve.horsley on 2007-09-07
Double-clisk the speaker icon on the top-right. Make sure all the sliders are up and not muted by the mute button at the bottoom. If that doesn't work, Edit Preferences in that dialog, and start making other tracks visible, trying each of those.

Actually, this process is quicker if you run alsamixer in a console window, if you can bring yourself to do that.

---

### Post by Heliose on 2007-09-07
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile= music: could not open source for writing

this is what im gitting as an error when i try and use the sound options, i'm starting to miss the lines.....

---

### Post by Heliose on 2007-09-07
there is also this No volume control GStreamer plugins and /or devices found, i donk know if that helps tell what i should do.

---

### Post by MockY on 2007-09-07
I only encountered this error when the onboard sound card is disabled.

---

### Post by Heliose on 2007-09-07
so how do you enable it?

---

### Post by MockY on 2007-09-07
You have to do that in BIOS. Depending on the BIOS vendor the motherboard is using, the way of getting there may vary.  During POST, hit F1, F2, ESC, or F10. Again, it all depends on what the BIOS vendor is.

---

