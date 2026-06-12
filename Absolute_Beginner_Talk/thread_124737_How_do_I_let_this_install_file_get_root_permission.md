---
title: "How do I let this install file get root permission?"
date: 2006-02-02
forum: Absolute Beginner Talk
---

### Post by bugmenot on 2006-02-02
edit: I managed to figure this out, but now I have a new problem.

Okay, I just managed to make Ubuntu completely unusable for the second time in 24 hours. I found out how to let the auto installer for my sound drivers work in sudo mode (put sudo in front of it, durr). After it installed with what looked like a few error messages, sound still wasn't working. I rebooted to see if it'd help and lo and behold:

> Error loading libraries: libasound.so.2 can not open shared object file: no such file/directory exists

This also gets spammed several times before the GUI shows up. It seems I managed to do *something* but I have no idea how to fix this except completely reinstalling again to probably just screw it up the same way yet again.

---

### Post by TechSonic on 2006-02-02
Go out and buy a cheap sound card, like a sound blaster live 5.1 digital, not any newer sb cards, that one. works really well and very cheap.

---

### Post by rmjokers on 2006-02-02
It sounds like the installer for your soundcard driver is breaking one of the audio libraries that GNOME depends on.  Either you have to find another way to get sound working, get a new card like the previous poster suggested, or try to re-install the package that has the broken library and hope that fixes the problem.

sudo apt-get remove libasound2
(may need a -f to force removal without removing dependencies)

sudo apt-get install libasound2

---

### Post by kaamos on 2006-02-02
No need to remove and screw up dependencies.
```
sudo apt-get install libasound2 --reinstall
```
should do the same.

---

### Post by rmjokers on 2006-02-02
Thanks, I didnt know about that option :)

---

