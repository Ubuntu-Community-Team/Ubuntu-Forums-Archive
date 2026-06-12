---
title: "Not A Neotype but new to Linux - need direction"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by linuxman1 on 2007-04-21
Was fairly impressed with Ubuntu 6.10 and even more so with 7.4 .  While the main hardware was recognized without difficulty, some of the other devices need to be setup and I am having some difficulty trying to navigate the necessary processes.  Before I ask specific questions let me describe the system hardware:

**User built system**:
P4 Case (with original PSU removed 
3 system fans + dedicated harddrive and DVD fans.
Antec TruePower 2.0 480W PSU
AMD Athlon64 x2 (AM2) 3500+ (retail ... fan and heatsink)
Gigabyte GA-M55Plus-S3G Motherboard (retail ... onboard Geforce 6100 and Realtec HD Audio)
Geil Ultra DDR2 PC6400 (Dual Channel) ... 2 x 512MB
Hitachi PATA 7200rpm 160GB Hard Drive
Pioneer DVD-WR (x16)
Floppy Drive
Logitech MX-Laser Mouse
Modware PS/2 Keyboard
Magview 17" CRT
Brother HL-2040 LaserJet
Epson Perfection 1260 Flatbed Scanner
Cambridge 5 piece Audio Speaker Set
Brother MFC-5440CN (connected over DSL Broadband)
LAN Home network via 2Wire DSL Modem Router.

No problems with the basic install but Scanner and Printers not initialized.  Through System->Administration->Printing, I was able to initialize the Brother HL-2040 Laserjet by selecting the HL-2060 driver from the dropdown list (as was suggested in a forum reference I had come across).

I know that Brother is actively developing Linux drivers for many of its hardware devices.  So my first set of questions are:
**Q#1**:  Brother has the devices listed under several categories and sub categories so which ones are applicable to Ubuntu?
CUPS vs CUPSWrapper
**Q#2**: It seems that the CUPSWrapper is the appropriate choice.  Is this correct?

**Q#3**: What type of CUPS Wrapper should be selected? Debian (DPKG) or SUSE, etc. (RPM)

According to Brother's website you first need to download and install LPD (LPR) before you can install the CUPS Wrapper driver.  
**Q#4**: Is this still the case with Ubuntu 7.4?

The install instructions require that you logion at the command prompt as root (or issue the SU command).  As a security enhancement Ubuntu requires that you login with a separate userid and password (has admin privileges).  
**Q#5**: From the desktop, what do I need to do to login as root (or issue the SU command with proper validation? 

The Brother MFC-5440 Inkjet/fax/scanner is deteced as a node on the LAN.
**Q#6**: Would I accept the "Detected" type or do I select the "Network" type if using the printing install utility?

Assuming that I can find an appropriate driver for the Epson Scanner, 
Q#7: What Option under the System Menu would I use to install the scanner?  Is there also a command string that must be executed to initialize the scanner or is the whole process handled through a GUI?

The above are of primary concern but I do have one more question.  The system seems a bit slow.  
**Q#8**: Are there some system tweeks that can be applied to improve performanace (such as recognizing that DDR2 800Mhz memory is in use).

I realize that some of these may not be considered "New User" type questions so if appropriate please direct me to a suitable forum.

---

### Post by BoneKracker on 2007-04-21
When you start to add printers, ubuntu should set up cups for you automatically.  LPD/LPR is the old print system, which you probably don't want to use (CUPS, although bloatier, has modern features most people want, such as IPP).  

I'm not familiar with CUPS wrapper, but it sounds like something to let systems that assume you have LPD/LPR to use CUPS (or vice versa) which you should not need, _unless_ the brother device you are using is trying to tell you it can only work with LPR/LPD.  You'll need to consult someone else or google CUPS wrapper or something on that one.  Sorry.

Ubuntu is a distribution of Debian; it uses the "DPKG" (deb) package format.

Ubuntu doesn't set up a root user by default.  In theory, this makes it more secure.  Instead, it automatically gives the first user what a Windows user would call administrative privileges.  In short, if you want to issue a command as the root user, just make "sudo " the first word.  For example, if you want to edit a file of your own using the editor "nano" you just type ```
nano /somedirectory/somefile
``` but if you want to edit a file that you do not have write permission on (like, say /etc/fstab), then you type ```
sudo nano /etc/fstab
```

"su root" essentially turns your user into root until you type "exit", but it requires that you do in fact have a root user.  "sudo <command>" does not require that you have a root user.  Until you know more about it, stick with the default and continue using sudo, you can add a root user later if you want.

Not sure I understand what you are describing wrt to the other device.  If it's connected via LAN, I would go with the "network" option (unless it's obviously already detected the device properly as a device that's on the network).  If it's connected directly (e.g., usb) then I'd go with detected.

If you have problems with the graphical interface that's built into the sytem, CUPS provides a web-based interface that I've found to be pretty good.  You might find an icon for it already set up for your use under the menus somewhere (looks a big green/black C or something).  Also, there should be a full set of HTML documentation for CUPS right on your computer (probably in /usr/share/doc/cups....) unless ubuntu chose not to include it, in which case you can view it on the CUPS website.

As to speed, yes there are many things you can do to speed up the system.  Get it stable and functioning first.

[Edit]: oh, and there should also be some somewhat more abbreviated documentation in the cupsd man page.  (In terminal type "man cupsd".)  Actually, you might as well learn how to use man.  Start by typing "man -k cups" (that will list all the man pages that seem to have something to do with cups).  Then you can choose from that list and type in "man cups" or "man lpd" or whatever you fancy.

---

### Post by kiran_aryan on 2007-04-21
> Q#5: From the desktop, what do I need to do to login as root (or issue the SU command with proper validation? 

Instead of logging in as root, enter commands with a "sudo" prefix.
eg: sudo gedit /etc/X11/xorg.conf

---

