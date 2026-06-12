---
title: "How do I load software to match added hardware?"
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by Panhead Bill on 2006-03-22
I'm battling with my install, so i tried the live disk: no go.
I get many errors about line 125 and a few about a couple of different lines.

Next I pulled the raid and ethernet card, and tried again.  The live disk almost fires up but ends up in the BASH shell.  During the attempt the message is that I dont have an ethernet card, but do I want to configure for firewire ethernet (unlikely).  Well I do have a usb2 card and a wireless card in the PIC slots but no Firewire.

I will continue to pull cards and try the live disk until I get the desktop screen and functionality, then I will try the install disk.

My main PC has the same MB and CPU as my linux box and the live disk worked flawlessly on the main PC so I know that the disk is good.

All this to ask, if I finally get Breezy to install will it be difficult or easy tohave Ubuntu auto detect the new hardware and load the packages needed?

TIA

---

### Post by az on 2006-03-22
[QUOTE=Panhead Bill]I'm battling with my install, so i tried the live disk: no go.
I get many errors about line 125 and a few about a couple of different lines.

Next I pulled the raid and ethernet card, and tried again.  The live disk almost fires up but ends up in the BASH shell.  During the attempt the message is that I dont have an ethernet card, but do I want to configure for firewire ethernet (unlikely).  Well I do have a usb2 card and a wireless card in the PIC slots but no Firewire.[/QUOTE]

I doubt that the problem is that it cannot find an etheret card.  If you have no network interface, the install still continues normally.


[QUOTE=Panhead Bill]
I will continue to pull cards and try the live disk until I get the desktop screen and functionality, then I will try the install disk.

My main PC has the same MB and CPU as my linux box and the live disk worked flawlessly on the main PC so I know that the disk is good.

All this to ask, if I finally get Breezy to install will it be difficult or easy tohave Ubuntu auto detect the new hardware and load the packages needed?

TIA[/QUOTE]

Maybe it's the optical drive that's the problem?

The only think you will need to do when you change hardware is reconfigure the graphics card by hand.  Everything else is done automatically.

If you change the video card, or move the harddrive to another computer, boot into recovery mode and run
dpkg-reconfigure -phigh xserver-xorg
and then
init 2

You should be good to go.

---

### Post by Panhead Bill on 2006-03-23
[QUOTE=azz]Maybe it's the optical drive that's the problem?[/QUOTE]

Well the Plextor DVD R/W drive would stop the install at the 12% mark of downloading packages, so I pulled out a 1995 vintage quad speed Mitsumi CD ROM which would load the main packages but then error in downloading the additional packages.  

Bypassing the other packages in expert mode would get me past the reboot in the install process, and inserting the cd after the boot started on the Hard drive would initiate the additional packages, but with many buffer errors.

I figure that if I pull all the pci cards except the video card and the live cd works, I should be able to get the install to work.  If not I'll pull a CD/ROM out of my main PC and try again.  (the main PC did work with the live CD).

---

