---
title: "videos blank"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by AuToFiRE on 2007-11-27
Hey everyone
Im on 64 bit 7.10 by the way
I got ATI drivers working but as i got them working a couple things stopped working
Flash stopped working(but fixed it myself)
The one main problem I have not been able to fix is the video issue, I was able to watch my anime before putting up the ATI drivers but now its blank, i still get sound and just the flicker of a frame at the beginning of the videos.

How would I solve this without uninstalling the ATI drivers?

Thank you for your time

---

### Post by annda on 2007-11-27
first, i suggest experimenting with different players and different video output modes. vlc and mplayer are configurable. try x11 and openGL first. you might have to restart xserver or even reboot to notice changes.

---

### Post by master_kernel on 2007-11-27
Which ATI driver do you use?

---

### Post by noodles12 on 2007-11-28
Are you running compiz w/ AIGLX?

I recently installed the new ati drivers using compiz w/ AIGLX and I also get videos with a bunch of flickering. I havin't found a solution, but if you turn off Compiz-fusion, the videos play fine.

---

### Post by Takster on 2007-11-28
> **AuToFiRE said:**
> Hey everyone
Im on 64 bit 7.10 by the way
I got ATI drivers working but as i got them working a couple things stopped working
Flash stopped working(but fixed it myself)
The one main problem I have not been able to fix is the video issue, I was able to watch my anime before putting up the ATI drivers but now its blank, i still get sound and just the flicker of a frame at the beginning of the videos.

How would I solve this without uninstalling the ATI drivers?

Thank you for your time

If you are running compiz while getting the no picture/flicker and good sound still, it may be this:
[http://ubuntuforums.org/showthread.php?t=507328&highlight=compiz+totem+playback](http://ubuntuforums.org/showthread.php?t=507328&highlight=compiz+totem+playback)

Configure whatever player you prefer with those settings, mine was like that, now it works. ;)

---

### Post by noodles12 on 2007-11-28
This fixed my problem! You rock man!

---

