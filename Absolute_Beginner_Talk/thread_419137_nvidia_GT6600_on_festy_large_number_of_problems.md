---
title: "nvidia GT6600 on festy large number of problems"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by barmazal on 2007-04-22
I'm new to Ubuntu, somehow i got to Envy using 6.10 but on Festy i cannot to a thing tried different methods but i end up with xorg blue screen each time i try new methods.

I have Leadtek GT6600 and LG Flatron  F700p screen.

Methods i've used, right after install and setting up internet i've enabled restricted hardware, it downloaded a file and all was fine except Refresh rate which supposed to be 85hz but i couldn't change it via Gnome since it shown no such resolutions in menu or via xorg.conf which always gave me an error after restart.

Envy beta and Automatix destroyed my system automatically without me messing with xorg file.

My question is how do i set it this exact card from scratch, i want to use ?Ubuntu and i'm looking forward for Ubuntu Studio + helping as i can to it but this Nvidia issue is frustrating because i know some experienced users can easily modify files back and i can't even do delete file or change name outside of GNOME, when i'm always outside of it right after getting blue screen xorg error.

+ Ubuntu does not give me to run my Windows resolution and refresh rate settings keeping the screen stretched.


Thanks, if someone gives me step by step tutorial and best method which gives me my Windows Resolution and Refresh Rate 1152x864 85hz without adjusting screen manually each time i log into different system

---

### Post by wh0rd on 2007-04-22
To reconfigure xorg from the command prompt you can: 

sudo dpkg-reconfigure xserver-xorg



Have you tried this guide:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Graphics_Driver_.28NVIDIA.29)

---

### Post by barmazal on 2007-04-22
problem is sudo dpkg-reconfigure xserver-xorg asks me questions i have no answers to them, like how i call my monitor. Should i give random name or just type what i guess it is.


in xorg.conf there are few lines like vertial and horizonal rates or something like that, i have no clue which one means refresh rate and other one other thing, if at all.

---

### Post by barmazal on 2007-04-22
it says x version is 1.0-9631 and Nvidia 1.0-9755 what should  i do ?

---

### Post by Tux Aubrey on 2007-04-22
> Envy beta and Automatix destroyed my system automatically without me messing with xorg file.

:lolflag: Yes, its much easier to have a script or program destroy your system than fiddle about with the command line.  Same happened to me on a fresh install of Feisty on a machine with a Geforce 6600 series card and a BenQ monitor capable of 1920x12000 res:

The install was fine but I was unable to access the higher resolution with the standard "nv" driver.

The inbuilt restricted driver manager left me unable to start X because certain modules would not load.

Envy installed the wrong version of the nVidia driver with the same result.

Eventually, after a day of useless tweaking, I "sudo apt-get --purge" 'd everything to do with nVidia, removed then reinstalled the restricted kernel modules and tried the in-built restricted driver manager again.

Voila! it worked - except that 1920x1200 woud not "stick" - ie it reverted to 1600x something everytime I restarted X.  (I have previously found that "save settings" on the nVidia settings manager doesn't).  The fix was simple - use the Screen Resolution dialogue under System-Preferences and check the "use as default" box.

Good luck.  This is the first time I have found the third party products (Automatix and Envy) exacerbate or confuse a problem.

---

### Post by barmazal on 2007-04-22
how do i purge all the stuff from command line?

---

