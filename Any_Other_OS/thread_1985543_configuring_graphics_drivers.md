---
title: "configuring graphics drivers"
date: 2012-05-23
forum: Any Other OS
---

### Post by tonglen on 2012-05-23
hi here i go i am trying to download later editions of  Mint 11, 12 and now 13 each time my machinerie gets to the mint logo and then blackness can hear the programmes loading but my screen stays black for ever ...
here is my graphics spec
hope this makes sense my graphics card spec

 00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)

found some more stuff hope this makes sense...

Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.2.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7

i have no idea how to configure the above in order for me to try to run nvidia driver(s)...in the hope that my machinerie will boot the live cd's properly...nomodeset is not an option until i know how to configure my drivers...i am aware that this is Ubuntu and not Mint but the more postings i do hopefully the wider the knowledge i gain so i can do what i have to do...here is my laptop spec

..Acer Aspire 5332, 1.9GHz, 3GB memory, Intel processor, 250GB HD...with thanks for your time and patience...I am a novice at this so bear with me thanks...

---

### Post by steeldriver on 2012-05-23
> **tonglen said:**
> 
i have no idea how to configure the above in order for me to try to run nvidia driver(s)...in the hope that my machinerie will boot the live cd's properly...nomodeset is not an option until i know how to configure my drivers...i

I'm confused... your lspci output appears to show you only have Intel integrated graphics - do you have an additional discrete nvidia card? or are you trying to configure the Intel one?

iirc for the older intel chips you may need "i915.modeset=0" instead of "nodmodeset" (however since iirc the newer intel drivers _only_ support KMS I *think* the effect of this is just to make Xorg fall back to the VESA driver - but it should get you a working screen)

---

### Post by Perfect Storm on 2012-05-23
Moved to Other OS/Distro Talk.

---

### Post by tonglen on 2012-05-23
sorry been a chump I have no idea what I am doing I have discovered that i have no need for nvidia drivers as i don't have a nvidia graphics card...oops...i have intel only as such should only be trying to work out why the later editions of Mint 11, 12 and now 13 after loading from a live dvd show only a black screen ...it has to be something to do with my intel graphics driver that causes this to occur ...

---

