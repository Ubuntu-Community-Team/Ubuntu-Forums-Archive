---
title: "No sound after ALSA reinstall"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by THE_DEATH_M on 2007-06-22
I'm a Kubuntu Feisty user, and accidently screwed alsa, to a state it seemed to never have been on my PC, and then installed it again following [http://alsa.opensrc.org/index.php/Quick_Install]("http://alsa.opensrc.org/index.php/Quick_Install") and my heart warmed when i saw Kmix was detecting the alsa mixer, but found out there was absolutely no sound. After a lot troubleshooting everything seemed to be ok, but still no sound. If that helps anyway, when i ran amaroK xine engine returned error: can't initialize any drivers (or something like that).
Any idea pls?

---

### Post by Happy_Man on 2007-06-22
Tried ```
alsamixer
``` in the terminal?

---

### Post by THE_DEATH_M on 2007-06-22
Yes tried it, seems to work with no problem, I restored the settings just the way they were, but nothing... also checked the Soundcards order and etc, but nothing seems wrong...
EDIT: solved problem by simply running alsaconf :)

---

