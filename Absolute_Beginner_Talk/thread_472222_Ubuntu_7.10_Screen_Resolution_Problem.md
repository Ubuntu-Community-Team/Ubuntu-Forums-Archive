---
title: "Ubuntu 7.10 Screen Resolution Problem"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by mig96 on 2007-06-12
when I installed the 915resolution package, and "make install"ed it like usual, and ran it, now I don't know how to change the res.  
HELP
(My native res is 1440x900)

---

### Post by brownknight on 2007-06-12
this is how you should do it.

To install 915resolution on Ubuntu make sure that you have included the "universe" repository and type (replacing "915resolution" with "855resolution" on Breezy):

sudo apt-get install 915resolution

Once the program is installed you can use the program to list all available vBios modes:

sudo 915resolution -l

The result should look similar to:

Intel 800/900 Series VBIOS Hack : version 0.5.2

Chipset: 845G
BIOS: TYPE 1
Mode Table Offset: $C0000 + $269
Mode Table Entries: 27

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1920x1440, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1920x1440, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1920x1440, 32 bits/pixel

If the resolution of your sceen is not present then you can overwrite a unused mode by the value of you screen. Since the results of using 915resolution are temporary you must arrange to have it run each time Ubuntu boots up. This is accomplished by modifying the file /etc/default/915resolution. For example if you want to overwrite the mode 41 by the resolution 2400x1600:

Ubuntu

gksudo gedit /etc/default/915resolution

Kubuntu

kdesu kate /etc/default/915resolution

Your file should look similar to:

} 
#
# 915resolution default
#
# find free modes by  /usr/sbin/915resolution -l
# and set it to MODE  or set to 'MODE=auto'
#
MODE=41
#
# and set resolutions for the mode.
XRESO=2400
YRESO=1600

This will ensure that the vBios mode 41 is overwritten in the RAM at boot-time, before initializing the X-windows. Since the resolution is now available in the vBios your system should automatically be able to set the right resolution after rebooting.

---

### Post by Clay_Banger on 2007-06-12
[This]("https://help.ubuntu.com/community/FixVideoResolutionHowto#head-0e3051713171cb5d1bf49dc2dc7bea24eb9ed83e") should help you out

---

### Post by mig96 on 2007-06-13
Thanks

---

