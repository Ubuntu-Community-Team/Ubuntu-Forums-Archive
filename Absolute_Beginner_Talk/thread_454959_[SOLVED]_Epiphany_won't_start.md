---
title: "[SOLVED] Epiphany won't start"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by forestpixie on 2007-05-26
Small problem here - I can't use Epiphany.

When I try and start it it wants me to choose between recovering or not recovering tabs - last use ended unexpectedly.

Doesn't matter which I choose - same result - it appears to be starting then nothing happens

I've uninstalled it and reinstalled to no effect 

Can anyone help?

---

### Post by guitarmaniac on 2007-05-26
did it ever work?
when you uninstalled it did you remove it or *purge* it.
I recommend you ```
sudo apt-get purge epiphany-browser
```then```
sudo apt-get install epiphany-browser
```see if that works.

---

### Post by forestpixie on 2007-05-26
Yes it did work - I did the purge abd reinstall but it still seems to know that it ended and wants the restore or not tyhing before it starts.

I assume that there is a conf file or similar somewhere which isn't being removed on purge.

---

### Post by forestpixie on 2007-05-27
saw another post - [http://ubuntuforums.org/showthread.php?t=456307](http://ubuntuforums.org/showthread.php?t=456307)

similar to this - trying to start epiphany from terminal gives me an error - which means very little to me at all - I'm ok with the 1st and 3rd lines!

kevin@kevin-desktop:~$ epiphany
Segmentation fault (core dumped)
kevin@kevin-desktop:~$ 

Can anyone shed some light please!!

---

### Post by forestpixie on 2007-05-28
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/epiphany-browser/+bug/117419](https://bugs.launchpad.net/ubuntu/+source/epiphany-browser/+bug/117419) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Further to this I set thread off again at [http://ubuntuforums.org/showthread.php?t=456388](http://ubuntuforums.org/showthread.php?t=456388) - only to get it unanswered.

---

### Post by forestpixie on 2007-06-02
after todays ff update , reinstalling epiphany got it to work

---

