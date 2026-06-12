---
title: "New Xubuntu install - can't get to internet"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by Ortnet on 2007-02-08
I am new to the Linux/Ubuntu world as of about 3 weeks ago, when I installed Ubuntu 6.10 on 3 computers on my home network. (2 dual booting with XP Home, because I can't get a couple of games to run). Each of these computers uses a wireless connection - one usb, one pcmcia and one PCI card. 

I have a 4th computer that is a little older, so instead of installing Ubuntu, I installed Xubuntu, because I had read that the response time is a little faster using XFCE instead of GNOME or KDE.

Here's my issue: The current location of the computer requires a wireless connection. I have two different wireless USB cards that worked on the computers running Ubuntu. Note: each of them required me to run ndiswrapper to get them to work. 

Xubuntu doesn't even see the usb card. I know that the usb ports are working, because I used a usb jumpdrive to transfer the usb wireless card drivers to the Xubuntu desktop.

I was thinking that by running ndiswrapper, the system would see the card and let me configure it. However, ndiswrapper is not installed. It's not listed in the Add/remove utility or Synaptic. So, as far as I can tell, the only way to install ndiswrapper is to download it. However, I can't download it until I can get the card working - which is my catch22 dilemma.

Other than adding a NIC and moving it computer to a place where I can plug an ethernet cable into it, is there anything else I can do??

Thanks,
-Michael

---

### Post by punx45 on 2007-02-08
ill get the ball rolling till one 'o the experts comes in :)

what model to the best of your knowledge is the USB wireless adapter? is it the same or different than the other USB adapters that did work with ubuntu?

in a terminal do 'lsusb' and then 'lspci' and paste the output of each in here.

---

### Post by Ortnet on 2007-02-08
I've tried two different USB wireless adapters, both of which worked on the Ubuntu machines (not just the same models - the exact same adapters)

One is a generic adapter that says "USB-400" on it and on the driver CD (802.11b).

The other is a Trendnet TEW-424UB (802.11g)

Here is the output from lsusb and lspci:
~$lsusb
Bus 001 Device 002: ID 0967:0204 Acer (??) WarpLink 802.11b Adapter
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  

~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT82C598 [Apollo MVP3] (rev 04)
00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C586/A/B PCI-to-ISA [Apollo VP] (rev 41)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 02)
00:07.3 Bridge: VIA Technologies, Inc. VT82C586B ACPI (rev 10)
00:08.0 USB Controller: OPTi Inc. 82C861 (rev 10)
00:0a.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c)


Thanks!

---

### Post by teaker1s on 2007-02-08
burn the alternate Iso suitable for your system, use add cdrom feature in synaptic,hit reload tab and you can now search and install
network-manager-gnome and ndiswrapper and utilities:KS

---

### Post by lyceum on 2007-02-08
The only think I can think of is to move your PC so you can plug in to set up your wireless. That or download ndiswrapper and put it on your flash stick and put it on the Xubuntu box. I have no idea where to start on how to do that though... sorry

also.. add/remove & synaptic pull programs from the net. So even if they were there you could not install them w/ out internet access.

---

### Post by punx45 on 2007-02-08
so the two adapters that did work on standard Ubuntu installs are the same ones that wont work on the Xubuntu install?

if that is the case, my guess is that the xubuntu install cuts out some of the extra drivers etc. to stay lightweight.   if you had success with ndiswrapper with those adapters before, then do like teaker1s said and enable CD with synaptic and install ndiswrapper that way.

---

