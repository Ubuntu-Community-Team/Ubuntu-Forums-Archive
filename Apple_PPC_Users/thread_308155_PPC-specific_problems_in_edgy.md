---
title: "PPC-specific problems in edgy"
date: 2006-11-27
forum: Apple PPC Users
---

### Post by eduardgrebe on 2006-11-27
I've been experiencing some serious problems since upgrading to edgy on my Powerbook G4 1.25Ghz 15". The system is no longer reliable, which is causing me severe headaches.

The major problems are the following:
(1) wake from sleep doesn't work
(2) intermittent login problems with gnome session

I have reported the following bugs, but they haven't received attention as yet. I was wondering whether anyone else has been experiencing similar problems.

[https://launchpad.net/distros/ubuntu/+source/update-manager/+bug/72336](https://launchpad.net/distros/ubuntu/+source/update-manager/+bug/72336)
[https://launchpad.net/distros/ubuntu/+bug/72337](https://launchpad.net/distros/ubuntu/+bug/72337)

---

### Post by gnomeza on 2006-11-28
> **eduardgrebe said:**
> (1) wake from sleep doesn't work
I just moved from Gentoo (where I was tracking the vanilla kernel on a weekly basis) to Edgy.

Since around 2.6.17 I started getting intermittent resume-from-sleep failures (same symptoms as you describe). On a hunch I'd say this was caused either by changes to the radeon driver, or the bcm43xx (airport extreme) driver. The bug seemed to happen less often after 2.6.19.

I've had only one resume failure since moving to Edgy.
Hopefully an updated kernel will be available soon (plus I'd like stable wireless back).

---

### Post by EuroCity on 2006-11-29
Talking about sleep and resume, does anyone know if there is a way to enable (deep, fanless) sleep also on a *desktop* Power Mac G4 (or G3, or G5)?

By default, on my G4, when I set it to sleep - an option of the red exit button on the right side of the top panel - it only sets a password-protected black screen, and nothing else happens.

Must one install pmud, or similar packages? I tried to install it in Synaptic: but, IIRC, it required to uninstall pbbuttonsd and all the *buntu-desktop meta-packages (I have all four of them installed).

Should I try anyway?

---

### Post by stream303 on 2006-11-30
I think this depends on your video card - I think nvidea equipped machines don't support full sleep.

---

### Post by EuroCity on 2006-11-30
It's an ATI Radeon 9000 Pro (Mac Edition). I tried to install pmud, but it didn't work (nothing changed): during the install, it was also said that it only supported PowerBooks, but maybe could also work on some desktops (BTW, is it an old program?). But nothing changed: when the Sleep button is pressed in the Exit panel, it only gets into the same password-protected black screen as before. Or maybe one must additionally edit some configuration files?

Probably, there is no way to get desktop Power Macs to (deep) sleep in Ubuntu, then...?

---

