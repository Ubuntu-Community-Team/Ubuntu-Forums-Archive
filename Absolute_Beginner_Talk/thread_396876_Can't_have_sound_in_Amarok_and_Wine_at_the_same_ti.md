---
title: "Can't have sound in Amarok and Wine at the same time?"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by fyleow on 2007-03-30
I'm using Ubuntu Feisty beta and I'm running Warcraft 3 Frozen Throne under Wine.  Everything runs fine except for sound.  If I run WC3 first and then try Amarok it won't play, complaining about how the sound device is busy.  If I run Amarok first and then go into WC3 there's no sound in WC3 and it gives me an error at the beginning saying that sound cannot be initialized.

Is there a fix for this?

---

### Post by justin whitaker on 2007-03-30
> **fyleow said:**
> I'm using Ubuntu Feisty beta and I'm running Warcraft 3 Frozen Throne under Wine.  Everything runs fine except for sound.  If I run WC3 first and then try Amarok it won't play, complaining about how the sound device is busy.  If I run Amarok first and then go into WC3 there's no sound in WC3 and it gives me an error at the beginning saying that sound cannot be initialized.

Is there a fix for this?

Yeah, there is.

You need the aoss package. Run synaptic to get it, then start WC3 with aoss wc.exe (or whatever), then start amarok with aoss amarok.

---

### Post by theoldwiseking on 2007-03-30
I faced a similar problem and the solution was by updating to the latest amarok from amarok.kde.org, after installation of the new version, if missing pluggin, amarok will install it automatically for u

---

