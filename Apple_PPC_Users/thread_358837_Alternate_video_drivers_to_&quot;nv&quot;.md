---
title: "Alternate video drivers to &quot;nv&quot;"
date: 2007-02-11
forum: Apple PPC Users
---

### Post by Gaki on 2007-02-11
Hello all,


I just made the switch from OS X to Kubuntu, knowing full well about the issues with the nVidia driver and the poor substitute available in the "nv" driver.  What I didn't expect is precisely how bad ...

5-6 seconds to close an app before it disappears from the screen, 8-10 seconds to switch desktops, etc.  Everything works, but the video performance is so bad that I can't stand it.  I have 768 MB RAM on a 1.33 gHz G4 equipped 12" Powerbook.

Has anyone successfully gotten X to work with an alternate driver, i.e. VESA  I don't care about 3D acceleration at all, just 2D performance.

Gaki

---

### Post by grazie on 2007-02-11
I have an ATI card on machine my, so I use the open source ati driver. I don't have any performance problems. I have also used the open source nv driver on an x86 machine and found it to be pretty good for 2D. I think your problem may be somewhere else.

---

### Post by Gaki on 2007-02-11
Kubuntu was the culprit ... it autodetected my video card as an nVidia FX Generic.  It is an nVidia Go FX5200, so perhaps the difference between the desktop FX cards and the Go version was the issue.  I noticed that the live CD saw none of the slowdowns I was experiencing and just copied over the settings.  Voila, everything is fine and I'm a happy camper.  Thanks!

---

