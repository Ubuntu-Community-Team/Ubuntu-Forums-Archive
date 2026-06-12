---
title: "xserver fails to start on G4 feisty install live cd"
date: 2007-08-26
forum: Apple PPC Users
---

### Post by Kpax1 on 2007-08-26
I am trying to install a live cd of Feisty Fawn on a G4. It gets to the bootsplash screen, and it looks fine, but then while loading the O/S a garbled display pops up that says:

Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the x server output to diagnose the problem?

Then it goes to a command prompt. In this directory is located the Desktop, what I assume you would boot into on the live o/s, but the gui does not work. I tried dpkg-reconfigure xserver-xorg-core, but when I reboot, the problem persists. Please help.

---

### Post by frog_pilot on 2007-08-27
If you have an ATI-Radeon-Card, look here

[[SOLVED] xserver wont start after 7.04upgrade PPCG4dual]("http://ubuntuforums.org/showthread.php?t=531002")

---

