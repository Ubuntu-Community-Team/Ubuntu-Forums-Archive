---
title: "The best version of Ubuntu for a PowerBook G3 Pismo"
date: 2008-10-25
forum: Apple Hardware Users
---

### Post by SphereCat1 on 2008-10-25
Hi! I'm currently running Xubuntu 6.06.2 on my Pismo. It runs great, but I need to upgrade to get access to newer repositories. I've tried Hardy, but it doesn't seem to support my graphics.
When I boot up, it makes it to where the logo should appear, then it looks like the screen gets too much power or something, and a weird pattern goes up the screen.

Anyway, if anyone has had luck with a newer version of Ubuntu (or Xubuntu's good, too.) that will work on my laptop, or how to fix the Hardy graphics problem, that would be great. :)

Thanks!
SphereCat1

---

### Post by ppc_guy on 2008-10-27
+2, I have 6.06.2 installed here on my G4/450. So far I've been locked into 1024x768 with no work around, and trying to boot the 7.10 live cd crashes on me, though I think ram is an issue (256 currently).

ppcguy
----------------------------------------------------------------------
When you are Sierra-Oscar-Lima. I'm Hotel-Tango-Hotel.
----------------------------------------------------------------------

---

### Post by SphereCat1 on 2008-10-27
Thanks for the feedback, ppcguy! My Pismo is 400mhz with 192 megs of ram, I had the same problem with gutsy.

SphereCat1

---

### Post by stream303 on 2008-10-27
If you feel like trying again in the future, maybe with a little more ram, be sure to write down your existing /etc/X11/xorg.conf from 6.0x.

Because of the major changes to Xorg, some video configs still need to be manually edited, which means after installation going back in via rescue mode or some other shell, and editing xorg.conf with the proper values gleaned from your earlier file, most notably the monitor and device lines.

Unfortunately Apple's hardware doesn't provide the proper feedback to the new Xorg so you have to manually edit it sometimes.  Luckily you have a known good config with 6.0x to fall back upon for reference.

---

### Post by Frak on 2008-10-27
Try Xubuntu PPC edition. To get it, you need to install server edition, then install the xubuntu-desktop package. I can't seem to find an Xubuntu PPC disk anywhere.

---

### Post by SphereCat1 on 2008-10-28
stream303: thanks for the tip! I just remembered that one time I got it to switch screens (via Ctrl+f-key) and it had some sort of error. I can't remember what it said, but it was something to the effect that X died, so that might have been the cause.

frak, I have been running Xubuntu PPC, and here's a link to the desktop version of dapper.

[http://releases.ubuntu.com/releases/6.06.2/ubuntu-6.06.1-desktop-powerpc.iso]("http://releases.ubuntu.com/releases/6.06.2/ubuntu-6.06.1-desktop-powerpc.iso")

I'd assume that the other versions have links on their release pages. :)

SphereCat1

---

