---
title: "Failed to start the X server (Non ATI card)"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by opqosite on 2007-07-05
Hi, ubuntu was acting up on an older computer, so I installed it again on another computer I had laying around. I get this message upon attempting to boot up:" Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?"


I looked this error up, and what I found was that it was due to newer ATI cards not being supported by the open source driver...or something like that. But I have an Intel Extreme 3D graphics card. So is there any way to solve this?

Specs on the compy:

CPU: Intel® Celeron® 2.60GHz Processor 128KB L2 cache & 400MHz FSB
Chipset: Intel® 845GV chipset
Memory: 256MB DDR (PC 2100)
Hard Drive: 250GB Seagate Barracuda HDD
Optical Drive: 	48x Max. CD-RW Drive; 16x Max. DVD Drive; 3.5" 1.44MB FDD
Video: 	Intel® Extreme Graphics 3D
64MB Shared memory
Sound: 	AC '97 Audio

---

### Post by cleverselfreferentialname on 2007-07-05
Hit ctrl+alt+F1 and log in on a TTY. Then run 'sudo dpkg-reconfigure xserver-xorg' and select 'i810' (I think) as your graphics driver. Then reboot or run 'startx'. Good luck.

---

### Post by opqosite on 2007-07-05
ok sorry im a total noob at this. how exactly do i do this? it asks for a password and i have no idea what it is.

---

### Post by opqosite on 2007-07-05
I log in under the username and password i created during setup, and it seems to work. I type in sudo dpkg-reconfigure xserver-xorg and it asks for a password. I tried typing in the password that I used to log in, but it doesn't work. Any suggestions? Please break down this process step by step for me. Thanks.

---

### Post by moredhel on 2007-07-05
if you mean that the password doesn't show up, it shouldn't. just type it in and press enter :)

---

### Post by opqosite on 2007-07-05
Yeah, I ghost-type it in. But it asks for the password again. So, I guess its wrong.

---

