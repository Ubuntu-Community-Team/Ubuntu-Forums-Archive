---
title: "Ubuntu ubuntu-9.10-desktop-powerpc"
date: 2011-02-27
forum: Apple Hardware Users
---

### Post by caladan1810 on 2011-02-27
Hi Everyone,

I've installed ubuntu-9.10-desktop-powerpc onto my PowerBook G4 17".
Everything works fine except I have no WiFi.

I have researched and found there is no "Out Of the Box" wifi access for this.

I have gone to linuxwireless.org and found the drivers for the WiFi which are found in compat-wireless-2.6.35-1.tar.bz2 

I have followed the instructions and have installed through terminal everything has been installed and I have rebooted and yet still no WiFi. 
Is there an actual work around for this?

Using a Broadcom BCM4306 802.11b/g (rev 02) 
I found the WiFI Controller through ```
lspci -vnn | grep 14e4
``` which returns 0001:10:12.0 Network Controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [[COLOR="Red"]**14e4**[/COLOR]:4320] (rev 02)

Any assistance would be appreciated.

---

### Post by linuxopjemac on 2011-02-27
you need b43legacy

[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

---

### Post by snafu006 on 2011-02-27
if the drivers dont work try this.

Upon installing Ubuntu 10.0.4, immediately open the terminal and type:

sudo aptitude install wicd

Follow the instructions. Next, 

sudo aptitude remove network-manager

Follow the instructions.

Next, open up WICD which should be in your applications area, find your network, click properties and enter the password in. Click connect.

---

