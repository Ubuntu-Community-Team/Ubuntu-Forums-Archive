---
title: "Kagoole"
date: 2005-12-10
forum: Absolute Beginner Talk
---

### Post by kagoole on 2005-12-10
Please help,
I have just spent the last week trying to load breezy 5.10 in expert,server & basic mode, the only one that will load is basic which gives me the command line and as I'm a newbie this is not much help.
The program loads ok including the grub loader all of the modules are loaded except hotplug system, when the progress bar is almost complete the system crashes so no GUI. I have tried changing almost all of the variables in bios without any progress, I have disconnected, printer, scanner and removed my sound card.
My processor is a p4/2.8 gh  motherboard;Asus,P4C800;added additional Hd to accomodate new o/s. Tried loading Mandrake, comes up with the same fault so I suspect the problem is my pc. What am I doing wrong!!!!!!!

Frustrated beyond belief.

---

### Post by davmac on 2005-12-11
Sounds like some problem starting X. Do you see any error messages flash by? If you have a look at the file /var/log/Xorg.0.log, can you see anything there that points to what the problem is?

You can do this by opening a terminal and typing "gedit /var/log/Xorg.0.log" and the case you enter DOES matter.

Hope this helps,

Dave Mac

---

### Post by kagoole on 2005-12-11
Dave, 
Many thanks for your reply.
The only way I can get to the program is from the grub boot loader and using "Ubuntu, kernel 2.6.12-9-386 ( recovery mode) this eventually allows me to log in as root.
I tried all ways to enter your comand line making sure to use upper case where required and all I got back was "no such file or directory"
If I type in startx the system then crashes and I then have to reboot.
Any other ideas????
kagoole

---

### Post by kagoole on 2005-12-11
Dave,
I have resolved my problem, my monitor is both digital and analog and I only had the digital connection to my pc pluged in, when I plug in both analog and digital cables the system comes up ok, so now I can get started on exploring what linux has to offer, once again many thanks for your help.
kagoole

---

