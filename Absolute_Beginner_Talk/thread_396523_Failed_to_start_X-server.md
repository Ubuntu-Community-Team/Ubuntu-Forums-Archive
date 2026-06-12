---
title: "Failed to start X-server"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by Jurgonh on 2007-03-29
I´ve installed Beta graphics driver (NVIDIA) using ENVY
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Nov i cant reboot my system.
I get the following error message upon startup

Failed to load X-server
Nividia Kernel version is 1.0-9755
and the X-server version is 1.0-8776


How do i correct this?

Thanks for any help.

---

### Post by Bachstelze on 2007-03-29
Get the installer from nvidia.com and use that instead of some stupid automated script :)

---

### Post by Jurgonh on 2007-03-29
But it seams that the Nvidia version is newer than the X-server

and it said somthing about that it must be the same version or somthing..?

So if thats the problem its the x-serber i need to upgrade? but my system is up to date..

plz help.

---

### Post by BillGod on 2007-03-29
check your /etc/X11/xorg.conf file.  See if there is one with the date before you upgraded.  you can try renaming the xorg.conf file to xorg.conf.bak and rename your other backup to xorg.conf then sudo /etc/init.d/gdm restart.. if that does not work just reboot.

---

