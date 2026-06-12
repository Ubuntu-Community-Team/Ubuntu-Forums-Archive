---
title: "BSOD using Unity with MBP 6,2 hardware"
date: 2012-11-05
forum: Apple Hardware Users
---

### Post by moschops on 2012-11-05
I've been trying to get Ubuntu 12.10 running stably on my MBP 6,2 hardware but I keep having black screen of death crashes while using the Unity Launcher.  I think the recent Ubuntu update that I got today made the problem less prevalent - it used to be that I could just mouse up and down the launcher and get a crash in a second or two.  Now it is spurious - moving over or out of the launcher (auto-hide is on) screen goes black, fan comes on, can't get a terminal with Ctrl-Alt-F1 and have to reboot.  The record I can find is a syslog message:

Nov  5 10:59:40 oscar kernel: [ 4446.631124] compiz[2522]: segfault at 7fc753fadfff ip 00007fc63f122fd6 sp 00007ffff0819a30 error 6 in libnvidia-glcore.so.304.60[7fc63dc16000+19d0000]
Nov  5 10:59:40 oscar kernel: [ 4446.633767] NVRM: GPU at 0000:01:00.0 has fallen off the bus.
Nov  5 10:59:40 oscar kernel: [ 4446.633774] NVRM: GPU at 0000:01:00.0 has fallen off the bus.


Note my nVidia version is 304.60 which is the very latest driver from nVidia downloaded from their website.  But I was experiencing these crashes with all the drivers that came with Ubuntu - the nouveau ones and the nvidia tested, updated and experimental versions.  I rather think this is a compiz bug, not the driver.  

Hopefully someone else has some ideas - the only way I've been able to avoid the crashes so far seems to be a) never use the launcher, just use dash to start apps, or b) use gnome classic or xfce.

Any ideas? Or do I just file a launchpad bug and be done with it.

---

### Post by jcekstrom on 2012-11-10
I am having the exact same issues.  Has anyone heard anything on this?

---

