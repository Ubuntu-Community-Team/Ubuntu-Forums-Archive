---
title: "Strange graphics problem"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by adam_d on 2007-06-24
Sorry if this is in the wrong place, or if it has an obvious answer. 

I'm new to Linux, and have never used it before, so sorry if this is obvious.

I recently got an old IBM thinkpad a21p with a pentium 3 850mhz, 128mb ram and ATI Mobility M3 graphics. It came with windows 2000, which runs ok, but i already have a newer laptop with windows xp so i wanted to use it to run linux. It only has 128mb ram, so I used the xubuntu alternate install with text mode install. I installed xubuntu onto it, which went well, as it installed straight away with no problems. However, once i rebooted the system, just before the xubuntu boot progress bar appears, the IBM logo from the bios flicks on the screen, but it is mirrored on either side. The progress bar displays ok, but once the login screen appears, the screen is messed up. There is a small flickering line down the middle, and the screen seems to be split, as the mouse pointer can be in two places at once. It's hard to explain exactly what it looks like, an the only way i could get a picture would be to use my camera. I could do this if it helps.
Would I be able to fix this by installing normal Ubuntu? How much slower than Xubuntu would it be?

Thanks

---

### Post by overdrank on 2007-06-24
> **adam_d said:**
> Sorry if this is in the wrong place, or if it has an obvious answer. 

I'm new to Linux, and have never used it before, so sorry if this is obvious.

I recently got an old IBM thinkpad a21p with a pentium 3 850mhz, 128mb ram and ATI Mobility M3 graphics. It came with windows 2000, which runs ok, but i already have a newer laptop with windows xp so i wanted to use it to run linux. It only has 128mb ram, so I used the xubuntu alternate install with text mode install. I installed xubuntu onto it, which went well, as it installed straight away with no problems. However, once i rebooted the system, just before the xubuntu boot progress bar appears, the IBM logo from the bios flicks on the screen, but it is mirrored on either side. The progress bar displays ok, but once the login screen appears, the screen is messed up. There is a small flickering line down the middle, and the screen seems to be split, as the mouse pointer can be in two places at once. It's hard to explain exactly what it looks like, an the only way i could get a picture would be to use my camera. I could do this if it helps.
Would I be able to fix this by installing normal Ubuntu? How much slower than Xubuntu would it be?

Thanks

Hi and welcome, I had a familiar problem with a dell laptop. I believe it is the graphics and not xubuntu. Have you tried to change the screen resolution to a lower setting? This is what help me and you can also check your xorg to see which drive your are using. This can be done by going to the terminal under applications, accessories, terminal  then enter the command  *gksudo gedit /etc/X11/xorg.conf* and the drive will be located under the devices section. Hope this helps. Good luck!:KS

---

### Post by adam_d on 2007-06-24
Ok, it seems I have fixed the problem. It caused this problem running at 800x600 resolution, booted in recovery mode and ran the auto adjust options while reconfiguring the xserver and it allowed me to choose the monitor's real resolution of 1600x1200, and after rebooting it was fine. Thanks for your help :)

---

### Post by kahm on 2007-06-24
I had the exact same issue. The only way I managed to get it working is by setting my colordepth to 16 instead of 24. Magically, X started coming up in 1600x1200, without the doubling cursor, etc :)

16bit isn't exactly wonderful, but it works.

---

