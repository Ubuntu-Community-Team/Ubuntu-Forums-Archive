---
title: "Problem with K53SV, nVidia GT540M Graphics Card"
date: 2011-11-17
forum: Asus Ubuntu Support (CLOSED)
---

### Post by thumaszz on 2011-11-17
Hello forum,
I have bought a new laptop, an Asus K53SV.
The laptop has a Nvidia GeForce GT540M Cuda 1GB.
I can't get the right driver for this.
When I try to auto-update to the newest version of Nvidia, my computer  gives a crash report fail when I reboot, and then I have to remove all  the Nvidia drivers in TTY.
And when I try to manually install the correct driver, I get an error  that I need to close the X server. And when I open it in TTY before  booting, I still get the same error.
When I add lspci -v | grep -i vga in Terminal I get this:
     Quote:
                                                 00:02.0 VGA compatible controller: Intel Corporation 2nd Generation  Core Processor Family Integrated Graphics Controller (rev 09) (prog-if  00 [VGA controller])
01:00.0 VGA compatible controller: nVidia Corporation GF106 [GeForce GT 555M] (rev a1) (prog-if 00 [VGA controller])                                 
It thinks I have an nVidia GeForce GT 555M, but I have a nVidia GeForce GT 540M.
How can I tell Linux which VGA I have? :confused:

---

### Post by 2F4U on 2011-11-17
Maybe this helps:

[http://askubuntu.com/questions/58056/which-driver-do-i-need-to-install-for-my-gt540m-if-i-want-to-use-bumblebee](http://askubuntu.com/questions/58056/which-driver-do-i-need-to-install-for-my-gt540m-if-i-want-to-use-bumblebee)

---

### Post by thumaszz on 2011-11-17
I followed the instructions and installed bumblebee and the specific nVidia driver.
Now when I reboot unity doesn't startup and lspci still gives that I have a GT555M, I think I need to change some settings for the graphics card...
Does anyone know how I can change this?

---

