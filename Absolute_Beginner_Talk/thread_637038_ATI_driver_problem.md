---
title: "ATI driver problem"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by teamkiller87 on 2007-12-10
Greetings all,

I need some help with sorting an ATI driver problem. I downloaded the drivers for my Mobility Radeon X1600 from here [http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html) and went through the installation without any glitches. After I restarted the situation took a turn for the worse namely the environment behaves like I don't have any drivers installed, i get maybe 5 frames a second when I try to scroll down on a page etc. The ATI Catalyst Control Center is installed as it appears in the Applications tab but when i try to run it it says that it appears I either have no drivers installed or the one that are installed aren't properly configured. I haven't the faintest idea how to use aticonfig and furthermore, if I try to run anything fglrx related or even the gears in the terminal my graphical environment restarts sending me back to the login screen.

Help!!! I'm desperate!!

---

### Post by spydon on 2007-12-10
Try to install the ATI driver from System>Administration>Propierty drivers, or something like that my ubuntu is in Swedish :P

---

### Post by misfitpierce on 2007-12-10
Can also google envy ubuntu and visit alberto milones page for envy... helps install ati graphics. Good program

---

### Post by stchman on 2007-12-10
> **teamkiller87 said:**
> Greetings all,

I need some help with sorting an ATI driver problem. I downloaded the drivers for my Mobility Radeon X1600 from here [http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html) and went through the installation without any glitches. After I restarted the situation took a turn for the worse namely the environment behaves like I don't have any drivers installed, i get maybe 5 frames a second when I try to scroll down on a page etc. The ATI Catalyst Control Center is installed as it appears in the Applications tab but when i try to run it it says that it appears I either have no drivers installed or the one that are installed aren't properly configured. I haven't the faintest idea how to use aticonfig and furthermore, if I try to run anything fglrx related or even the gears in the terminal my graphical environment restarts sending me back to the login screen.

Help!!! I'm desperate!!

If you are running Feisty or Gutsy you can simply enable the ATI restricted driver.  You can install Envy:

[http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.9-0ubuntu1_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.9-0ubuntu1_all.deb)

This will download and install the latest ATI driver.  Worked well on my ATI equipped laptop.  This program also works with Nvidia based PCs.

---

### Post by teamkiller87 on 2007-12-10
Okay I installed the driver using Envy and the GDM works fine in all its cubed-desktop and wobbled-windows goodness. YAY!

However, the gdm still restarts whenever i attempt to run any fglrx command in the terminal, like the gears and so on. An quake 3 doesn't work...

And for some reason I still can't access ATI Catalyst Control Center... it still says I have to configure my driver with aticonfig.

---

