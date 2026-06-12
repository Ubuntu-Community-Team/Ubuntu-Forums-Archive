---
title: "Installing Ubuntu 7.04: ATI X**** Cards (a noob is born)"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by hamhoks on 2007-08-29
Guys,

I know this stuff must be 2nd nature to a bunch of you but, as an absolute LINUX beginner (with some 18 yrs experience DOS/WINDOWS),  this is just plain intimidating.

I'm out of my comfort zone AND do not want to jeopardize my current WIN XP/VISTA install since, if I screw up, baaaad things might happen that I'm ill equiped to deal with (since I'm so lacking in the LINUX dept).

So, I downloaded the 64bit installer and when rebooting into the CD, the monitor shuts down... Yes, I have an ATI X**** card...

So a pal helps me d/l the text installer version then says that the instruction provided here:
> This quick guide will get Feisty installed and X.org 7.2 up and running.

Boot using PC (Intel x86) alternate install CD for Ubuntu or Kubuntu.
Start text mode installer and install Ubuntu/Kubuntu.
Finish Install and reboot.
Update package list and upgrade any packages needed.

Code:
sudo apt-get update
sudo apt-get dist-upgradeInstall fglrx closed source driver for ATI video cards.

Code:
sudo apt-get install xorg-driver-fglrxUpdate loaded modules.

Code:
sudo depmod -aConfigure /etc/X11/xorg.conf

Code:
sudo aticonfig --initial
sudo aticonfig --overlay-type=XvReboot

Ubuntu 7.04 should now boot into GDM/KDM. 

are only a part of the puzzle and that there will be a host of questions in the middle!

OK, I can answer question since that is an Aspect Oriented activity and within my comfort zone.

I understand that the last installed OS generally 'wins' on bootup and that I'd need GRUB for multi-boots but again, no mention of that in the original thread... But again, my experience of multi-booting slaps me back into the comfort zone however, in the LINUX world I'm back in the dark... Where is GRUB?  How do I install?  Will it play nice with XP and VISTA?

Perhaps an even more important issue is network connectivity... Pal says during the install, all necessary network protocols will be installed to instantly hit the net but, my experience kicks in and I ask about drivers for my NIC and if, since I use fixed IP's on my subnet, the installation will still be 'easy'.  Well, the answer is "its all in there"... Well OK then!  I'm almost happy now!!!

And, what does this mean?
"sudo apt-get install xorg-driver-fglrxUpdate"

Sure, easy enough to see that an install/update procedure kicks in but what is SUDO?  Yup, easy enough to query the net for it but, when/where do I call it? What must I do to pull up a command prompt window (err whatever it's called in LINUX :confused:).

Arrgh!!!

---

### Post by Mornedhel on 2007-08-29
GRUB will be installed as part of the Ubuntu installation procedure, and will attempt to detect other OSes (and generally succeeds), and create entries for them in the boot menu. (Compare with the MS boot managers, which will only look for existing Windows installations, and forget about other OSes.) Dual- or triple-booting with other OSes is perfectly feasible and almost automated.

Don't know about the networking part, it's not really my field.

'sudo' is a mechanism to allow normal users to temporarily issue administrator-only commands (to play root for a while).

For instance :
sudo apt-get update
updates the package database from the repositories on the Net.
gksudo synaptic (or gksu synaptic)
starts an interface for package management (update, installation, removal, etc.)

---

### Post by timcredible on 2007-08-29
grub plays well with xp and vista

99% of nics will run fine from first boot, and it's easy to change from dhcp to static ip (menu option, click a button, type in your ip/subnet/dns, etc.)

ati is a pain in the a$$ because their linux drivers are not good.  i only buy nvidia because they work very well.  i have 7.04 running on a pc with ati x1550, i had to follow instructions i found on [www.ubuntuguide.org](www.ubuntuguide.org), and i've been running linux off and on since 1994.  so, yes, the ati card may be difficult to get the 3d stuff working, but all your other issues are not a problem.

before installing anything, read [www.ubuntuguide.org](www.ubuntuguide.org), it has 99% of your questions answered with copy-paste simplicity.

---

### Post by hamhoks on 2007-08-30
Thanks guys!

I vsisted the 'guide' and was quite overwhelmed by the amount of info.

I'm ready to install and started the alternate CD process but came to a halt on Partitioning.

I take that UBUNTU doesn't necessarily operate under NTFS and if not, what is is the format? And, will my Win installs be able to read it?  Perhaps some version of SAMBA is involved?

I did see that SAMBA is able to mount a NTFS partition and that's a start:)

---

