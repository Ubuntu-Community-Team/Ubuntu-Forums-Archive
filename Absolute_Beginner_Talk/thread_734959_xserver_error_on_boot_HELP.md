---
title: "xserver error on boot HELP"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by hogwartsnigel on 2008-03-25
Hi guys I am booting a second computer to Ubuntu at home all installed and working fine until.......
I installed the nvidia proprietary driver for my geforce 6600 card and upon reboot I now get a blank screen and a dead pc needing to be physically switched off to reboot (a pain because the battery is shot meaning a bios config each time---not a prob just a pain)
I can reboot in recovery console it tells me my error is in my xdriver at line 47 too many arguments.
Is there anyway to "go back" to my previous xdriver from the console help.

I've tried several things from other threads including
"sudo dpkf-reconfigure -phigh xserver -xorg"
I get xdriver not installed

I am about to try
"gedit /etc/x11/xorg.conf" and see if ZI can work out how to revert to the vesa driver that was working.

HELP

---

### Post by bumanie on 2008-03-25
Need to confirm that you can get into console mode.

---

### Post by hogwartsnigel on 2008-03-25
hi bumanie,
Yes I can get into the restore console, I've just tried the reconfigure code and it allowed me to install backup of my xorg, just rebooting now..give me 5mins.

Thnaks nigel

---

### Post by hogwartsnigel on 2008-03-25
well bumanie,
It lets me get to the logon screen but it doesn't correctly display it and I can't log on.
Can you help me through recovery console get my system back..damn why did i push it and load the proprietory drivers on this old box.

Thanks
In Anticipation

Nigel

---

### Post by hogwartsnigel on 2008-03-25
from the console how can i go back to the usual driver for nvidia non prop.?
Thanks

---

### Post by bumanie on 2008-03-25
How did you install the proprietary drivers? What are your system specs outside of the video card?

---

### Post by hogwartsnigel on 2008-03-25
Hi Bumanie
Installed the nvidia drivers within the proprietry drivers feature in the system tab. and chose driver from screen and resolution feature. All worked fine on the generic.
Is there a driver roll back or return to generic drive path through the console?

Thanks

Nigel

---

### Post by hogwartsnigel on 2008-03-25
The system is an olf pent 4 MSI motherboard, 1.7ghz. 512mb ram 250gb hdd on an old dell 17"lcd.
Its a rescued frankenstein from 3 old boxes, going to be a homework pc for kids

Nigel

---

