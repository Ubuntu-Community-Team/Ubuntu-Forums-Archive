---
title: "power book 1400cs"
date: 2006-09-22
forum: Apple PPC Users
---

### Post by wd3thatsme on 2006-09-22
has anybody installed ubuntu on a powerbook 1400cs? here's the specs:


# 1400cs/166 introduced 1997.10.15; discontinued
# requires System 7.5.3 (with PowerBook 1400 Enabler) through 9.1, but not 7.5.5; Mac OS 8.1 and 8.6 recommended
# CPU: 166 MHz PPC 603e
# bus: 33 MHz
# performance: 152 (166 MHz), MacBench 4
# ROM: 4 MB
# RAM: 12 MB or 16 MB soldered, expandable to 64 MB total by adding one or two memory modules (second module piggybacks on the first). There are some single card memory upgrades that cannot be piggybacked.
# Level 2 cache: 128 KB on 133 and 166 only
# VRAM: 1 MB
# display: 11.3" 16-bit 800 x 600 dual-scan or active matrix color screen
# hard drive: 750 MB, 1 GB, or 2 GB EIDE
# CD-ROM: 6x, 8x, or 12x (removable)
# ADB port for keyboard and mouse
# DIN-8 serial port on back of computer
# PowerBook SCSI connector on back of computer
# PC Card slots: two
# size: 11.5 x 9.0 x 2.0"
# weight: 6.6-7.0 pounds with battery
# Gestalt ID: 310


:?:

---

### Post by stmiller on 2006-09-22
It probably will. But I doubt you will be able to run Gnome or KDE. Probably enlightenment, or other lightweight window managers. And you'd have to turn off any services you didn't need; make a pretty slimmed down version of ubuntu. Probably possible, but definitely not with just throwing in the ubuntu ppc cd and clicking install. 

The biggest problem may be the lack of a network card. Or does it have one?

Good luck!

---

### Post by jdp on 2006-09-25
It'll take a PC Card to get networking.  The biggest hurdle is the limit of 64MB RAM.

---

### Post by Jesterday on 2006-09-25
I have the same old laptop, and have tried to get ubuntu installed, but I must be missing something because it won't boot to the CDROM drive with the Ubuntu disk inserted. And I don't have a MacOS installed on it since I don't have one, well I have a copy of OS9 but that old book won't run that.

Anyone have any suggestions?

Darren

---

### Post by stmiller on 2006-09-25
This computer probably falls into the old-world mac category. With old world macs, you have to have a dual boot system with MacOS. MacOS 8.something is available for free download on the apple website somewhere. I think.

You'll have to use bootx, on old world machines.

[http://penguinppc.org/bootloaders/bootx/](http://penguinppc.org/bootloaders/bootx/)

I used to run Mandrake PPC and Yellowdog on old macs, and faintly remember the process. I think you have to get into some kind of disk utility from the MacOS install process and go from there to create space for Linux. Good luck,

Edit: I just found this link, might be helpful:

[https://help.ubuntu.com/community/Installation/OldWorldMacs](https://help.ubuntu.com/community/Installation/OldWorldMacs)

---

