---
title: "linux noob with several issues after install"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by f_s on 2006-07-20
hi there

my problems:

- get strange sound failure and authentication protkoll error messages in terminal windows when invokin sudo gedit, etxtfile ist opened with gedit, terminal hangs, when i enter [Ctrl]+C terminal stopps hanging and gedit is closed; creepy!

- DWL-G122, the dreaded D-Link problem hog; go it working eventually with the RT73 driver; problem is: i ahve toreconfigure each time with iwconfig to get a conenct to the access point; where the heck can I save these settings? the interfaces file looks fine (for me, yet --> see title)

- after the kernel upgrade during this week "sudo make" won't work at all! it states that there is no "build" folder; of course that's true, the build folder is in the old kernels directory -- again: very creepy!

Hope someone indugles me with some help

regards

Frank

---

### Post by adam.tropics on 2006-07-20
A bit confused with the first part of your problem, but if you type sudo gedt in terminal, gedit (text editor) will open, and that terminal will be held for output of running program, gedit. Such as any error messages etc. As you opened it from terminal, killing the terminal command, <ctrl>c will give you back the terminal, and close gedit, that's normal.

The second part,,,,click on System>>Administration>>Networking

Enter your password, and setup your network stuff from the nice shiny gui, save your settings, and then activate. That should keep them going.

---

### Post by f_s on 2006-07-20
thanx adam

reg. terminal:  ok, so now I understand the behaviour of the terminal window, makes sense after all

reg. using the network GUI: this won't do the trick or worse will just end up with a complete systeme freeeeeeeeeeeeeeeeeeeeeeeeeeez (as described for the Ralink RT73 driver or e.g. the DWL-G122 USB stick); what I don't understand here is: in the interfaces file every info is present (like ESSID, WEP key, etc.) but DHCLIENT cannot obtain a lease until I reconfigure the USB WLAN adapter using iwconfig; though of a shell script to do the work and save me some tiping (whych in fuct ist bessikally brone to eorors ;o)

reg. my make problem: how do I hve to reconfigure the "make" prog after a kernel upgrade so that it will work? Do I really (really?) have to compile the drivers (here for my WLAN USB) again?

Thanx again! The fog is getting thinner each minute I delve into Linux!

Regards

F

---

### Post by adam.tropics on 2006-07-20
can you post your /etc/network/interfaces file

---

### Post by f_s on 2006-07-20
auto lo
iface lo inet loopback


auto rausb0
iface rausb0 inet dhcp
mode auto
wireless-essid ConnectionPoint
wireless-key s:se18cg2327DOF

---

### Post by f_s on 2006-07-21
pushed upwards

:D

---

### Post by adam.tropics on 2006-07-21
Well that wasn't what I expected, however you, it seems are not alone and might benefit from reading [this thread]("http://www.ubuntuforums.org/showthread.php?t=187201&highlight=usb+interfaces").

---

### Post by f_s on 2006-07-21
adam

thanx for the hint! accordingly I changed my interfaces file to:

iface rausb0 inet dhcp
pre-up ifconfig rausb0 up
pre-up ifconfig rausb0 down
pre-up iwconfig rausb0 essid <my SSID>
pre-up iwconfig rausb0 key <my WEP key>
pre-up dhclient rausb0


as a result the login screen hung, no mouse action, USB device not even powered

changed the intergaces file to

iface rausb0 inet dhcp
mode Managed
rate auto
wireless-essid ConnectionPoint
wireless-key s:se18cg2327DOF
auto rausb0


and still have to use the iwconfig commands in a terminal window to get dhclient fetch an ip address:

frank@frank-pIII:~$ sudo iwconfig rausb0 rate auto
frank@frank-pIII:~$ sudo iwconfig rausb0 mode managed
frank@frank-pIII:~$ sudo iwconfig rausb0 essid "ConnectionPoint"
frank@frank-pIII:~$ sudo iwconfig rausb0 key s:se18cg2327DOF
frank@frank-pIII:~$ sudo dhclient rausb0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/rausb0/00:15:e9:ba:8a:1c
Sending on   LPF/rausb0/00:15:e9:ba:8a:1c
Sending on   Socket/fallback
DHCPREQUEST on rausb0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.5 -- renewal in 37999 seconds.


regards

F

---

