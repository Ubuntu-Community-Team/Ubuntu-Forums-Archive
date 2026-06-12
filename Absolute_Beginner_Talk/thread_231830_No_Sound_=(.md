---
title: "No Sound =("
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by That Guy X on 2006-08-07
**When i first installed ubuntu the sound worked fine,but now its gone!:shock:  I have a SB card can anyone help?**

---

### Post by deadgobby on 2006-08-07
Is your sound card a SB Live or different?

---

### Post by That Guy X on 2006-08-07
Its a Creative Labs SB Audigy LS

---

### Post by That Guy X on 2006-08-08
Anybody?

---

### Post by patrickthebold on 2006-08-08
try from the shell alsamixer to adjust volumes.  Are there any error messages when you try to play sound?  Check dmesg and syslog in /var/logs.

---

### Post by davebgimp on 2006-08-08
So your sound is gone. Since when? After some updates? Did you do anything that might have caused it? What Ubuntu version are you using? Gnome, KDE...?

---

### Post by That Guy X on 2006-08-08
Since like the first 3 boots.I had the same problem before i switched from mepis. Im useing Gnome

---

### Post by Mtnear on 2006-08-08
I have a SB Live! 24 bit card, and I have to admit that sometimes I boot up and have sound and sometimes I don't.  Not sure why.

I always open up the sound preferences menu and make sure that the CA106 driver is selected (are you able to select that?), then reboot.  Usually that does the trick.

---

### Post by davebgimp on 2006-08-08
I have an SB Audigy card as well and the problem I ran into initially was that by default Ubuntu was using my inboard sound and not my card. Since the speakers were hooked to my card, I got nothing. I had to disable the inboard sound from the BIOS, I believe and everything worked automatically by default. Other than that, you could try checking each program and see which sound device it's using, but the BIOS trick worked best since it was a one-stop fix.

---

### Post by That Guy X on 2006-08-08
Thanks for the help the bios thing did the trick :D

---

### Post by davebgimp on 2006-08-08
> **That Guy X said:**
> Thanks for the help the bios thing did the trick :D

Awesome! Glad to help. :D

---

