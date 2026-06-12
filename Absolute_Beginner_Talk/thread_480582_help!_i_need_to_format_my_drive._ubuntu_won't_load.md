---
title: "help! i need to format my drive. ubuntu won't load."
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by sameoldude on 2007-06-21
hi, i'm dual booting windows xp and ubuntu. 
i had no problems at all, ubuntu was working perfectly and windows... well, it's windows. 
i got a new monitor and tried to get both screen to work separately (pretty easy thing to do on windows) but i pretty much messed up following the procedure.
now, i would feel ok if i could just put my livecd and reinstall, but i've tried that and ubuntu starts it's grub loading from the hard disk, even though i configured the laptop to boot from cd first.
maybe there's a way i can format it through windows (for free)? or some other recommended method?

thanks in advance

---

### Post by orb9220 on 2007-06-21
> but i've tried that and ubuntu starts it's grub loading from the hard disk, even though i configured the laptop to boot from cd first.

Are you sure you have a bootable liveCD?
You did burn it as a iso and not as a bootable CD? As this confuses alot of new users. 
As an example in Nero there is create a bootable CD which is NOT what you want. You want to burn iso to cd.

Some laptops reqire you to press the C key to boot from cd drive

---

### Post by overdrank on 2007-06-21
> **sameoldude said:**
> hi, i'm dual booting windows xp and ubuntu. 
i had no problems at all, ubuntu was working perfectly and windows... well, it's windows. 
i got a new monitor and tried to get both screen to work separately (pretty easy thing to do on windows) but i pretty much messed up following the procedure.
now, i would feel ok if i could just put my livecd and reinstall, but i've tried that and ubuntu starts it's grub loading from the hard disk, even though i configured the laptop to boot from cd first.
maybe there's a way i can format it through windows (for free)? or some other recommended method?

thanks in advance

Hi could you not just reconfigure your xorg from the terminal? Press alt,ctrl,F1 right after the grub loads and then login and use the command sudo dpkg-reconfigure -phigh xserver-xorg

:-k

---

### Post by ScottY_ on 2007-06-21
Whilst booting at the BIOS screenit will say press F8, F12, DEL or a key to go into setup do that make sure CD is first in boot order. Or for me i need to press F12 to choose if i want to boot from CD/HDD etc sometimes

---

