---
title: "Mint, issue with sound over HDMI [SOLVED]"
date: 2013-04-21
forum: Any Other OS
---

### Post by interestinfellow on 2013-04-21
BACKGROUND
Hello all! I fond and loved ubuntu around version 7, and it kept moving directions I didn't care for (bloat and features I didn't care about). I recently found Mint and have a renewed faith in migration totally back over to linux. 
That being said, I know little to nothing about Linux....but I'm learning...again.

OK. I hooked up a computer to my tv and set it up with win7 and mint14.  Mint will do all I need it to (and more), so I wiped the hdd and did a fresh install of Mint14 only.  I'm trying to keep the system lean and clean, so I would rather not install the Nvidia drivers to save some system resources (I see no benefit in my situation, unless you can persuade me otherwise).

HARDWARE
is as follows:I've started with a Dell C531, AMD Athlon x2 4000 2.1ghz, 1gb dr-5300, Sandisk 32gb SDSA4AH-032G SSD, 500gb SATA, GeForce 6150 onboard (not used), GeForce 315, DVD rom, and a decent (unidentified) onboard audio.

SCENARIO and QUESTION
Having just performed a fresh install of mint14, there is no sound to the tv over hdmi. I play with system sound settings and can't get the hdmi sound to work, so I go in and change the resolution to what I wanted (1024x768), apply, keep settings, and BOOM! Sound works over HDMI. Great! right?
no.
Reboot, no sound over hdmi again. Played around with sound settings some more, with no joy.
Change the resolution to anything else, apply, keep settings, and then changed it back to 1024x768, apply, keep settings, and it works again!

why? and what do I need to change to make it keep working?

---

### Post by pqwoerituytrueiwoq on 2013-04-22
Try deleting your ~/.pulse folder and log out and in again

---

### Post by Perfect Storm on 2013-04-22
Moved to Other OS/Distro Support.

---

### Post by interestinfellow on 2013-04-22
thanks PQ, but that didn't work (deleting .pulse and logging out/in).
another detail I just remembered; when it does begin to work after changing resolution, the "connector" choice under the HDMI changes from "hdmi connector port" to "hdmi connector port 2".


sorry, AI, and thanks!

---

### Post by interestinfellow on 2013-04-24
bump.

any other suggestions???

---

### Post by interestinfellow on 2013-04-27
simple fix and I feel like a dumb bass....
under the "hardware" tab just trying different profiles fixed it (without having to install the nvidia)

---

