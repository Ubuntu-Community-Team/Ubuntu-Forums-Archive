---
title: "Installing Broadcom 43xx Firmware driver"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by TeuchterNYC on 2007-06-17
I'm trying to instal bcm43xx-firmware driver for a Belkin wireless card. I have actually done this successfully before using the same file from the same CD, so I'm sure the file is good. I am working on a new, clean installation of Ubuntu 7,04 again from the same CD I used before. 

When I double click on the package located on the Desktop, the Package Installer come up and I click Install Package. I then get a window with the Installing package progress bar that continues to run endlessly. When click on the terminal button, I get:

"Selecting previously deselected package bcm43xx-firmware. (Rading database... 88002 files and directories currently installed.) Unpacking bcm43xx-firmware (from ../bcm43xx-firmware_13-lubunt.deb)...

WARNING: There have been some reports of problems with bcm43xx driver on etc...

I will now continue to install, just be aware. Please hit return to continue..."

When I hit enter, it continues to install endlessly. The Package Installer will no close when I attempt to close the window.

At the Terminal when I type:

sudo aptitude install bcm43xx-firmware_13-lubunt.deb (and then enter the admin password), I get

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package list....Done
Building dependency tree
Reading state information....Done
Initializing package states.....Done
Building tag database....Done
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Rebooting and running the same command gets the same result.

Seems that the problem has nothing to do with the driver and is to do with access to directories. Any suggestions anyone? I am very new to Linux. Thanks.

Allan

---

### Post by Seisen on 2007-06-17
Do you have synaptic running or update manager running? That will cause the error.

---

