---
title: "Macbook Pro keyboard not working"
date: 2007-04-17
forum: Apple Intel Users
---

### Post by asdasd on 2007-04-17
I just installed Feisty Beta on my Macbook Pro and the keyboard is not working in gdm so I can't login, it works ok in the console though. Can anyone help?

---

### Post by ronocdh on 2007-04-17
> **asdasd said:**
> I just installed Feisty Beta on my Macbook Pro and the keyboard is not working in gdm so I can't login, it works ok in the console though. Can anyone help?

How does the keyboard respond on the GRUB screen (I'm assuming you run GRUB, possibly with rEFIt?)? I triple boot my system, and while I have never had an issue with keyboard response on the rEFIt screen, the keyboard is very often (I'd say 80% of the time) completely unresponsive on the GRUB screen. This means I have to wait for the timer to count down and choose Ubuntu in order to boot into it; on the rare occasion that I want to boot WinXP, though, I have to do many hard shutdowns until I get a boot when the keyboard works in GRUB!

---

### Post by asdasd on 2007-04-17
The keyboard works for everything but gdm. I'm just using bootcamp, no rEFIt.

---

### Post by asdasd on 2007-04-19
I just updated to 7.04 final and the only key that works on the login screen is the space bar.

---

### Post by ronocdh on 2007-04-19
> **asdasd said:**
> I just updated to 7.04 final and the only key that works on the login screen is the space bar.
Did you do this by downloading the Live CD and installing freshly? Also, have you tried plugging in a USB keyboard? I know it is not practical for everyday use, but I am interested in the results from a diagnostic standpoint.

---

### Post by Chowbow on 2007-04-19
Just FYI, in case this helps anyone. The keyboard on my MBP was not working when I booted from the CD by holding down "C" when I started my mac. But if I'm in OSX, and I select the CD as the startup disc and reboot that way, the keyboard works. Strange...

---

### Post by asdasd on 2007-04-19
I managed to fix it, it was a problem with "XkbVariant" in xorg.conf.

---

