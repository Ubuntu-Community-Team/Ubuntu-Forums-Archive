---
title: "Latitude 600 and the live CD."
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by breaking on 2008-01-06
I'm attempting to salvage usability on a Dell Latitude C600 (that a hard drive platter has crashed on) by booting the Live CD (7.10 Desktop).  I am unable to write to the hard drive.

When I boot and try to configure the wireless NIC (eth1) using the Network administration control panel, it seems to accept the settings (SSID, key, etc.) but the NIC still shows DISABLED when I run the lshw command.

I see from the Laptop Testing Team page for the model that the NIC should be supported.  [https://wiki.ubuntu.com/LaptopTestingTeam/DellLatitudeC600](https://wiki.ubuntu.com/LaptopTestingTeam/DellLatitudeC600) 

I am unable to figure out how to enable the wireless interface to show it as active. Can anyone advise how to enable the hardware or what other resolution is required?

TIA

---

### Post by Rotaj on 2008-01-06
1. Is the NIC showing up as Eth0?

2. An alternative, if you can boot from USB, is to try to install to a thumb drive(or external drive, if available). Then you can create a consistant, updateable system to boot from until the hard drive is replaced. 

A new HD(40-60Gb)  should start at about $60, 4Gb thumb drives start at $30.

---

### Post by breaking on 2008-01-07
The physical port shows up as eth0.  The wireless is eth1.

I'm aware of the flashdrive option, but that's not the one I'm pursuing atm.

---

### Post by breaking on 2008-01-07
so am I to understand that the Live CD does not support the the built in wireless without a writeable fs?

---

### Post by PetePete on 2008-01-07
that is incorrect. it supports wireless without requiring writeable fs.

is the problem you can't use wireless or can't write to the HDD ?

---

### Post by breaking on 2008-01-07
I intend to use the laptop as a terminal of sorts.  primarily just web surfing on the couch.  

the Hd is dead dead dead.  I can boot the live cd, but cannot connect to the wireliss network.  lshw indicates the wireless is disabled.

---

