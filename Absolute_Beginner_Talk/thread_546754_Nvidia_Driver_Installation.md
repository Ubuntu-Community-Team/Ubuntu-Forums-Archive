---
title: "Nvidia Driver Installation"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by capera on 2007-09-09
Ok....I'm as new as they come. 13 years Windows experience and just discovering Linux.

I am running ubuntu

I went to the Nvidia site and got the lates drivers for my card (GeForce2). They gave me a = NVIDI…nux-x86-1.0-7184-pkg1.run.    file

When I try to execute it.... I get this error   =  

Could not open the file /home/dave/Desktop/NVIDI…nux-x86-1.0-7184-pkg1.run.


Any suggestions?

---

### Post by forestpixie on 2007-09-09
It's easier to install the nvidis driver from System > Admin > Restricted Drivers

---

### Post by mikewhatever on 2007-09-09
One of the very convenient ways to install the nvidia driver is envy [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
If, for some reason, you have to install it manually, try this [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
Lastly, there is the restricted drivers manager in Feisty, that is in case you use this version, of cause.

---

### Post by capera on 2007-09-09
> **mikewhatever said:**
> One of the very convenient ways to install the nvidia driver is envy [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
If, for some reason, you have to install it manually, try this [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
Lastly, there is the restricted drivers manager in Feisty, that is in case you use this version, of cause.

I ran this program and it all installed. I did get some message after re-boot about a driver that was not completely supported by ubuntu........but the video seems to be working much better.

thx  :)

Now I need to get my VIA 4in1 drivers installed.

Linux sure runs well...... seems better than Windoze

---

### Post by forestpixie on 2007-09-09
> Linux sure runs well...... seems better than Windoze :) did for me

Glad you got video sorted - might be worth looking at the [wiki]("http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu") for when you have to upgrade or kernel upgrades happen.

What are the other drivers you're trying to install?

---

### Post by mikewhatever on 2007-09-09
Nvidia drivers belong to Nvidia. They are closed source and are supported entirely by the company.

---

### Post by tripokey on 2007-09-09
Don't think you need the via4in1 driver.... Most of the time you don't need to install additional drivers in Linux.

---

### Post by alienexplorers on 2007-09-09
Just use the ENVY script and it will install your drivers for you.

---

### Post by therunner on 2007-09-09
why will my screen resolution not stay where I want it?  I have Dl'd the latest Nvidia drivers and I adjust my monitor to 1440x900 and it automatically changes it back to 1024x768.  Actually, anything greater than 1024x768 will revert back to 1024x768 after logging out and then back in.  If I adjust it and don't log out it's fine and will not revert back to the 1024x768 setting.  I have saved the setting in the xconfig file but I think I may not be setting the correct parameters. 
I have a samsung940bw. [http://www.samsung.com/ca/products/monitor/lcd_digital/ls19hawkbqxaa.asp?page=Specifications](http://www.samsung.com/ca/products/monitor/lcd_digital/ls19hawkbqxaa.asp?page=Specifications)

---

### Post by alienexplorers on 2007-09-09
therunner try adding a modeline to force the mode you want.  You just add it to the monitor section of your xorg.conf file.

---

