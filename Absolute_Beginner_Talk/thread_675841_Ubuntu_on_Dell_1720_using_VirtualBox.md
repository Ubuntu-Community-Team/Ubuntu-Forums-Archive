---
title: "Ubuntu on Dell 1720 using VirtualBox"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by grimerking on 2008-01-23
Hi Everybody, 

Maybe I'm trying to run, before I can walk... However, I've recently bought a Dell 1720 laptop. The specs are: 

C2D 1.67GHz
2GB RAM
250GB HDD
GeForce 8600m GT
1920x1200 screen

I've uninstalled Vista and installed XP-SP2. Everything is running well in Windows. 

I've tried Ubuntu before on my desktop, but could never get dual monitor to work. I read an article in a UK magazine 'PCPro'. They had a basic guide on how to set up VirtualBox and install Ubuntu. The installation went OK and I fully updated Ubuntu. 

The only problem was the screen resolution. The maximum available was 800x600. I went into the settings and changed the screen to something like 'generic lcd 1920x1200'. Ubuntu prompted me to log off and on again. I did this and the log-in screen  is now corrupted and I can't make anything out. 

Strangely, when Ubuntu is booting, it actually boots at 1024x768 without any problems. 

Is there a command that I can use to reset the graphics to default? and then set it use 1280x1024 or (preferably 1440x900 or 1680x1050)? 

My desktop colour depth is 32-bit in Windows. I have tried changing it to 16-bit, but this didn't make any difference to the corruption. 

Do I need to install the nVidia linux drivers before i can use resoltions above 800x600? If so, why does Ubuntu boot using 1024x768? 

If anybody can help me out, I'd really appreciate it. 

Thanks, 

Rob

---

### Post by Dekunuts on 2008-01-23
when you boot ubuntu, you have 2 seconds to see the grub menu entries (escape shows them) . boot recovery mode and you will have a working command line system without messed up screen. Then you can type sudo dpkg-reconfigure xserver-xorg to reconfigure X or just sudo nano /etc/X11/xorg.conf and change the config file yourself. If you want resolutions higher than VGA you need to install guest additions in virtualbox.

that should help you a bit.

---

### Post by grimerking on 2008-01-23
Hi, 

Sorry, total noob. What does "reconfigure X" mean? Is that the default display driver? 

If I want to manually change the cofig file, what should I change it to? 

What is 'Guest Additions'? 

Thanks, 

Rob

---

### Post by kpkeerthi on 2008-01-23
When running Ubuntu or any other OS as guests in VirtualBox (and other VMs), the guest OS will NOT be able to see and use your host machines Nvidia card and its 3D capabilities. 

To fix the resolution, you need to install VirtualBox Guest Additions. See [http://ubuntu-tutorials.com/2007/10/13/installing-guest-additions-for-ubuntu-guests-in-virtualbox/](http://ubuntu-tutorials.com/2007/10/13/installing-guest-additions-for-ubuntu-guests-in-virtualbox/)

Then (Re-)boot ubuntu in recovery mode, and type ```
dpkg-reconfigure -phigh xserver-xorg
``` and choose the resolutions you want. Reboot ubuntu normally.

---

### Post by grimerking on 2008-01-23
Brilliant! 

Thanks for your help. I'm at work at the moment, but will attempt it when I get home. 

Rob

---

### Post by grimerking on 2008-01-23
Hi, 

I tried what you said and my screen is now back to normal. However, I can't select a higher resolution monitor or change the desktop resolution. 

If I go into the screens and graphics section, I can select other monitors and get a resolution of 1024x768  to test correctly. When I click OK, it just reverts to 'Plug and Play' and only gives me the choice of 800x600 or 640x480. 

This is really doing my head in. Any ideas? 

Rob

---

### Post by kpkeerthi on 2008-01-24
> **kpkeerthi said:**
> 
To fix the resolution, you need to install VirtualBox Guest Additions. See [http://ubuntu-tutorials.com/2007/10/13/installing-guest-additions-for-ubuntu-guests-in-virtualbox/](http://ubuntu-tutorials.com/2007/10/13/installing-guest-additions-for-ubuntu-guests-in-virtualbox/)

Then (Re-)boot ubuntu in recovery mode, and type ```
dpkg-reconfigure -phigh xserver-xorg
``` and choose the resolutions you want. Reboot ubuntu normally.
Well... this was exactly what I did to my xubuntu running in VirtualBox to fix the resolution. 

You may try this:
1. Reinstall guest additions. 
2. Run **dpkg-reconfigure xserver-xorg** in recovery mode. 
3. Select "vesa" for driver and the resolutions you would like. Leave the rest default. 
4. Reboot normally.

---

