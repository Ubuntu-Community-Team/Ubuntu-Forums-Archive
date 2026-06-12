---
title: "No monitor signal after ubuntu install"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by Thommo88 on 2007-12-22
Im new to linux and have been trying to install for the last few days and really dont want to give up just yet.

I first tried the live cd but starting the setup just seemed to cause my monitor to loose signal. I then read numerous forums and then installed using the text-based installer which seemed to work fine untill i tried to boot ubuntu when i started having the same problems.. im using dual boot where i have vista insalled on one hdd and ubunto on the other, vista is working fine but when i select ubunto i just loose my monitor signal..

i have read numerous forums on this but being new to linux im struggling to get into the command line to reconfigure my video configuration seeing as i have no display.  I have a 22" monitor that uses a 1680 x 1050 display and refresh rate of 60 so i cannot see an issue with it not being compatable..

---

### Post by taurus on 2007-12-22
Boot into recovery mode from GRUB menu and reconfigure your X server again.

```
dpkg-reconfigure -phigh xserver-xorg
-or-
dpkg-reconfigure xserver-xorg
shutdown -r now <-- reboot your machine
```

---

