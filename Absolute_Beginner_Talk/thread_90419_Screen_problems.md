---
title: "Screen problems"
date: 2005-11-14
forum: Absolute Beginner Talk
---

### Post by gazruss on 2005-11-14
Hi there folks.
I posted this in the hardware forum, but i think it is more of a noooobie issue.
I installed linux, and at first had a lot of problems getting the screen to a usable size/res. (it defaulted to 1024x768) after configuring the driver i managed to run at 1400x1050 which fills the screen nicely. BUT now when i get to the gui boot in where i used to be able to choose between KDE & Gnome, i have a huge black band in the center of the screen, and the boot screen is split right up the middle. Problem is the options are on the side outside the screen. I can scroll to the left and right, and see the cursor go across the screen (a bit like the old Pac-Man game) but can't get into KDE....

Any help would be really appreaciated

---

### Post by ecobuntu on 2005-11-14
Crazy...you might want to try to reconfigure xorg
sudo dpkg-reconfigure xserver-xorg
I've had some issues with wierd stuff and X.  Good luck!

---

