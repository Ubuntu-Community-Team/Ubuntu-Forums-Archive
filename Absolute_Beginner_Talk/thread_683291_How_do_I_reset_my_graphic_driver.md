---
title: "How do I reset my graphic driver"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by Djalmahal on 2008-01-30
So, i have Ubuntu 7.10 and an Intel 945 graphic card, I tried to improve some issues by installing another graphic driver, now my screen stays blank after I log in. I did this before and there is a way to tell Ubuntu to detect the original (safe) graphic driver, but I couldn't find the thread anymore.

Any tips?

Andreas

---

### Post by overdrank on 2008-01-30
> **Djalmahal said:**
> So, i have Ubuntu 7.10 and an Intel 945 graphic card, I tried to improve some issues by installing another graphic driver, now my screen stays blank after I log in. I did this before and there is a way to tell Ubuntu to detect the original (safe) graphic driver, but I couldn't find the thread anymore.

Any tips?

Andreas

Hi, when you reach the login screen use the keys ctrl, alt, F1 all at the same time and this will bring you to the command line. Login with user name and password and then enter this command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and when complete use the command to reboot ```
sudo reboot
``` Hope this helps and good luck!

---

### Post by Shazaam on 2008-01-30
This code will reconfigure X manually....
```
sudo dpkg-reconfigure xserver-xorg
```
This code will reset X back to default (if the original xorg.conf exists)....
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Djalmahal on 2008-01-30
Ok, that worked, thanks, my screen is back, it seems though as I am stuck with low graphic settings, when I try to reset them to custom in order to work with compiz I get the line "Desktop effects can not be enabled".

What to do?

Thanks 
Andreas

---

### Post by overdrank on 2008-01-30
> **Djalmahal said:**
> Ok, that worked, thanks, my screen is back, it seems though as I am stuck with low graphic settings, when I try to reset them to custom in order to work with compiz I get the line "Desktop effects can not be enabled".

What to do?

Thanks 
Andreas

HI and you may search synaptic manager for the 915 resolution and install. It may help. Also in your xorg you may insure that the i810 is the driver. ```
gksuo gedit /ect/X11/xorg.conf
```

---

### Post by Djalmahal on 2008-01-30
The problem with the blank screen strarted because I tried to set the driver for i810, so i won't change it again, unless there is some serious tip how to do it better. I read it on other posts to change that line to i810 but it just doesn't seem to work for me.

How can I enable the custom Visual effects by the way?

Thanks for everybodys input, long live ubuntuforums...
Andreas

---

### Post by rvanderwerf on 2008-02-13
I too have the same problem on 7.10. I tried to add a 2nd monitor, which worked until I restarted my computer. Now it runs in vesa 800x600. I keep switching my card back to i810 driver, but now my desktop effects are hosed (disabled). Also I'm running in 1600x1200 instead of 1920x1200 native resolution. I too have a Latitude D820 with a Intel 945 graphics card. I installed 915resolution, but it didn't help. I used to need 915resolution on 7.04, but a fresh install of 7.10 detected it properly. However I can't seem to get it back into that state. It seems dual monitors on intel chipset is still not a good solution.

---

