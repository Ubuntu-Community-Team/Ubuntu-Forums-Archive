---
title: "Nvidia graphics drivers broke ubuntu"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by Dapman01 on 2007-10-17
I installed my nvidia drivers using envy.  When it was done downloading and installing it prompted me to restart, which I did.  When I got back to the desk top ubuntu said that it needed to be unrestricted, so I did so and prompted me to restart again only this time it I can't get into the desktop, tells me I have something wrong with something X.
Is there anyway to save ubuntu and get the graphics drivers working
I have an 8800 gts and it worked in ubuntu before.

---

### Post by overdrank on 2007-10-17
> **Dapman01 said:**
> I installed my nvidia drivers using envy.  When it was done downloading and installing it prompted me to restart, which I did.  When I got back to the desk top ubuntu said that it needed to be unrestricted, so I did so and prompted me to restart again only this time it I can't get into the desktop, tells me I have something wrong with something X.
Is there anyway to save ubuntu and get the graphics drivers working
I have an 8800 gts and it worked in ubuntu before.

Hi when you reach the xorg error click ok and  use the keys ctrl, alt, F1 all at the same time and this will bring you to the command line. Login with user name and password and then enter this command 
```
sudo dpkg-reconfigure xserver-xorg
``` and choose vesa as the driver, answer a few questions and when complete use the command to reboot ```
sudo reboot
``` Hope this helps and good luck!

---

