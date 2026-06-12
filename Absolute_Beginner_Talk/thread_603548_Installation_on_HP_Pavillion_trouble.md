---
title: "Installation on HP Pavillion trouble"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by YetiMachete on 2007-11-05
Hi my name is Kyle and I am new to Ubuntu. However I'm pretty computer inclined but not with Linux lol. I have a problem installing Ubuntu 7.10 on my HP Pavillion dv9005us laptop. It runs through the installation and when it's about to load the GUI the system hangs and I have to restart. Sometimes when it is initializing the hardware or even the system modules, the system will stall. Is my system simply not compatible with this operating system? I've tried recovery, reinstallation, even running off the LiveCD. Even then with the LiveCD, the system will not boot up to the login screen. Can anyone help me?

My system specs are

HP Pavillion DV9005us Notebook PC
Currently running Windows XP Media Center Edition
1.5 GB RAM
100GB SATA HD
Nvidia Geforce Go 6150 Graphics
Nforce Network Adapter
D-Link Wireless USB Adapter (my Broadcom internal card is toast.)
17'' Widescreen Display with Brightview
DVD-R/RW w/ Lightscribe
AMD Turion64 x2 Mobile Processors

Any additional info please email me
Thanks for all your help and time!

---

### Post by sailor2001 on 2007-11-05
do you have the 64 live disk?  Also you may try downloading the 64 alternate disk

---

### Post by Inxsible on 2007-11-05
> **sailor2001 said:**
> do you have the 64 live disk?  Also you may try downloading the 64 alternate diskEven if he has a i86 CD it should work, since his processor is capable of handling both. But trying the alternate CD seems good advice.

---

### Post by smurphy_it on 2007-11-05
Here are a couple of threads you can look at, but sounds like you need to shut off acpi on boot or use the alternate cd (text based installer).

[http://ubuntuforums.org/showthread.php?t=528618]("http://ubuntuforums.org/showthread.php?t=528618")
[http://ubuntuforums.org/showthread.php?t=431815]("http://ubuntuforums.org/showthread.php?t=431815")
[URL="http://ubuntuforums.org/showthread.php?t=512059"]http://ubuntuforums.org/showthread.php?t=512059
[/URL]

---

### Post by YetiMachete on 2007-11-05
ok, so if I use the alternate cd, how do I install it from text? can I shut off the acpi in the bios?

---

### Post by smurphy_it on 2007-11-06
You can install it from the liveCD if on the bootup screen you edit the boot command and type noacpi
then install as usual.

Or download the alternate cd, and but it... It's totally text based installer.

---

