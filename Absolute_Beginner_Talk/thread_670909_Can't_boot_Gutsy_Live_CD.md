---
title: "Can't boot Gutsy Live CD"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by onryou on 2008-01-18
Fairly new to linux. I downloaded the 64bit Live CD for Gutsy 7.10. MD5 checked out so I burned it and verified it and everything checked out ok. When I go to boot from the CD I get the startup screen just fine however when I try to choose Check CD for defects or Install/Start Ubuntu it loads the kernal then restarts. I tried deleting quiet and changing to nosplash in options but the printout flashes by a little too quickly to see what it's doing. Could the CD be defective or is there another issue? My specs:

C2D E6550
Gigabyte GA-P35C-DS3R
8800GTS 640MB

---

### Post by Dynaflow on 2008-01-18
Could you be more exact about the computer you're using, like what (exact) model it is?  If you could figure out at what point your crashes are occurring, that would be good to know too.

Also, is there a reason you're using the 64-bit LiveCD rather than the 32-bit one (besides having a Core 2 Duo)?  Maybe because you have more than 4 gigs of RAM or something?

The reason I ask is that, if you're taking Ubuntu out for a test drive with a LiveCD, you might want to use the 32-bit one instead.  It'll work just as well, and it's usually worked well much more consistently in my experience.

If you are trying to install, that's a different kettle of fish.  Just download the .iso for the Alternate Install CD to do a text-based install.  That way, you can reconfigure whatever's causing your crashes (possibly your graphics hardware) to play nice with Ubuntu more directly, without having to depend on just boot-time kernel arguments.

---

### Post by onryou on 2008-01-18
Perhaps I'll try 32bit. I've heard 64bit does run faster but are there too many compatability issues? I have a copy of both alternative and live for both 32 and 64bit. I've only burned the 64bit live though. Should I try giving the 64bit or 32bit alternative CD a go? Thanks for the help.

Also I built the computer so there's no model #. Motherboard is Rev. 1.0, EVGA card. Using Core 2 Duo E6550 overclocked. 2GB of RAM.

---

### Post by rexxxlo on 2008-01-18
sometimes you can hit pause (over by the page up and down button) on the keyboard during the boot and it will freeze the screen so you can read it

---

### Post by onryou on 2008-01-18
Managed to catch what seemed to be the last thing running. It said:

[53.8xxxxx] io scheduler cfq register (default)

Something along those lines.

---

### Post by Dynaflow on 2008-01-18
> **onryou said:**
> Perhaps I'll try 32bit. I've heard 64bit does run faster but are there too many compatability issues? I have a copy of both alternative and live for both 32 and 64bit. I've only burned the 64bit live though. Should I try giving the 64bit or 32bit alternative CD a go? Thanks for the help.

Also I built the computer so there's no model #. Motherboard is Rev. 1.0, EVGA card. Using Core 2 Duo E6550 overclocked. 2GB of RAM.

Ahhhh...

Okay.  Do the test drive with the 32-bit live CD (if it'll run; it may run into the same hiccup the other liveCD ran into, whatever it was).  If you plan on upgrading to more than 4 gigs of RAMin the medium-term future, install the 64-bit system from the alternate CD.  If you anticipate keeping your system as-is, go for the 32-bit system, either from the liveCD if it works or its alternate CD if it doesn't.  32-bit will likely continue to be the more-thoroughly supported version (and not just with Ubuntu) for some time yet.

---

### Post by nikoPSK on 2008-01-18
> **onryou said:**
> Fairly new to linux. I downloaded the 64bit Live CD for Gutsy 7.10. MD5 checked out so I burned it and verified it and everything checked out ok. When I go to boot from the CD I get the startup screen just fine however when I try to choose Check CD for defects or Install/Start Ubuntu it loads the kernal then restarts. I tried deleting quiet and changing to nosplash in options but the printout flashes by a little too quickly to see what it's doing. Could the CD be defective or is there another issue? My specs:

C2D E6550
Gigabyte GA-P35C-DS3R
8800GTS 640MB

LiveCD's don't like my system even though it's specs are nice. I just resort to a text based installer. Maybe use the check cd option. :)

---

### Post by onryou on 2008-01-18
Burned a 32bit Live CD and managed to check for defects. CD was fine so I tried booting with it. Same problem only it lasted a while longer before rebooting. Tried nosplash and that seemed to fix it. Started up fine and even detected the integrated audio. I'll go ahead with the install tomorrow. Thanks for the help.

---

