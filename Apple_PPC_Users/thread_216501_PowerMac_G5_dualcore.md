---
title: "PowerMac G5 dualcore"
date: 2006-07-15
forum: Apple PPC Users
---

### Post by Bazzg on 2006-07-15
I decided to try ubuntu on my Powermac. It's a Late-2005 dual core G5, 2.3Ghz.

Install went ok, no hang ups or anything and I can dual boot OS X and Ubuntu.

BUT! After about 30 seconds the fans run up to full speed and stay there.

I found a couple of modprobes (i2c-something, and therm_pm72) The second one produces an error. After further looking I found another probe - windfarm - which DOES shut the fans down but only for about 30 seconds.

Obviously this makes Ubuntu unusable. Is there a fix or anything for this? 

BAzz

---

### Post by 3rdalbum on 2006-07-16
Try Yellow Dog Linux, or if you're experienced with Linux try compiling a new kernel. For some reason, although the Linux kernel supports good control of your fans, Ubuntu's version of it doesn't.

Or, is there possibly any way to set up a cron job on the probe, so the fans run for 30 seconds then off for 30 seconds then on again?

---

### Post by Bazzg on 2006-07-16
I'm used to freeBSD rather than Linux. It would be a shame to have to leave Ubuntu. I run it on a coule of x86 boxes and I like it.

I'll give YD a try and also do some research on making a new kernel.

The main thing is I'm worried that shutting the fans off completely might let the machine get too hot.

I've only ever had the fans come on a couple of times in OS X so I'd really prefer to have the temp sensors actually working properly.

Cheers,
BAzz

---

### Post by Bazzg on 2006-07-16
Well, YDL was fun for a while.. still got no fan control and X wouldn't work.

I'll stick to Ubuntu and keep checking for updates.

BAzz

---

### Post by RoadTripDK on 2006-07-16
Thermal control and sound seem to be two problems shared by all G5's at this point for anyone using a Debian based distro. Fedora Core 5 seems to have thermal control sussed, but I much prefer Ubuntu, so I as well am hangin' until we get some updates that work.

---

### Post by Bazzg on 2006-07-17
YDL install went ok, but gave errors on the restart, and then I got "Cannot display in this video mode" on the screen and had to power off to get the system back.

I'm not a great fan of Fedora - Ubuntu and generally, Debian-based distros seem a lot friendlier. Also, on all the various hardware I've put Ubuntu on over the last couple of years it's never failed to install or get X working with no fiddling.

I'm going to put 6.02 on my G4 powerbook soon, but again, I'll have to wait for the airport express card to be supported.

BAzz

---

