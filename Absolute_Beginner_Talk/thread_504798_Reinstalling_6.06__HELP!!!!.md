---
title: "Reinstalling 6.06  HELP!!!!"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by noobboob on 2007-07-19
I am currently having fatal kernel errors/panics with my 6.06.  I previously had set up a RAID 5 in Ubu and afterwards tried to install drivers for the ATI 9250 card.  I managed to get my ATI card to work but Ubu is having kernel panics (most likely due to me incorrectly installing the ATI).  

I was wondering if i reinstall a fresh copy of ubu over my damaged version if i would still be able to access the information on my RAID!???  I'm really not sure what to do because during the GDM (gnome) start up it freezes while loading hardware drivers (this is why I think its the ATI).

Any advice or help at all is appreciated.  I tried running the repair OS off of the CD but to no avail.  HELP!!!!!!

---

### Post by Daveth on 2007-07-19
how did you install the ATI driver then?

---

### Post by alienexplorers on 2007-07-19
Just reinstall everything and hope for a better result.  Ubuntu from what I have read in these forums does have some problems with Raid setups.

---

### Post by noobboob on 2007-07-19
well i applied the ati driver fix for fglrx before installing the ati drivers.  when i figured out that i didnt have the ati drivers preinstalled in ubuntu (like some .doc have mentioned it should be there for a plug and play), i installed the correct ati drivers.  now it asked me to restart so i restarted and it gave me an error saying that the display was not detected because i had the monitor plugged into the onboard graphics, but after a few restarts and changing bios to boot the graphics card in the pci card i got the monitor to work with the ati but now i can't boot into the gnome GDM.  i tried reinstalling the grub loader and fixing the os, but both failed.  

i have 3 versions 6.06.28 - server, 6.06.26 - servers, and 6.06 - 383 of ubuntu and none of them work.  i did a safe boot with one of the servers and thats where i found out the error message that it hangs when it checks the hardware.

well the raid was a pain in the butt to set up but i got it up and running.  i forgot how i did all of that as well.  i'm just hoping that a fresh install on my non-RAID hd will read the rest of the raid.  anyone know!?!?  :confused:

---

