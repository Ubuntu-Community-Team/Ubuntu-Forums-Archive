---
title: "Ubuntu loads but won't accept keyboard input"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by NetworkDr on 2006-08-17
Pentium 4, 3Ghz
512Mb RAM
Diamond Multimedia video (S2 ViRGE chipset)
Generic NIC
120Gb HDD

I just want a LAMP Server.

Ubuntu seems to load fine. It goes through all the steps for setup (in VGA mode) and then reaches the point where I remove the CD and reboot to launch Ubuntu.

Upon startup, all appears fine but it comes to a command prompt only ( <hostname> login: )and won't accept keyboard input.

I wouldn't have any problem working from the command prompt to fix the bugs in my video but why can't I type anything to the screen?

No obvious errors on bootup....no issues during setup....WTH?

Al
:confused:

---

### Post by zxee on 2006-08-17
Have you tried Alt+Ctrl+F1 ? That should open up an alternate shell.
If you can't type in that either though my best guess is that your keyboard never got configured. If you can use a live cd you could navigate to your ubuntu install and edit /etc/X11/xorg.conf

---

### Post by NetworkDr on 2006-08-17
Bam!!
I had tried the various keyboard shortcuts and such that I had scoured from this and other forums, to no avail.

Just finished loading Ubuntu on a different system, no problems arose, keyboard worked fine, login worked fine.

Restarted the 'bad' system, opened up the CMOS Setup page and selected "Load Fail-Safe Defaults". 

The system came up and Voila!! keyboard input accepted!

Incredible. What a weird PITA.

Thanks for the help, folks.

Al

:D

---

