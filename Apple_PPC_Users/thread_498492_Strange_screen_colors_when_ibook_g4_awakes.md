---
title: "Strange screen colors when ibook g4 awakes"
date: 2007-07-11
forum: Apple PPC Users
---

### Post by mambro on 2007-07-11
When my ibook awakes from sleep i see some strange colors on its screen. With gentoo I didn't have the same problem..
I attach a video

---

### Post by mambro on 2007-07-14
nobody has the same problem?

---

### Post by reh4c on 2007-07-14
mambro,
I see the same thing on my ibook G4.  It's probably an issue with either suspend or gnome power manager.  The colors do look strange, but the unlock screen does pop up eventually .

---

### Post by stmiller on 2007-07-14
When waking from sleep, Linux is actually running a little script. "Turn on USB, get network address, load graphics driver, start alsa, ..."

So most likely the graphics driver is taking a few moments to load. Probably the LCD screen itself turns on before X is ready.

---

