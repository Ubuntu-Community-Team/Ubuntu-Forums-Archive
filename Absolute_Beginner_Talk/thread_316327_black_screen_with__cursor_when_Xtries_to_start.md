---
title: "black screen with  cursor when Xtries to start"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by saintj0n on 2006-12-10
Hi.I am trying to get my nvidia geforce FX4000 working on my computer. It worked at 800x600 before but I tried to change it to 1024x768; which totally screwed the configuration. I ran nvidia-glx-config and enabled it. It tries to load the X window and immediately starts giving error messages.

If anyone understands these error messages or knows how I can get my nvidia card to work, please help!!


Here is the relevant stuff from /var/log/Xorg.0.log:

(--)Chipset NVIDIA GPU
(ww)NVIDIA: No matching device section for instance (BUS ID PCI:0:5:0) found.
(EE)NVIDIA(0): Failed to initialize the GLX module; please check in your X log file that the GLX module has been loaded in your server and that the module is the GLX module.
If you continue to experience problems, Please try reinstalling the driver
(EE)NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure that there is a supported NVIDIA GPU in this system and that the NVIDIA device files have been created properly.


(EE)Screens found, but none have a 
usable configuration
Fatal server error:
no screens found

Thanks!

---

### Post by useResa on 2006-12-10
What you indicate seems very similar to something I have also experienced with my Nvidia driver.

I got it solved by the explanations that were given in [this thread](http://www.ubuntuforums.org/showthread.php?t=293014).
Maybe this can help you to.

---

### Post by saintj0n on 2006-12-12
Okay...well at least I got some different errors this time. But it still didn't work. I do not understand why this is so difficult. It was working great in 800x600! I would switch back but I unwisely didnt make a backup before I hacked up my xorg.conf...Poor foolish newb ;)

Isn't there a utility out there for someone who wants to automate GLX configuration? I tried automatix2 but it didn't help.

How aggravating:evil:

---

