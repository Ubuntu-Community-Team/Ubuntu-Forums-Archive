---
title: "Edgy Live CD fails to load X, doesn't revert to prompt"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by stevensheehy on 2006-10-26
I'm trying to boot the LiveCD in order to install a fresh copy of Edgy. Every Ubuntu release I've tried (edgy is my 3rd now), the X server fails to recognize my graphics card (PowerColor X800 XL) with the default "ati" driver. Naturally, this time is no different and I get an X server error saying it can't load due to the driver. Even before this, the usual progress screen wasn't displaying properly.

This is pretty annoying that this hasn't been fixed in 1.5 years, but that's not the main problem. After I click through the X errors it goes to a blank, black screen. No command prompt or anything. Typing text and hitting enter doesn't do anything but display the entered text. Basically, I need to be able to edit the xorg.conf to change "ati" to "radeon" like I usually do, but without the command prompt I can't even do that. Any ideas?

---

### Post by stevensheehy on 2006-10-26
Nevermind, I was able to use the ctrl+alt+F1 combination to reveal the command prompt.

Still, the problems with my graphics card and the issue with the command prompt are both bugs, so I would appreciate if someone could let me know what I need to do to see that those get resolved.

---

