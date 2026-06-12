---
title: "Help installing NVIDIA 169.07 drivers (Kubuntu, Edgy Eft)"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by person_99 on 2008-01-09
I am having some trouble installing the latest Nvidia drivers for a Geforce 6200 (256mb DDR2) on Edgy Eft. I installed GTA San Andreas via wine, but it runs extremely slowly even though my computer is much better then the recommended, and people on the GTA forums told me to update my Nvidia drivers.
(Sorry if this is the wrong forum)
I currently have the 100.14.19 drivers, trying to upgrade to 169.07.

When I start the installer with: Sudo sh NVIDIA-Linux-169.07-pkg1.run, it tells me that it can't be installed while the X server is running.
I did /etc/init.d/kdm stop
It sat at an  empty kubuntu loading bar for a minute, then went to a strange console-like thing where I could type things in, but whatever I typed did nothing.

What am I doing wrong?

Edit: Not pressing CTRL + ALT + F1  at the empty line to get it going.
Problem solved.

---

### Post by Shazaam on 2008-01-10
Did you download the drivers to your desktop?
Try this.
When you are at your normal desktop hit control+alt+f1 which will bring you to a prompt. Go ahead and login. Once you are logged in type in cd ~/Desktop (capitol D), then type in ls to make sure the drivers are there.
Then type in sudo /etc/init.d/kdm stop
This will stop X.
Then you can do sudo sh NVIDIA-Linux-x86-169.07-pkg1.run.

---

### Post by Raptor45 on 2008-01-10
Might be a bit easier.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by person_99 on 2008-01-10
> Then type in sudo /etc/init.d/kdm stop
This will stop X.
Then you can do sudo sh NVIDIA-Linux-x86-169.07-pkg1.run.

That is the thing, I CAN'T do Sudo SH anything once I get to the command line. I can't do anything, It is a black-screen white text, it lets me type things, but when I press enter all it does is go to the next line.
What is going on?

---

### Post by person_99 on 2008-01-10
Bump

Edit: Solved.
Turns out all I had to do was press CTRL + ALT + F1 to get the line working.

---

