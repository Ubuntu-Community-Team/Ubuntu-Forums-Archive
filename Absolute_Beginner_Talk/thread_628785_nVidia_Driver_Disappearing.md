---
title: "nVidia Driver Disappearing"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by GGLucas on 2007-12-01
Ok, I have a small problem, I'm running gutsy (regular ubuntu), I have an nVidia card so I installed the restricted drivers (didn't work at first, so I used Envy and it made it work), got compiz working, succesfully managed to play Team Fortress 2 through WINE, and StepMania natively, all without a hitch. Then, yesterday, I decided to try out Xfce, so I apt-get'ed the xubuntu-desktop metapackage, tried it out, was unable to do some things I wanted to do, so logged back into GNOME. Nothing has changed for me, Compiz is still working and being pretty as always, except for one thing, whenever I run either of the two games I successfully played before, it crashes, saying "Your system is reporting that direct rendering is not available. Please obtain an updated driver from your video card manufacturer.". So, I checked some more things, and nVidia settings reports that the driver is not being used, and I should run nvidia-xconfig (tried that, restarted X, still says the same thing), I also tried running Envy again, but after a reboot, still the same. It also reports that it is enabled and in use in the Restricted Drivers manager, and it has to be, because I'm still on 1280x1024, and Compiz is still working. What do I do ? XD 

(Oh, one thing I also noticed changed since I tried xubuntu was that when logging in, the cursor changes into a cross shaped X for a second until it goes to normal and gives me my usual desktop.)

EDIT: Okay, solved it, removing the xserver-xgl package solved all the problems.

---

### Post by GGLucas on 2007-12-01
Okay, this is weird, logging into the GNOME Failsafe session makes the drivers be recognised again :confused:
That must mean it's somewhere in my startup scripts, what else are the exact differences between a regular GNOME session and the failsafe one?

---

