---
title: "Advisory during boot -- S.M.A.R.T disabled ??"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by jerrynewt on 2007-12-26
During boot, I get a page identifying my processor (Intel dual core cpu 1.8 gig) and at the bottom it says ULTRA DMA Mode-5, S.M.A.R.T. capable but disabled. Any ideas what this means ?

---

### Post by IgnacioMiller on 2007-12-26
It is a method of analyzing your hard drives in order to anticipate failures such as mechanical wear, and electronic component failure. I imagine that it would be most useful in a server environment, but if you want to play around with it, there is a linux client [here]("http://smartmontools.sourceforge.net/"). And more information can be found [here]("http://en.wikipedia.org/wiki/SMART").

---

### Post by CatKiller on 2007-12-26
> **jerrynewt said:**
> Any ideas what this means ?

I'd imagine that you have a setting in your BIOS for whether SMART gets used or not. You might as well turn it on, since as far as I know there is no performance penalty, and you might get some advance warning before the hard drive dies which could be invaluable.

---

