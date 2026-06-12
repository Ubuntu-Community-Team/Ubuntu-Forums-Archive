---
title: "Boot up issues."
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by Selrach on 2007-06-25
I managed to install Ubuntu with the text-based installer when the live one failed. However, I cannot boot up now into GUI. Heres what happens, it brings me up to a point with the following text:

Loading ACPI modules...
Starting ACPI services...
Killed.

I assume the kernel is what is being killed or something like that. I have tried disabling ACPI with the boot option acpi=off, and it just drops me to a BusyBox thing. The end result of this is that I end up at the console login or just at the console prompt. I try using startx and get a blank screen. Any help would be appreciated. I will list hardware specs. Oddly enough, ubuntu seems to have issues with this PC I built when Mandriva that I previously installed did not.

Processor - Athlon 64 3500+
Motherboard - ECS KN1 Lite Extreme (nvidia nforce chipset)
RAM - 1,024 MB
Video card - ASUS EAX1600XT (ATI type)
Hard drive - 160 GB, 16 MB cache, 7200 RPM, Western Digital
Ethernet card - D-Link DFE-530TX+

---

### Post by ronocdh on 2007-06-25
Are you using 32-bit or 64-bit? I would try switching and reinstalling, as long as you verify the integrity of the burn by using the checksum feature on the main screen of the live CD.

---

### Post by H.E. Pennypacker on 2007-06-25
You've posted the exact same problem in another thread in this forum.  Here it is:

[http://ubuntuforums.org/showthread.php?t=483397](http://ubuntuforums.org/showthread.php?t=483397)

Could someone lock this thread?

---

