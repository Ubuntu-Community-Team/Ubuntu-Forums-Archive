---
title: "Gutsy Upgrade Problems"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by Wake Rider on 2007-10-23
Hi, I've had some problems with the Gutsy Upgrade. Gnome won't work, it brings back the login screen. (I installed KDE which is working OK) Google Earth does the same thing, and so does Compiz when I type that into the terminal. Also Gutsy won't find my internet connection (I'm using another computer to type this). Is it worth fixing all this or doing a fresh install of Gutsy??

---

### Post by Lord_Dicranius on 2007-10-23
If you have everything backed up (or /home is on a separate partition), I would think about just doing a fresh install.

---

### Post by chuckyp on 2007-10-23
Need a little more info than it just doesn't work.

What type of video card do you have?  How did you install drivers?  
What type of network card do you have?  How did you install drivers?

Did you have any software from 3rd party repos installed?  Did you leave these repos enabled before you upgraded?  etc....

---

### Post by Wake Rider on 2007-10-23
Graphics Card: Nvidia GeForce 7600 GS, driver installed by running the .bin script downloaded from Nvidia site. Yes I had repositories from third parties enabled. The network card is built into the Asus motherboard, and was detected automatically before the upgrade.

I think that there is too much work to be done to try and salvage this installation and all of my important files have been backed up, so I am going to take the advice to download the .iso and do a fresh install.

---

### Post by merwizard on 2007-10-23
Forget about the bin file from NVidia site. The common way to regain your graphic interface in Ubuntu is:

sudo dpkg-reconfigure xserver-xorg 

That will generate you a brand new (and hopefully working) xorg.conf file. Then, kill either the gdm or kdm, whichever are running and restart it (i.e sudo gdm). Or, you may simply reboot.

Then, when in Gnome, use the restricted driver manager to install the proprietary drivers automatically

---

