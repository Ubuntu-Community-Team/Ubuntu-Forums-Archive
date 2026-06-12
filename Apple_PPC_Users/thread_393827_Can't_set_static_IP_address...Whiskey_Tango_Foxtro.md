---
title: "Can't set static IP address...Whiskey Tango Foxtrot?"
date: 2007-03-26
forum: Apple PPC Users
---

### Post by mph66 on 2007-03-26
Hi All,

When I sudo network-admin and attempt to set a static ip, the address won't work.  I've confirmed with the network admin that I am in fact using an ip address from inside the DHCP pool (tried those addresses outside the pool and that didn't work either).  I've also confirmed that I'm using the correct gateway and subnet mask.  Yet, when I OK these configurations, I can't ping anything past my own IF.  I'm postulating that it's a lack-of-support-for-PPC problem, because when I set a static ip for an Intel machine on the same subnet it works fine.  Can anyone confirm this theory?  Is it something else?


Best,

Marc

---

### Post by BryannMelvin on 2007-03-27
the last time this happened to me I had the gateway entered....but forgot to set the gateway DEVICE

on occasion I have had to deacivate the ethernet device....to get wireless to work as the gateway device as it had defaulted to eth0 even though I was trying to get eth1 (wireless)

Also If ppp has been used before I have had to deacivate the ppp device and/or uncheck "use modem as the default route to the internet" block

I have also had to reconfigure firestarter to get the right device to the internet (eth x instead of ppp) if you have the firewall running. Firestarter works better here doing that from preferences   the wizard seems to stall when changing gateway here.

Hopes this helps, I'm changing this stuff all the time as I have wireless connection at  my studio, and at the local library, wired at home and modem on one ubuntu machine as a backup when the wind blows the wireless  antenna at the top of a mounatain down :-)

---

