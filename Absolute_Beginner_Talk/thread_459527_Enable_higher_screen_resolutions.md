---
title: "Enable higher screen resolutions"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by mep916 on 2007-05-30
How do you enable higher screen resolutions? My monitor (Sony 17" LCD)  is capable of resolutions as high as 1280 X 1024; however, Ubuntu will only allow me to go as high as 1024 X 768.

My video card is an Nvidia GeForce FX 5500. I believe I correctly installed all necessary drivers.

Thank You!

---

### Post by taurus on 2007-05-30
Have you installed nVidia driver for your graphic card?  If you are running Feisty, here is how.

[http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia)

---

### Post by mep916 on 2007-05-30
Yes. I installed the "nvidia-glx new" driver. I also installed the 3D Acceleration driver.

---

### Post by alienexplorers on 2007-05-30
In Nvidia-settings don't you have the option to make your screen bigger.  Remember to run Nvidia -settings in SU mode for the changes to take.

---

### Post by Brightbelt on 2007-05-30
I posted this for someone else because it worked for me. I have an ATI, however, but it may still work for you. The Vesa driver referred to is, I understand a common driver, so it may work.

...""Instead of telling you what to do, I'd rather tell you that this is what I did and what worked for me. 

-I rebooted and went into the recovery mode...
- at the prompt I entered 'dpkg-reconfigure xserver-xorg' 

Then the text-based graphics reconfiguration wizard came up...Here it gets trickier, because you have a different brand card, but here's what I did:

-I was (correctly) instructed to choose 'Vesa' for the driver (this is the first menu you encounter)
-From there I chose all of the defaults, or as many as I could
- find out from your screen display in XP which resolutions are really available and that they work, and then choose these (with your space bar) when you get to that part of the wizard;
-For the X.org Server Modules, I enabled all of them except 'glx'
- You'll want to enter your specific Horizontal Freq. rate and your Vertical refresh rate towards the end. You can find these in your monitor's manual. 
- Then when you're finished with the wizard, do 'sudo reboot' "".....

Good Luck, Frank

---

### Post by daimaru on 2007-05-30
i would suggest u first check ur /etc/X11/xorg.conf file.
open it by typing in console:
```
sudo gedit /etc/X11/xorg.conf
```
go to the display section and check that "1280x1024" is in the line with all the display opts.
if your xorg.conf display section starts with 1024x768 or somthing else then u should paste "1280x1024" before every line (1-24..... depth)
save and restart xserver (ctrl+alt+backspace)

---

### Post by mep916 on 2007-05-30
> **daimaru said:**
> i would suggest u first check ur /etc/X11/xorg.conf file.
open it by typing in console:
```
sudo gedit /etc/X11/xorg.conf
```
go to the display section and check that "1280x1024" is in the line with all the display opts.
if your xorg.conf display section starts with 1024x768 or somthing else then u should paste "1280x1024" before every line (1-24..... depth)
save and restart xserver (ctrl+alt+backspace)

Cool! I simply edited the file, rebooted, and Ubuntu automatically switched my resolution to 1280x1024.

Thanks everyone for your help!

---

