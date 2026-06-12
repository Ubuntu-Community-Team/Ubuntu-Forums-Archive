---
title: "Unable to install on a G4--returning from prom_init"
date: 2009-04-20
forum: Apple Hardware Users
---

### Post by jimbren on 2009-04-20
I'm trying to install Ubuntu 8.04 on an old PPC G4 I just started messing with, and I'm not able to actually start the install.  It will boot the CD just fine and I try the 'expert install video=ofonly' command (along with just install video=ofonly and install).  It starts loading the kernel, then the screen changes to grey with black text, stating the following:

```
done
copying OF device tree..
Building DT strings...
Building dt structure...
device tree strings 0x022b0000 --> 0x22b0ac8
device tree struct 0x22b1000 --> 0x022c3000
Calling quiesce...
returning from prom_init
```

The screen will hang there for about 3 minutes, then the system reboots.

It is worth noting that I don't know the specs on the machine itself, and that while it did run OSX at some point, today it will not boot to that, either.  When I try to boot from the HDD, I simply get the Apple logo, then nothing.

Thanks,

jim

---

### Post by techgrl on 2010-09-03
if you are still a user of this forum, could you go back into your archives and recall how you (if you) solved this problem? I have the same one 5 years later!

---

### Post by QaysHP on 2012-01-04
I have the same problem and would love an answer if anyone has one.
Sorry for bringing the post back from the grave :(

---

### Post by rsavage on 2012-01-04
What CD are you trying?  Surely not 8.04?  Also, what exact machine do you have?  Can you provide a link at everymac.com please?

---

### Post by QaysHP on 2012-01-04
Sorry for not being more specific.

[Stock 450 MHz PPC G4 Cube]("http://www.everymac.com/systems/apple/powermac_g4/stats/powermac_g4_450_cube.html"), 320 MB RAM, Open Firmware Apple 4.1.9f1 BootROM (built 2001-09-14)

[PPC Oneiric minimal installer]("http://ports.ubuntu.com/dists/oneiric/main/installer-powerpc/current/images/powerpc/netboot/mini.iso") ISO

---

### Post by rsavage on 2012-01-04
A Cube!  Excellent, I am jealous!  I wanted to buy one of them to turn into an internet radio - but they cost like a hundred pounds over here!
 
I have to confess, I've never heard of your error before.  I'm a little unclear when this is happening.  Is is during trying the install or when rebooting after an install?
 
Have you tried the yaboot paramters video=ofonly nosplash ?

---

### Post by rsavage on 2012-01-04
No, I tell a lie [http://ubuntuforums.org/showthread.php?p=11439540](http://ubuntuforums.org/showthread.php?p=11439540) .

---

### Post by QaysHP on 2012-01-04
I have gone back and tried with Natty (2011.04) and Maverick (2010.10) as well as originally Oneiric (2011.10).
All mini netboot disks will boot on my Cube to the install menu screen with the "boot:" prompt.
After starting the install with any parameters listed bellow, the Mac sticks at the Open Firmware screen with the text from the original thread when using Oneiric or Natty.

parameters tried: [no parameters] and install, cli, install video=ofonly, cli video=ofonly

I also tried nosplash with all of the above, just to be sure.
Anyway, Maverick works, so I'll install it and see how I far it can get in the update procedures. Unfortunately the netboot WiFi feature seems odd, so I'll have to see what I can do about that.

rsavage: Thanks for pointing me to the other thread. Don't be too jealous of the Cube, it seems to drain time and money while still not having a useful purpose :P

---

### Post by pauljwells on 2012-01-04
I have to add my own 'me too' to the list. I am running Oneiric on my G5, but I can only boot the 2.6 kernel left over from the Natty mini-iso (install route was Natty mini, upgrade to oneiric and then install ubuntu-desktop)
If I try to boot a 3.0 kernel it hangs at the message. The G5 doesn't reboot itself tho, just hangs and cranks the fans up to max.

Don't even know where to start with a kernel problem...

---

