---
title: "complete hardware upgrade..."
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by myk.dinis on 2007-09-28
I am upgrading my entire computer (except the hard drives) and I need to keep my /home folder pristine and accessible.  I am going to need to re-install Ubuntu/Kubuntu/Xubuntu but I don't want it interfering or mesing up my /home partition...

I am going from:
PIII - 1Ghz
512MB SDRAM
dual-head dual-card mixed (ATI 128Pro and nVidia Vanta LT)
No USB 2.0

I am going to:
P4 - 2.93 Socket 478 (yeah I know, it's a celeron - but it's better than previous)
2GB DDR SDRAM
dual-head single card AGP 8x ATI Radeon (Something fast and powerful)
USB 2.0 
SATA
Ya know, fun!

I was wondering if I could do an upgrade or if I need to do a full re-install...
And if a full re-install is called for, will I be able to access my /home partition and have access to all the settings for all my software and stuff...Ya know, playlists and opera settings and all that fun stuff...since it's all stored in /~
Any ideas?

Thank you very much!
Myk

---

### Post by Whiffle on 2007-09-28
I'd copy the home directory somewhere, like a cd, or an ipod, or a flash drive just to back it up.  I honestly don't think you'll have to reinstall much, if anything.  You may have to reconfigure Xorg but i think it should handle the rest of it fairly well.

---

### Post by battyice on 2007-09-28
About 1 year ago I performed a similar upgrade on a computer running Debian linux (sid).   I had a P4 system with an ECS motherboard and a decent AGP video card.  I switched to an Asus motherboard with an Athlon processor and reused my video card and harddrive.  

The system booted up normally and ran great.  I was still running the Debian kernel, if you are running a custom kernel with specific drivers enabled you will need to reconfigure the kernel according to the new hardware.

---

### Post by LowSky on 2007-09-28
If your reusing your harddrvie and want to keep all your files the same just update Xorg.. everything will work fine... I've done  a few harddrive images ontp different machine and all I had to do was update Xorg

---

