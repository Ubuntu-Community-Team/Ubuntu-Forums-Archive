---
title: "triple boot"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by letitsnow on 2007-03-22
i'm trying to set up a triple boot with xp, kubuntu, and opensuse. i already have a very successful dual boot with xp and kubuntu. the problem with just letting the suse installer is that i still want kubuntu to be the main boot.
can i just edit the kubuntu grub to boot into suse by selection?

---

### Post by confused57 on 2007-03-22
> **letitsnow said:**
> i'm trying to set up a triple boot with xp, kubuntu, and opensuse. i already have a very successful dual boot with xp and kubuntu. the problem with just letting the suse installer is that i still want kubuntu to be the main boot.
can i just edit the kubuntu grub to boot into suse by selection?

The easiest way would be to install suse's grub to it's root partition & add an entry to kubuntu's grub to boot suse, using chainloading:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

for example:

title   OpenSuse
rootnoverify (hd0,x)
chainloader +1

---

### Post by tchoklat on 2007-03-22
this should help you!

[http://ubuntuforums.org/showthread.php?t=324621](http://ubuntuforums.org/showthread.php?t=324621)

---

### Post by letitsnow on 2007-03-22
> **confused57 said:**
> The easiest way would be to install suse's grub to it's root partition & add an entry to kubuntu's grub to boot suse, using chainloading:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

for example:

title   OpenSuse
rootnoverify (hd0,x)
chainloader +1

i'll try that. i've made a grub floppy, so i can't mess too much up.:D 

so my entry would be: 
title OpenSuse
rootnoverify (hdb1)
chainloader +1

it's being installed on a second drive in the first partition using kubuntu's /home partition as it's /home.

Thanks

 > this should help you!

[http://ubuntuforums.org/showthread.php?t=324621](http://ubuntuforums.org/showthread.php?t=324621)
i'm reading this now.

---

### Post by confused57 on 2007-03-22
> so my entry would be:
title OpenSuse
rootnoverify (hdb1)
chainloader +1

You entry would be something like this:


title OpenSuse
rootnoverify (hd1,0) <-----If Suse is on the first partition of your 2nd hard drive
chainloader +1

---

### Post by PurplePenguin on 2007-03-22
Yeah, grub looks really scary, but it's pretty easy to edit and get everything just how you want it.

---

### Post by letitsnow on 2007-03-22
i installed suse and it had a nice gui tool for editing grub, just move ubuntu kernel to top and click default, haven't rebooted yet to be sure though.

---

