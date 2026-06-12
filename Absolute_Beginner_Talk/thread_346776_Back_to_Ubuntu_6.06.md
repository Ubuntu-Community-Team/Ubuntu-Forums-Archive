---
title: "Back to Ubuntu 6.06"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by RudolfMDLT on 2007-01-26
Hi there,

I am going back to Ubuntu 6.06 because I can't get the ATI driver do all that it should and thus cannot run Compiz/Beryl on my 9600.

Just a couple of questions on downgrading:

1) Will version an earlier version of Evolution support email backed up from a better later version

2) Will I still be able to use my VmWare Virtual machines once I run Ubuntu 6.06.

3) Will I be able to upgrade to the latest Open Office and KDE in 6.06?

Help will be greatly appreciated!

Thanks,

Rudolf

---

### Post by lyceum on 2007-01-26
To down grade, you have to re-install. To answer you questions, you can upgrade your programs yourself, rather than the whole machine. If you are jsut "downgrading" because you can't use the 3D effects, you may want to jsut stay ware you are and wait for Edgy. You can upgrade then and they will work by defult.

---

### Post by LinuxConvert on 2007-01-26
Hi there Rudolf

The ati drivers on edgy work fine, I've managed to get beryl working with AIGLX and the open source ati driver on edgy. Open your xorg.conf file and under Section "Device" just make sure that you have selected "ati" as your Driver and you should be good to go.

FYI my graphics card is an ATI Radeon 9550

Hope that helps.

LC

**EDIT**
Changed a confusing sentence :)

---

### Post by lamego on 2007-01-26
> 1) Will version an earlier version of Evolution support email backed up from a better later version
Yes because there are no changes to the mail files format.

> 2) Will I still be able to use my VmWare Virtual machines once I run Ubuntu 6.06.

VMWare Virtual machines are not host system dependent, they will even run on Windows.
> 3) Will I be able to upgrade to the latest Open Office and KDE in 6.06?
No, the latest versions are not available for the older releases, at least no from the official repositories.

---

### Post by RudolfMDLT on 2007-01-27
Hey all,

Thanks! 

I&#314;l try the ati driver and see what pops up. Thanks for the ¨to the point¨ answers!

Thanks,

Rudolf Hoehler

---

