---
title: "plz Help with ndiswrapper!"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by encryptedballa on 2006-07-07
UPDATE:

I now show device and driver present in ndisgtk

i have ndiswrapper in my modules file

when i restart the system hangs when it tries to load xserver. when i unplug my wireless device it goes thru, but after the system starts and i plug the adapter beck in, the system hangs a lot...stops when i unplug it.

Never does anything other than eth0 (my lan connection) show up in networking!

---

### Post by encryptedballa on 2006-07-08
ok ive installed the gui for ndis and the driver loaded and the device is present...however the wireless connection does not appear in networking??

---

### Post by Dr. Nick on 2006-07-08
have you run this from a terminal?

sudo modprobe ndiswrapper

also from a terminal run

[FONT=Times New Roman][B][B]lsmod

and look for the line where ndiswrapper is and post it here.
[/B][/B][/FONT]

---

### Post by encryptedballa on 2006-07-08
modprobe shows no errors

lsmod:

usbcore               104316  4 ndiswrapper,usbhid,uhci_hcd


the driver and device show up in ndisgtk but the wlan0 doesnt appear in networking

---

### Post by Dr. Nick on 2006-07-08
try 

**sudo ifup wlan0**

and see if that make it appear in the network control panel. I wouldnt think this is necessary, I always recall it showing up as long as ndiswrapper -l says "driver and hardware present"

---

### Post by encryptedballa on 2006-07-08
i get this message:

Ignoring unknown interface wlan0=wlan0.

sudo ndiswrapper -l:

says driver and device are present

---

### Post by Dr. Nick on 2006-07-08
ohhh.. Now I think we are getting somewhere. The file /etc/network/interfaces controls this part. I have had the wlan=wlan0 before and if I saw your config file I could probably remember the fix.

run this command to get your interfaces file

** cat /etc/network/interfaces**


here is mine for refrence
```

auto lo
iface lo inet loopback


iface eth0 inet static
address 100.68.7.102
netmask 255.255.255.0
gateway 100.68.7.1

auto eth0

iface wlan0 inet dhcp
```

---

### Post by encryptedballa on 2006-07-08
well mine doesnt turn out like that:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth1

# The primary network interface
iface eth1 inet dhcp

auto eth1

iface eth0 inet dhcp





auto eth0

---

### Post by Dr. Nick on 2006-07-08
hmm not what i was expecting to see, try to add this line to /etc/network/interfaces

iface wlan0 inet dhcp

by running 

sudo gedit /etc/network/interfaces

after its added save and exit, then retry the sudo ifup wlan0 command

---

### Post by encryptedballa on 2006-07-08
ok now i get this message:

There is already a pid file /var/run/dhclient.wlan0.pid with pid 1
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
sit0: unknown hardware address type 776
Bind socket to interface: No such device
Failed to bring up wlan0.

---

### Post by Dr. Nick on 2006-07-08
ok, sorry you can remove that wlan0 line.

I guess your wireless card isnt called wlan0. I just revied your interfaces file and it says you have eth0 and eth1

try this command in a terminal

[B]sudo iwlist scanning
[/B]
that should help up determine which device/if any at the moment support wireless scanning

---

### Post by encryptedballa on 2006-07-08
im not seeing anything about eth1:

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

---

### Post by Dr. Nick on 2006-07-08
have you tried 

sudo ifup eth1

I imagne that is your wireless card

---

### Post by encryptedballa on 2006-07-08
still no luck:

There is already a pid file /var/run/dhclient.eth1.pid with pid 1
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
sit0: unknown hardware address type 776
Bind socket to interface: No such device
Failed to bring up eth1.

---

### Post by Dr. Nick on 2006-07-08
that has me stumped :confused:

have you added the word "ndiswrapper" to the /etc/modules file?

I would try that and then just restart the computer and see if it acts any better.

EDIT

Good luck, Its 1am here so I wont be back for several hours

---

### Post by Apple 101 on 2006-07-08
> **Dr. Nick said:**
> that has me stumped :confused:

have you added the word "ndiswrapper" to the /etc/modules file?
ndiswrapper is set to load on bootup when you use the *ndiswrapper -m* command.  Although that didn't work for me, so I had to add it to /etc/modules like you said.

---

### Post by encryptedballa on 2006-07-08
yeah ndiswrapper is in the modules file for me

---

### Post by Dr. Nick on 2006-07-08
Try this command to restart the network subsystem

[SIZE=4][B]```
sudo /etc/init.d/networking restart
```

[/B][SIZE=2]It looks like your interfaces file is messed up for some reason, dont know why though. It seems like it should be working[/SIZE]
[/SIZE]

---

### Post by encryptedballa on 2006-07-08
yeah that didnt help at all...

ive tried 2 different usb devices...same thing happens with both

---

### Post by encryptedballa on 2006-07-08
well how bout this...the usb adapter comes with linux drivers on the disk and there are instructions on there on how to install...have to do with using terminal for a make install and editing the makeinstall file...but i have not been able to make any sense of it. maybe i could email the .pdf to someone and they can make sense of it for me?

---

### Post by Dr. Nick on 2006-07-08
Do you know what chipset the wireless uses? If you have a cd with drivers that need to be compiled, then their may actually be precompiled versions floating around somewhere you could use instead.

---

### Post by encryptedballa on 2006-07-08
no i have no idea what chipset...im pretty sure its generic...like ieee 802.11g or something...i got it on ebay. i tried a netgear wg111v2 as well with the same results.

---

### Post by Dr. Nick on 2006-07-08
the netgear works for others it seems

[http://ubuntuforums.org/showthread.php?t=205498&highlight=wg111v2](http://ubuntuforums.org/showthread.php?t=205498&highlight=wg111v2)
[http://ubuntuforums.org/showthread.php?t=51993&highlight=wg111v2](http://ubuntuforums.org/showthread.php?t=51993&highlight=wg111v2)

are these all usb adapters?

make sure **lsmod** doesnt list anything else on the usbcore line if so.

---

### Post by encryptedballa on 2006-07-08
well i just updated to 6.06 and the wlan0 did show up in networks finally! however im still having trouble because networking is hanging when i try to go activate the wlan0. assuming i get it activated how do i go about detecting my network?

---

### Post by Dr. Nick on 2006-07-08
Many of the commands I have posted will help some. Are you using ndiswrapper, or did it come with a native driver, A simple **lsmod** like before will tell you.

Instead of activating from the GUI try it from the terminal with

**sudo ifup wlan0**

then you can do the 

[B]sudo iwlist scanning

[/B]to find your access point

If the sudo ifup command above works then you can probably go back to the gui to configure the rest of it. I like activating from the terminal better because instead of hanging, it will atleast give you some output and a idea of why its hanging.

It may help to get into your router and make sure ssid broadcast is on and any wep/wpa encryption is off. It is easier to get the software configured like this because it takes more possibility of error out. Once you can get online you can then begin to setup wep etc..

---

