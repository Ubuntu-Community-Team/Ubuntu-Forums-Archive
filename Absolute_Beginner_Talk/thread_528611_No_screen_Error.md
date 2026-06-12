---
title: "No screen Error"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by rubab on 2007-08-18
Ok everything was going fine until when i tried to change the resolution to 32bit cause i wanted to run Splinter Cell Pandora Tomorrow and it needs the desktop to be in 32bit. i searched for it and found a post were it said to use sudo dpkg-reconfigure xserver-xorg in the terminal.

I answered the questions correctly. After i restarted the PC it  tells me that there is a problem with X server & No Screen found.  i have a ATI RADEON X1650 PRO card.
I tried"sudo dpkg-reconfigure -phigh xserver-xorg"
A similar window like "sudo dpkg-reconfigure xserver-xorg" came and i entered the correct info still the error was there.
Then i tried "sudo dpkg-reconfigure xserver-xorg" and after entering the necessary infos i restarted my pc and still i am not able to get into Ubuntu not even in the safe mode.

I am running a Dualboot PC with WindowsXp. I am willing to uninstall windowsXP permanently . But if these problems keep on coming i fear i will start losing interest in using Ubuntu.

---

### Post by nitro_n2o on 2007-08-18
you'll need the ATI driver.. it's weired that you can't even use ur screen... but search the forums for ATI drivers and how to configure them.. 
you can also manually edit /etc/X11/xorg.conf and modify the Sections Display, Device, and Monitor to suite your needs

---

