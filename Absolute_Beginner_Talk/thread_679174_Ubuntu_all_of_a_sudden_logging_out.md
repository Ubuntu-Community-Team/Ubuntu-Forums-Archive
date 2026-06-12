---
title: "Ubuntu all of a sudden logging out?"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by thedon_1 on 2008-01-26
Twice during this session Ubuntu has just gone to a black screen and flashed a few lines of text, and then i find myself on the login screen.

This has not happend before, any ideas what's up?

---

### Post by SunnyRabbiera on 2008-01-26
hmm, are you using desktop effects?
What are your computers specs?

---

### Post by thedon_1 on 2008-01-26
Yep using desktop effects.

I have an AMD dual core 5000+
1GB Ram
250GB HDD
Nvidia Gefore 7600 GS (driver enabled)

I have only had Ubuntu just over a week, but i have not had anything like this happened before

---

### Post by Daveski on 2008-01-26
> **thedon_1 said:**
> Twice during this session Ubuntu has just gone to a black screen and flashed a few lines of text, and then i find myself on the login screen.

Sounds like the X Server has bombed. If you press CTRL-ALT-Backspace from a GUI it should appear to do the same thing (as this kills the server which should restart). It is likely to be a restricted video driver or the desktop effects as suggested.

---

### Post by SunnyRabbiera on 2008-01-26
> **Daveski said:**
> Sounds like the X Server has bombed. If you press CTRL-ALT-Backspace from a GUI it should appear to do the same thing (as this kills the server which should restart). It is likely to be a restricted video driver or the desktop effects as suggested.

yup, thats what I suspect as well

---

### Post by thedon_1 on 2008-01-26
Does this mean my install has gone bad for some reason, or after a reboot it should be ok?

---

### Post by thedon_1 on 2008-01-27
And also sometimes when i log in (Auto log in) the screen resolution isn't what it should be, i have to log out and then back in to fix it.

Anyone got any remedies?

---

