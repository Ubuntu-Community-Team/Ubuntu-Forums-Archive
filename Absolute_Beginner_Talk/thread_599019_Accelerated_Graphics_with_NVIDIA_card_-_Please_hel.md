---
title: "Accelerated Graphics with NVIDIA card - Please help"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by henrywm on 2007-10-31
I have had the following problems with enabling accelerated graphics with my NVIDIA GeForce2 Go:

1) When I tried enabling the drivers in the Restricted Drivers box my screen went black. I was eventually able to restore it.

2) Envy encountered this error:
ENVY ERROR: The following packages cannot be installed:
libqt3-mt-dev
kernel-wedge
rpm
libgtk2.0-dev
libxxf86misc-dev
libxtst-dev
libxxf86vm-dev
libxinerama-dev

None of the current threads on this issue have solved the problem for me.
Please help.

---

### Post by overdrank on 2007-10-31
> **henrywm said:**
> I have had the following problems with enabling accelerated graphics with my NVIDIA GeForce2 Go:

1) When I tried enabling the drivers in the Restricted Drivers box my screen went black. I was eventually able to restore it.

2) Envy encountered this error:
ENVY ERROR: The following packages cannot be installed:
libqt3-mt-dev
kernel-wedge
rpm
libgtk2.0-dev
libxxf86misc-dev
libxtst-dev
libxxf86vm-dev
libxinerama-dev

None of the current threads on this issue have solved the problem for me.
Please help.

Hi and can you tell us which version of ubuntu you are using ( 7.04 Feisty 7.10 Gutsy) and the model of the card ( this can be found with the command lspci in the terminal) ?

---

### Post by henrywm on 2007-11-01
I am using 7.10 Gutsy, but I had a similar problem with an earlier version of Ubuntu (I do not remember which).

ispci gave the following:
VGA compatible controller: nVidia Corporation NV11 [GeForce2 Go] (rev b2)

Thanks for your help.

---

### Post by overdrank on 2007-11-01
> **henrywm said:**
> I am using 7.10 Gutsy, but I had a similar problem with an earlier version of Ubuntu (I do not remember which).

ispci gave the following:
VGA compatible controller: nVidia Corporation NV11 [GeForce2 Go] (rev b2)

Thanks for your help.

Ok have you enabled all your repos, because I can find on my system what was posted.
```
2) Envy encountered this error:
ENVY ERROR: The following packages cannot be installed:
libqt3-mt-dev
kernel-wedge
rpm
libgtk2.0-dev
libxxf86misc-dev
libxtst-dev
libxxf86vm-dev
libxinerama-dev
```
Try and enable all your repos under system, administration, software sources. Ubuntu software and updates tab. Then you may try envy again, hope this helps and good luck!

---

### Post by henrywm on 2007-11-01
That allowed Envy to work, but when I rebooted my computer, the screen worked only on the left side when it reached the login prompt, and then it went blank before I could login. I had the same problem when I enabled the drivers in the Restricted Drivers box. I restored my computer by replacing my etc directory with a backup.

---

### Post by henrywm on 2007-11-05
Does anyone have any ideas on what I can do to fix this?

---

### Post by overdrank on 2007-11-05
> **henrywm said:**
> Does anyone have any ideas on what I can do to fix this?

You can try and use Envy to uninstall the drivers restart and then enable the restricted drivers.

---

### Post by henrywm on 2007-11-07
enable them where?

---

