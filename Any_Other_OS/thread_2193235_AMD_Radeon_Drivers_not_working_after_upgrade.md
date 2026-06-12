---
title: "AMD Radeon Drivers not working after upgrade"
date: 2013-12-11
forum: Any Other OS
---

### Post by mrjeffy321 on 2013-12-11
I have an HP dv6t notebook computerwith an AMD Radeon HD 7470M GDDR5 Discrete Graphics card.  Formerly,I was running Ubuntu 12.04 (64-bit) on this computer and had the AMDdrivers installed for the graphics card and it all worked fine.  Ifollowed these instructions (back in 2012) to install the drivers:
[http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450)


I recently upgraded to a fresh installof Linux Mint 16 (64-bit) on this same computer.  Now I am unable toget the AMD drivers to work.  I have tried installing the proprietarydrivers through the Device Drivers --> Drive Manager tool, where Iam offered three options:
--xserver-xorg-video-ati (recommended)
--fglrx
--fglrx-updates
I have the recommended xserver driversinstalled, but this runs both my integrated video card as well as thediscrete video card and burns up my battery in practically no time atall, plus it is hot and causes my fan to run all the time and make alot of noise.  I am not necessarily interested in getting the mostout of my graphics card as I am in saving my battery and having acooler, quieter laptop, which is why I want these drivers installed. When I try to install fglrx this way, on reboot Cinnamon crashes andI am forced to the fall-back mode.


I have also tried to install thedrivers in a more manual way, following the discussion from here:
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide)
But I get, best-case, another Cinnamoncrash or, worse-yet, failure of Xserver to start and I am bumped backto the terminal during boot.  I can remove the xorg.conf file from/etc/X11/ and restart Xserver, allowing my to revert my changes andget back to a bootable system.


Any idea why I am having so muchtrouble installing something that I know worked before with anearlier OS?

---

### Post by mastablasta on 2013-12-12
why not follow this guide (look at point 3.2): [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by mrjeffy321 on 2013-12-12
When I follow those instructions, for manual installation for the Intel/AMD hybrid graphics, I get an error during installation.  It says:
"DKMS part of installation failed" but then proceeds to finish the installation.

Afterward, when I run:
"sudo amdconfig --initial"
I get the following error:
"amdconfig: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory"

When I test the installation via:
"fglrxinfo"
I get the same error as above.

I found this page
[http://steveoliveira.com/blog/amd-13-1-64-bit-drivers-and-the-libgl-so-1-error/](http://steveoliveira.com/blog/amd-13-1-64-bit-drivers-and-the-libgl-so-1-error/)
that discusses the same problem, and I see that indeed that libGL.so.1 file is installed in my [COLOR=#333333][FONT=Helvetica Neue]/usr/lib64 directory.  But I do not have a [/FONT][/COLOR][COLOR=#333333][FONT=Helvetica Neue]/lib/usr on my system.
[/FONT][/COLOR]

---

### Post by mastablasta on 2013-12-15
have you tired removing driver (manually) and then reinstalling?

---

