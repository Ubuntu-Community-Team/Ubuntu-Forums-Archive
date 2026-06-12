---
title: "wireless setup"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by roberto22085 on 2006-09-30
I am currently trying to set up my wireless card in Ubuntu via the command line. I want to run Ubuntu as a server but I cannot remember the default name for a wireless card, like ethernet is eth0. What is the name for wireless cards???

Thanks

P.S. I think I am setting up the card correctly, I am editing the /etc/network/interfaces file.........is that correct???  Thanks again!!!

---

### Post by hyper_ch on 2006-09-30
You could type  "iwconfig".. that should list the wireless devices...

---

### Post by dppowell on 2006-09-30
The wireless adapter is just another Ethernet adapter.  So, if your wired adapter has already been assigned eth0, your wireless will be eth1.

---

### Post by hyper_ch on 2006-09-30
well, for me the wifi card is assigned as ra0 by default in ubuntu...

---

### Post by dppowell on 2006-09-30
Okay, then there's something going on there I don't understand...my only frame of reference is my Dell notebook, where the installer autodetected both wired and wireless and assigned them to eth0 and eth1 without my intervention.

Sorry I couldn't help!

---

### Post by hyper_ch on 2006-09-30
for me it did eth0 and ra0 using ubuntu 6.06 and got a LinkSys card...


However iwconfig should list the wireless adapters...

---

### Post by roberto22085 on 2006-09-30
Via iwconfig, i found out that Ubuntu is naming my wireless card ath0. Also, I have been searching for the file that I need to add my ESSID information to and so far I have only found one....and it doesn't work. I read that there was a /etc/network/ifcfg-eth0 file that i should add that information to, but that file doesn't exist in Ubuntu.

Does anyone know what file to add that information to (ESSID)? If not I will keep looking. But thanks for all of the help!!!

---

### Post by hyper_ch on 2006-09-30
You can do that through the Gnome Interface: System --> Administration --> Networking

Btw,  /etc/iftabs assigns what the interfaces are called. 

> 
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac **:**:**:**:**:** arp 1
ra0 mac **:**:**:**:**:** arp 1


---

### Post by roberto22085 on 2006-09-30
Thanks for the info....I am using Ubuntu right now to set up a server so I don't have a graphical interface. I want to learn how to use/run Ubuntu in a "server" setting.

Thanks again!

---

### Post by blx_286 on 2006-09-30
> **dppowell said:**
> Okay, then there's something going on there I don't understand...my only frame of reference is my Dell notebook, where the installer autodetected both wired and wireless and assigned them to eth0 and eth1 without my intervention.

Sorry I couldn't help!

You have an eth0 and eth1 because of the chipset in your card. I had a Netgear WG111 and it showed up as eth1. I now have and AirLink card and it shows up as ra0. I think his is showing up as ath0 because he has an atheros chipset. That's about the extent of what I know.

---

### Post by jamvegan on 2006-10-03
> **roberto22085 said:**
> Thanks for the info....I am using Ubuntu right now to set up a server so I don't have a graphical interface. I want to learn how to use/run Ubuntu in a "server" setting.

My /etc/network/interfaces file (which was generated using the graphical tool) contains the lines:

```
# The primary network interface
iface wlan0 inet dhcp
wireless-essid xxxxx

auto wlan0
```

Where wlan0 is, of course, my wireless card (Broadcom).  Hope that helps with syntax.

---

