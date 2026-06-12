---
title: "Toshiba Satellite R15 Tablet support issue"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by Priest Apostate on 2008-03-19
I'm trying to set up the tablet support for the Toshiba Satellite R15 unit. I downloaded the following packages to the system:

wacom-kernel-source
wacom-tools
xserver-xorg-input-wacom
setserial  

I am using Feisty Version Ubuntu, which isn't causing any issues with operation (as a matter of fact, it's running Linux on the system better than it ran Windows). 

However, when I try to use the command 

*$wacdump /dev/wacom0*

I get the error message:  *10:50:50.127 ERROR: Failed to open /dev/wacom0: No such file or directory WacomOpenTablet: No such file or directory*

I'm sure that the packages are recognized, but I don't know where to go from there. Can anyone help?

~P

---

