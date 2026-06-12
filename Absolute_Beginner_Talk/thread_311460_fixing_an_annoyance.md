---
title: "fixing an annoyance"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by Chinkostu on 2006-12-02
ok for every previous install of ubuntu i've done (6.06 and 6.10) i've installed by switching to my intel onboard graphics, because the installer hangs when trying to use my fx5200. however, this isn't exactly brilliant, as i then have to mess around in the xorg constantly trying different combo's to get it to load to my FX.
 even then, i still have to set it to the onboard in the bios and have it switch over automatically on boot as otherwise it hangs on the driver loading.

now, i would be eternally grateful if anyone knows a way of installing dapper or edgy using my fx5200 rather than the onboard, as it would save me ALOT of hassle. if it is possible.

edit: if you don't understand, just ask and i'll rephrase.

---

### Post by taurus on 2006-12-02
Go into your BIOS and turn off the onboard video card!  Then, download and use the alternate CD to install Edgy on your machine!

[http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/](http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/)

---

### Post by po0f on 2006-12-02
Chinkostu,

When booting the live CD, edit the boot options to include "agp=off".  This worked for me and my FX5500.

[EDIT]

You may also find [this link](http://doc.gwos.org/index.php/Nvidia_Intel_Integrated) useful.

---

### Post by Chinkostu on 2006-12-02
> **taurus said:**
> Go into your BIOS and turn off the onboard video card!  Then, download and use the alternate CD to install Edgy on your machine!

[http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/](http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/)


Definately use the alternate CD then? i will give it a try, thanks. (I always forget that they're there!)

po0f, boot with the bios set to agp and then set the boot option to agp=off? sounds illogical, but could work! i will try both, thanks!

edit: will i be able to choose my partitions in the alternate install? i don't rather fancy it overwriting my windows partition!

---

