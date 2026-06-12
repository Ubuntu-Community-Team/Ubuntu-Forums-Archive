---
title: "Black screen in Ubuntu 14.01 after software update, Macbook Pro"
date: 2014-09-17
forum: Apple Hardware Users
---

### Post by dcnicholls on 2014-09-17
[apologies in advance for cross posting with the Parallels forum, but this group seems more active]

I have Ubuntu 14.04.1 installed as a virtual machine on my 2011 Macbook Pro, on Parallels 9.0.24251. I downloaded the Ubuntu iso file from the Ubuntu site 2 weeks ago. It works perfectly. However, in the normal process of using 'sudo apt-get update' [not 'upgrade'], and the GUI sofware update app, Ubuntu downloads a lot of stuff that is more recent than the install iso. When I reboot the VM after the update, the login screen is normal, but after loading the GUI, any new window gives a black screen (with dashes and lines in some cases). All the dock applications generate black screens, although the dock icons themselves are normal. Same is true for the menu bar controls.

The MBP has a Radeon 6770m/Intel hybrid graphics set up. So I presume Ubuntu has downloaded the wrong graphics driver (because the black screen effect seems to be intrinsic to hybrid graphics systems), but it's not clear which of the update files is causing the problem.

I checked the "Additional Drivers" option and there is nothing available, but I suspect Parallels has its own drivers which are being damaged by the Ubuntu update.

I did the system test suite and the grapgics driver version test reported the following:

ERROR: No video driver loaded! Possibly in failsafe mode! 
------------- VIDEO DRIVER INFORMATION ------------- 
------------- HYBRID GRAPHICS CHECK ---------------- 
Graphics Chipset: Unknown (1ab8:4005) 
Loaded DDX Drivers: prlvideo 
Hybrid Graphics: no 

The prlvideo DDX reference suggests it's Parallels doing the video, in which case Ubuntu should not interfere, or there should be a way to reinstall the Parallels driver. Is there?

Is there a way around this problem?

---

### Post by dcnicholls on 2014-09-18
Solved.  Here's how to do it.  Before you do the software update:

1. close Ubuntu 
2. In the Parallels Ubuntu window Virtual Machine > Configure > turn off 3D acceleration
3. Start Ubuntu and log in (the graphics may be a bit sluggish)
4. Do the software update using Software updater
5. Restart Ubuntu after the update

Now it should be working (no black screens) but with sluggish graphics

6. Shutdown Ubuntu
7. In the In the Parallels Ubuntu window Virtual Machine > Configure > turn **ON** 3D acceleration.
8 Restart Ubuntu and log in.

It should now be working.

For further information (and where I got the recipe from) see [http://askubuntu.com/questions/404589/ubuntu-13-10-macbook-air-mavericks-parallels-9-black-screen](http://askubuntu.com/questions/404589/ubuntu-13-10-macbook-air-mavericks-parallels-9-black-screen)

---

### Post by morganamona on 2015-02-01
thank you it working

---

