---
title: "Issue booting to ubuntu after installation"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by bobicus on 2007-03-10
I'm pretty new to ubuntu & linux in general, so I'm hoping that my issue is a simple one to deal with :)

I've installed it from a live cd on a dell desktop with a flat panel display with windows xp still on another partition of the same hard drive. I used the graphical installer and everything seems to have gone fine, but two issues have arisen since then.

When the installer quits and asks me to reboot, as the computer is shutting down it gives me a message to eject the CD & hit enter. The CD comes out ok, but the system seems to freeze up then and I have to manually restart it. Doesn't seem to be a huge problem, but I'm not sure if it is related to this next part.

Rebooting the computer the GRUB interface comes up and I can select ubuntu just fine. The loading screen pops up and the progress bar completes, but after that the screen goes completely blank and stays that way indefinately. I thought maybe it had something to do with video card or monitor settings, but from looking at /etc/X11/xorg.config, it looks like it has all of the correct settings as far as I know.

Any thoughts on what I should try next?

---

### Post by teaker1s on 2007-03-10
what graphics make and model?

---

### Post by oilchangeguy on 2007-03-10
don't have an answer about the blank screen. as for the re-start issue, i've got a laptop (toshiba satellite 1805-s177) that will not perform a re-start. other than that it works fine (except for modem, and i don't use dial-up so i don't care). i've got the same version (6.06) installed on a desk top that re-starts fine.

---

### Post by bobicus on 2007-03-10
The video card is a NVIDIA GeForce 7300 LE, the monitor is a Dell 1707FP, and the computer itself is a Dimension 9200 with Intel Core 2 6400 @ 2.13 Ghz., and I was installing 6.10. Thanks for the help!

---

### Post by teaker1s on 2007-03-10
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Graphics_Card]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#Graphics_Card")

you will need recovery kernel-select from grub boot options

---

### Post by bobicus on 2007-03-10
Thanks a bunch! That did the trick.

---

