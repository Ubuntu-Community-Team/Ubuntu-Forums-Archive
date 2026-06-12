---
title: "nVidia nSanity"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by Doc.Caliban on 2007-06-05
I had the latest nVidia beta driver installed and working perfectly with Beryl.

I installed ndiswrapper and couldn't get back into xserver.

I edited one line in the blacklist file to get my old wifi driver back.

I couldn't get into xserver because it claimed the nvidia driver was no longer configured correctly.  (Coming from 15 years of Windows, I don't question totally arbatrary and illogical error messages.)

I changed the driver from "nvidia" to "nv" and was able to get back into xserver.

I tried reinstalling nVidia drivers with Automatix, but they would not run Beryl.

I uninstalled those again (via Automatix) and reinstalled the original beta drivers that were working before.

I can't get into xserver with them and when I run dpkg-reconfigure -phigh xsrever-xorg, it shows the "1/2" next to the nvidia driver.

I have no idea what to do to get the drivers that worked before to work again.

-Doc

---

### Post by Crafty Kisses on 2007-06-06
> **Doc.Caliban said:**
> I had the latest nVidia beta driver installed and working perfectly with Beryl.

I installed ndiswrapper and couldn't get back into xserver.

I edited one line in the blacklist file to get my old wifi driver back.

I couldn't get into xserver because it claimed the nvidia driver was no longer configured correctly.  (Coming from 15 years of Windows, I don't question totally arbatrary and illogical error messages.)

I changed the driver from "nvidia" to "nv" and was able to get back into xserver.

I tried reinstalling nVidia drivers with Automatix, but they would not run Beryl.

I uninstalled those again (via Automatix) and reinstalled the original beta drivers that were working before.

I can't get into xserver with them and when I run dpkg-reconfigure -phigh xsrever-xorg, it shows the "1/2" next to the nvidia driver.

I have no idea what to do to get the drivers that worked before to work again.

-Doc

To be honest, I gave up trying to install my drivers a long time ago, but Ubuntu is still the best OS I've ever used. :p

---

### Post by Doc.Caliban on 2007-06-06
> **Codename said:**
> To be honest, I gave up trying to install my drivers a long time ago, but Ubuntu is still the best OS I've ever used. :p

Again though, it had been working perfectly.  I just need to get back to a clean install of these drivers.

---

### Post by Crafty Kisses on 2007-06-06
> **Doc.Caliban said:**
> Again though, it had been working perfectly.  I just need to get back to a clean install of these drivers.

You can try disabling them from the "Restriced Driver Managers" and then enabling them again.

---

### Post by dacookiemonn on 2007-06-06
> **Codename said:**
> To be honest, I gave up trying to install my drivers a long time ago, but Ubuntu is still the best OS I've ever used. :p

I have been thinking that too. im new, but installing stuff just seems a little weird, i think ms has a good installer, but then again you get more errors.

---

### Post by Azakus on 2007-06-06
Try "sudo nvidia-xconfig".
It automatically creates nvidia's xorg.conf file, which might fix your problem.

---

### Post by Crafty Kisses on 2007-06-06
> **Azakus said:**
> Try "sudo nvidia-xconfig".
It automatically creates nvidia's xorg.conf file, which might fix your problem.

That's possible, but it could be that my chipset is not compatible with my Video Card, but what I don't get is that it worked with Windows XP before I wiped that piece of garbage off my harddrive.

---

### Post by Dedoimedo on 2007-06-06
Hello,

Did you follow this guide:
[http://ubuntuforums.org/showthread.php?t=263851](http://ubuntuforums.org/showthread.php?t=263851)

Dedoimedo

---

### Post by Doc.Caliban on 2007-06-07
I've tried everything mentioned in this thread so far with no luck.  

I think what I need to do is find out how to completely uninstall all traces of the nvidia driver and start again with the beta driver that worked perfectly in the first place.  I'll look for a thread on that, but in the mean time does anyone know of instructions to do this?

-Doc

(BTW, thanks for all the suggestions!)

---

