---
title: "Fiesty network not working due to Avahi"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by AcworthJack on 2007-08-10
Problem: no network access - no IP address 

History: This PC has Windows XP (which I am on now) and works fine on the internet.  It had Fiesty on it several months ago - and worked fine. 
I am trying to install Ubuntu Studio and the network doesn't work.

As far as I can tell - this is a known bug with Avahi and the zero-conf stuff.  But, I have tried many workarounds with no success.  I read the many, many suggestions here and on other sites - but I can not get my PC to access my network.

I have even removed avahi-daemon and avahi-autoipd - but then I can not configure my network in "Network Tool".   ahhhhhhh

Any help would be great.   Can I just re-run the initial network config scripts - without Avahi - to get this thing working?  
HELP :confused:

---

### Post by AcworthJack on 2007-08-10
Bump - come on - I **know **I am not the only person seeing problems with Avahi -- should I post this in networks???

---

### Post by wirelessmonkey on 2007-08-11
Avahi, so far as I can tell, should not interfere with dhcp requests, only DNS and services discovery.  What sort of network are you on? Are you behind a personal router, or plugged directly into your Cable/DSL modem? 
From a terminal try: sudo dhclient eth0 (or the name of your network interface if different)
if it works, great, if not post the output.

---

### Post by AcworthJack on 2007-08-11
Thanks!

I am on a home network with a Dlink Router (DI-624) connected to a Comcast Cable modem.

I have a Ubuntu Server and Ubuntu Desktop running as VM from the windows server - as well as 6 Windows PCs all running DHCP from this and working fine.

This PC had Wubi Ubuntu running about 6 months ago - no problem.

I have the very typical issue of seeing my eth0 as IPV6 only.  eth0:avahi is IPV4 with the 169.x.x.x address.

There are a LOT of posts on this around the web.  I have tried many fixes - including dhclient eth0.

I have not been able to get network access.

I have also edited /etc/network/interfaces and tried dhcp as well as static.  

I have also reinstalled Ubuntu desktop and Ubuntu server 6 times today!

thanks again for any help.

---

### Post by ruibernardo on 2007-08-11
> **AcworthJack said:**
> 
I have the very typical issue of seeing my eth0 as IPV6 only.  eth0:avahi is IPV4 with the 169.x.x.x address.



Hi AcworthJack,

If the problem is because of IPV6, blacklist its module.

```
 sudo nano /etc/modprobe.d/blacklist
```

Add "blacklist ipv6" in the end of the file.

Then reboot. This will make avahi to use only IPV4.

---

### Post by AcworthJack on 2007-08-12
Thanks again - I tried blacklisting IPv6 - which did prevent Avahi from using it - but it did not resolve the eth0 problem.  Eth0 does not show any IPv4 address.

---

### Post by ruibernardo on 2007-08-12
After blacklisting ipv6 module and doing a reboot, you can't have anything working with it.

Check with the ifconfig command.

---

### Post by AcworthJack on 2007-08-12
you're right - eth0 has no network config - not IPv6 - nothing...

I tried removing avahi-daemon
I also manually deleted a lot of references to avahi - still not working.

Netowkr card shows as Realtek RTL-8139/8139C/8139C+ 
all looks OK in lshw -C network

I am running the latest WUBI Ubuntu - 2.6.20-15-lowlatency

---

### Post by ruibernardo on 2007-08-12
I guess that having removed avahi, you can't "discover" the network the right way. I would suggest you to reinstall avahi, but I doubt it will work (try it anyway). 

I would suggest you to install Ubuntu again, and after the installation process, if you are using the Deskop CD, edit the /etc/modprobe.d/blacklist file in the newly installed Ubuntu partition, or do it right after the first boot and reboot again.

---

### Post by AcworthJack on 2007-08-12
Many thanks to all for your help - here is the solution.

As documented elsewhere - I unplugged my PC for a minute, rebooted into Ubuntu (without going into Windows) and all worked fine!

see [http://gentoo-wiki.com/HARDWARE_RTL8168#Troubleshooting](http://gentoo-wiki.com/HARDWARE_RTL8168#Troubleshooting) for details

:)

First, my apologies to Avahi folks – I had pegged you as the bad guys and had visions of flaming you and all the ZeroConf folks.  Mia culpa – I was wrong.

This turned out to be a driver problem with my Ethernet eth0 interface card: Realtek RTL 8139 (8100 family).  As penance – I will tell at least 3 people this week about Avahi and ZeroConf.  :)

---

