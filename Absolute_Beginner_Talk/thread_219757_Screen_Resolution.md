---
title: "Screen Resolution"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by iighite on 2006-07-20
Hi,

I have installed UBUNTU 6.06. This is my first time ever using a LINUX type OS... I've been a Windows user for the most of my life except for my first computers were ATARI's :) but they unfortunately don't exist anymore.... but I digress...

Now I know my monitor has a screen resolution of 1280 x 1024 because I have Windows XP on the system and it is on that. Now my UBUNTU screen resolution tool under system preferences is showing only the option of 1024 x 768.  How do I get this to be 1280 x 1024? Is there a way? Or is UBUNTU limited in screen resolution... I hope not...

Oh on another sepreate question... does UBUNTU support dual monitors?

Thank you,

George Hite

---

### Post by Klemik on 2006-07-20
Have you installed graphic drivers ? This should fix screen resolution. 
You can also try to edit your /etc/X11/xorg.conf file, add that resolution and reboot. Its easy so you shouldn't have any problems with adding a new resolution.

---

### Post by iighite on 2006-07-20
I'm sorry I'm new to UBUNTU and Linux... how do I install the graphic drivers, (I thought the setup did it already for me) my graphics card is NVIDIA Quadro FX 3000. Is there a way to find out if they are already installed?

---

### Post by Klemik on 2006-07-20
In 99% you have standard mesa graphic driver card, you should go to nvidia.com and download drivers for linux for your card from there. After downloading run it (in terminal: sudo sh ./drivers.run). Check other posts about installing nvidia drivers.

---

### Post by nalmeth on 2006-07-20
See here:
[http://wiki.serios.net/wiki/Ubuntu_NVIDIA_proprietary_display_driver_installation](http://wiki.serios.net/wiki/Ubuntu_NVIDIA_proprietary_display_driver_installation)

Ubuntu comes with the open-source nv driver, which gives you some 3D, and all the basic 2D you need.

You have to install the NVIDIA proprietary driver seperately --> licensing issues.

---

### Post by iighite on 2006-07-20
Thank you, I will try that. :)

---

### Post by Blondie on 2006-07-20
An easy (some would say lazy) way to install graphics drivers is by using Automatix or Easyubuntu.

[http://www.ubuntuforums.org/forumdisplay.php?f=100](http://www.ubuntuforums.org/forumdisplay.php?f=100)
and follow the links.

Just so you know that this option exists.

They both do a lot more than that so you might want to take a look for that reason as well. IMO they're good both for smoothing out the initial learning curve for newbies and also for doing really quick setups if you reinstall a lot and don't want the tedium of entering lots of stuff to the command line that you've done lots of times before. If your aim is to learn as much as possible and you don't mind expending some time and effort though you might prefer to avoid them.

---

