---
title: "Need help connecting to internet with Wireless Network Card (Netgear WG111 v1)"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by koolkid64us on 2006-11-16
I'm new to Ubuntu, but have used a couple Linux distros in the past.  I've been able to get the internet to work on both of those, but am having a bit of trouble with Ubuntu Dapper Drake.  I've done everything in the WiFi Docs on the Help.ubuntu.com part of the site.  My wireless card is a Netgear Wg111 v1.  I AM able to ping my router, but can't access the internet.  It feels like I only need 1 or 2 more tweaks to be able to get online.  Right now, I'm using the Evil One to access the internet to type this.  Any help would be appreciated.  ](*,) :confused:

Edit:  I ndiswrapper installed the driver.

---

### Post by Ashrael on 2006-11-16
I am only a newbie too, but i think you should look if your router is using an access list/MAC control list...see if it does, and to start disable it....
I'll look at this post tomorow, and maybe it works maybe not...we'll see

ashrael

---

### Post by koolkid64us on 2006-11-16
There is no filtering of that kind within my router, and to be sure, I've set it up so my card connects through the MAC filtering, even though it's disabled.

IP: 192.168.0.3
Subnet Mask: 255.255.255.0
Gateway IP: 192.168.0.1


Those are the setting on the network setup.

---

### Post by koolkid64us on 2006-11-16
This is the only thing holding me back from using Ubuntu more than Windows...

---

### Post by doobit on 2006-11-16
I think the wg111 v.1 uses the prism2 drivers. so you need to download and install the linux-wlan-ng package using Synaptic. There are also docs there for that so get those while you are at it.

---

### Post by koolkid64us on 2006-11-16
I CANNOT connect to the internet through Ubuntu, as we're on a wireless network, and this old timer of a comp is upstairs.

---

### Post by Ashrael on 2006-11-17
Since you got an IP adress from the router,i think the problem must be in your pc, so tell us  what you see when you use SYSTEM>NETWORK and SYSTEM>NETWORK TOOLS...

Do you have another computer that CAN connect to the net? if so, download the prism drivers and transfer them to the old beast....
And otherwise you should move the pc (temp) or lay a cable....and download this driver....

Well i'll keep checking this post....


ashrael...

---

### Post by FritzBrown on 2007-06-10
I seem to be having a similar (though bigger) problem.  Though my Netgear WG111 (v2)  works on my Windows machine, I don't get anything on my laptop with xubuntu.  It (the adapter) shows in Network Admin (System -> Networks), and I can put all the right info in (WEP key and SSID), it doesn't appear to see anything out there.

I've even tried going totally unsecure, and it doesn't make a difference.  Is there something I have to do besides Activate eth0 in the Networks GUI?  I am just getting into Linux, and don't know what I don't know.

BTW, the CardBus ethernet (physical connection) works fine and dandy.  And, I just booted with the thing plugged in, Activated it in Networks, and I was on the WWW.  Doesn't help much, though, since this is a laptop and is supposed to be mobile....

**Edit**:
FIXED!  I simply looked a little harder around here, and found [this link]("http://ubuntuforums.org/showthread.php?p=2827303").  Worked on my 6.06.1 xubuntu like a champ.
**End edit**

---

