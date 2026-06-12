---
title: "Soundcard (SB AWE32) and C compiler"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by Napjar on 2006-09-01
Hello,

I just installed a version of Kubuntu on my older PII pc after years of windows using ...
The installation went smoothly but i had no sound. I searched on this forum how to install a Creative Labs SB AWE32 driver and found the right info.
When trying to install (following the instruction on [www.alsa-project.org](www.alsa-project.org) ) this (took some time since i'm new and unexperienced with linux) i got a "no acceptable C compiler found in $PATH" ...
I have no idea what $PATH means but i guess that i do not have C compiler installed to compile this driver.
Can some help me with this problem ?
Thanks:?: :?:

---

### Post by elettronicha on 2006-09-01
> sudo apt-get install build-essential

will install all that you need to compile

---

### Post by Napjar on 2006-09-03
OK thx, got it installes with:
  sudo apt-cdrom add
  sudo aptitude update
  sudo aptitude install build-essential

since the package was on the Kubuntu distribution CD

---

