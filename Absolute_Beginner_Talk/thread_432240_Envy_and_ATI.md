---
title: "Envy and ATI"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by Sanchopinky on 2007-05-03
I installed Envy and it says it supposedly installed ATI Catalyst Control Center, but I can't access it. Also everytime I install the ATI drivers from Envy I can't boot because it says my resolution is not available and I should switch. So it remains a black screen and I can't change anything. Envy also says FGLRX is not installed.

Bottom line:

Can anyone help me install the ATI drivers WHILE keeping my 1280x1024 resolution?

---

### Post by thelocust on 2007-05-03
First make sure you uninstall everything ati, fglrx and anything associated then I do a fresh install **[COLOR=Red]xorg-driver-fglrx[/COLOR]**

Then I did these:
**[COLOR=Red]sudo aticonfig --initial[/COLOR]**
**[COLOR=Red]sudo aticonfig --overlay-type=Xv[/COLOR]**

Finally, **[COLOR=Red]sudo dpkg-reconfigure xserver-xorg[/COLOR]**, selecting the **[COLOR=Red]fglrx[/COLOR]** driver and setting my monitor resolution how I wanted it

Then I rebooted and that was it.

---

### Post by Sanchopinky on 2007-05-03
Tried that, I got it working ^^

Thanks a lot man!

---

