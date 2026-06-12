---
title: "Screensaver broken, screen blinks"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by Hawk_AA on 2007-10-17
Hey,

I have just installed the Gutsy RC Ubuntu, and everything works great.

I had no problems with the graphics driver, which i expected. Nice!

But my screensaver does not work. I can preview the 3D ones in the selection tool, but when its supposed to enable (after 1 min, on idle) the screen goes black for a second or two, and goes back to where it was. this keeps on "forever". Im having a HP Compaq nc8430 notebook if it helps, if theres something with power saving abilities.

When i use a normal screen saver which obviously doesnt need much 3d rendering, it works.

Anyone?

Thanks
Hawk

---

### Post by 1337455 10534 on 2007-10-17
Mmm, is your system compiz capable?
Check using my guide on Ubuntu Guide under the Compiz Fusion (Universal) entry.

If not, know that screensavers are graphics intensive, and if your system can run them properly is a good indicator whether or not it is compi fusion capapble. These graphics may be too much for your CPU or graphics card//

---

### Post by Hawk_AA on 2007-10-18
Hi there,

Yeah, with my x1600, compiz works absolutely fine. No problems with that. Additionaly, it works to preview every single screensaver

Its quite fantastic: Everything works! Except this damn screensaver. Is this a bug that should have been fixed for the final release?

Hawk

---

### Post by 1337455 10534 on 2007-10-19
Probably so. Sorry for not reading the part about your new cars (oops)_.

---

### Post by bluedragon436 on 2007-10-20
I am having this same issue.  I have a Dell D610 and it runs everytrhing just fine including Compiz Fusion, I can view the screensavers just fine in the preview screen but once I apply it it just blinks when it comes time for the screensaver to cut on (after 1min. @ idle)

---

### Post by Colro on 2007-10-20
Same thing here, Radeon 9600 pro. The screen saver works fine if I lock my screen to enable it (or if I set it to lock my screen for me), but not just enabling it normally. My machine is quite compiz-capable, and I'm running with full effects enabled as I type this. I can play highly graphical games using WINE, so there's no way I can't handle a simple screen saver.

---

### Post by suziequzie on 2007-10-28
Same problem here. The Release candidate version had a working screensaver, but I screwed that up and did a complete reinstall of the final version this weekend, and now can't get screensaver to work. It just doesn't turn on after the 5 minute delay. (Also tried 1 minute delay, nothing...)

Nvidia 7300 GS card, AMD XP2800, and no problems previewing screensaver or running compiz fuzion.

---

### Post by 67GTA on 2007-10-28
I used this and fixed mine:

add > DPMS-dependent=false to the screensaver section of ~/.kde/share/config/kdesktoprc, or Gnome equivelant so it looks like:

[ScreenSaver]
Enabled=true
DPMS-dependent=false
Lock=false
LockGrace=60000
Saver=asciiquarium.desktop
Timeout=60

---

