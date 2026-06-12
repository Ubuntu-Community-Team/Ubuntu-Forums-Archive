---
title: "Video Card Troubles"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by samasaur on 2007-06-22
Hey, I'm fairly new to the Ubuntu but I've enjoyed the experience so far. I've installed Ubuntu to my new computer I bought recently and I've have a few problems. When I go to the restricted drivers manager and install the drivers for the ATI accelerated graphics driver and restart, I receive a black screen after the startup loading screen. I didn't know how to fix that nor get into safe mode so I had to reinstall Ubuntu from the bottom up again. Does anyone know a way to install drivers for my video card that won't give that black screen or a way to correct that problem? I've gotten World of Warcraft to work except its really slow. I was hoping that Beryl would work as well but it doesn't.

samasaur@Desktop:~$ glxinfo | grep rendering
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  16
  Current serial number in output stream:  17

I received that message in terminal when I checked for direct rendering. Any help would be greatly appreciated. Thanks! -Sam

My system: Amd X2 4200, DDR2 1Gb Ram, SATA2 250Gb Harddrive, ATI X1600PRO 512mb Videocard, Ubuntu 7.04 Feisty Fawn

---

### Post by Crafty Kisses on 2007-06-22
> **samasaur said:**
> Hey, I'm fairly new to the Ubuntu but I've enjoyed the experience so far. I've installed Ubuntu to my new computer I bought recently and I've have a few problems. When I go to the restricted drivers manager and install the drivers for the ATI accelerated graphics driver and restart, I receive a black screen after the startup loading screen. I didn't know how to fix that nor get into safe mode so I had to reinstall Ubuntu from the bottom up again. Does anyone know a way to install drivers for my video card that won't give that black screen or a way to correct that problem? I've gotten World of Warcraft to work except its really slow. I was hoping that Beryl would work as well but it doesn't.

samasaur@Desktop:~$ glxinfo | grep rendering
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  16
  Current serial number in output stream:  17

I received that message in terminal when I checked for direct rendering. Any help would be greatly appreciated. Thanks! -Sam

My system: Amd X2 4200, DDR2 1Gb Ram, SATA2 250Gb Harddrive, ATI X1600PRO 512mb Videocard, Ubuntu 7.04 Feisty Fawn
You might want to try this command:
```
sudo dpkg-reconfigure xserver-xorg
```

This will pop up a text-based graphical "wizard" that will ask you questions about your keyboard, your mouse, your graphics card, and your monitor. Answer the questions as best you can. If you don't know the answer to a question, just go with the default and press Enter.

When you're done, press Cntrl-Alt-F7 to get back to graphical mode and then Cntrl-Alt-Backspace to reset the X server (so your changes can take effect).

---

### Post by samasaur on 2007-06-22
Do I type that code in the terminal?

---

### Post by Crafty Kisses on 2007-06-22
> **samasaur said:**
> Do I type that code in the terminal?

You sure do. :D

---

### Post by Crafty Kisses on 2007-06-22
> **samasaur said:**
> Do I type that code in the terminal?

You also want to know how to install the ATI Drivers right?

---

### Post by jdmrsx05 on 2007-06-22
Yes, type that from the terminal.  Good luck, let me know the results because I'm thinking about getting an X1600.

---

### Post by samasaur on 2007-06-22
I don't think I do anymore. Can you give me a step by step to install the ATI drivers?

---

### Post by Crafty Kisses on 2007-06-22
> **samasaur said:**
> I don't think I do anymore. Can you give me a step by step to install the ATI drivers?

Sure, this link may be really helpful too you:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by samasaur on 2007-06-22
I have a bit trouble following the steps to that link you just gave.

Build Ubuntu packages from the installer by opening a terminal, entering the directory that you saved the installer to, and running bash ./ati-driver-installer-<version>.run --buildpkg Ubuntu/feisty

where <version> is the version number of the driver you downloaded. This will take a short time. After finishing, the installer will create several debs. Use the command "dpkg -i <filename>" to install the fglrx-kernel-source<something>.deb and the xorg-driver-fglrx<something>.deb. The other two debs created will be fglrx development headers which you probably will not need and the AMD Control Panel which doesn't work.

Could you explain what I'm suppose to do there. I saved the driver from ATI to my desktop in an untitled folder. I'm fairly new to Ubuntu so I don't know a whole lot. Sorry for the troubles

---

