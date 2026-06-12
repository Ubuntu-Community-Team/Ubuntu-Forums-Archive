---
title: "Lost wireless driver"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by Liet_Kynes on 2008-02-04
Help!  I'm not sure what I did but for some reason my wireless network card driver isn't being loaded anymore ](*,). I'd like to have to avoid doing a reinstall.

The card is an intel pro wireless 3945 and the drivers load automatically with the live CD. How can I fix without reinstalling?

---

### Post by jan quark on 2008-02-04
first check if there are inactive drivers in the restricted drivers manager

system > administration > restricted drivers manager

then pls post the results of the following terminal commands

```
iwconfig
```

```
ifconfig
```

```
lspci
```

```
lshw -C network
```
```

cat /etc/modprobe.d/blacklist
```

---

### Post by Liet_Kynes on 2008-02-04
Just started to format my HD about 2 mins before you posted :cry: :oops:

I should have read this quote

"Wisely and slow; they stumble that run fast"

---

### Post by Liet_Kynes on 2008-02-04
> **jan quark said:**
> first check if there are inactive drivers in the restricted drivers manager

system > administration > restricted drivers manager

I couldn't even access the restricted driver's manager. It said I needed to install packeage (can't quite remember it now but the package didn't want to install saying unable to build dependencies) So i thought he yI might as well reinstall

---

### Post by jan quark on 2008-02-04
perhaps a clean fresh install of ...

what version are you installing by the way..

will solve some issues

please feel free to ask if something goes awry

---

### Post by Liet_Kynes on 2008-02-04
Thanks I will and have already learned alot from this forum :)

I'm using ubuntu feisty fawn. It was running very well. The wireless was working even better than the same card in windows (e.g. in windows In one of my rooms the Wireless Signal says 27% and reboot into ubuntu its at 76%) It also transfers files on the LAN much faster.

I was gonna get Gutsy but someone said that Hardy was gonna be LTS and I should wait for that release (not sure what it means though :) )

---

### Post by jan quark on 2008-02-04
LTS means Long Term Support

that is updates will be provided for 5 years for the server edition and for 3 years for the desktop edition

furthermore the LTS editions are focussed on stability and not on the newest and perhaps unstable features

the Hardy Heron 8.04 release is in April

---

### Post by Mach1US on 2008-02-24
I have had my intel 2200BG wireless working for last two years without the problem and then yesterday it just disappeared from network manager .
When i run live cd it works without the problem but when i boot it from HD for some reason the driver is not loading.
When i run iwconfig shows no wireless adapters but when i do lspci i can see my 2200BG
```
03:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
``` 
When lshw -C network i can see it too but it tells me it is unclaimed ????
```
  *-network UNCLAIMED
       description: Network controller
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=64 maxlatency=24 mingnt=3

```
Printout from lshw -C network when using live cd:
```
 *-network
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:ea:f4:63
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.0kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) ip=192.168.1.148 latency=64 link=yes maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=IEEE 802.11g

```
Also it is not blacklisted nor is it disabled in restricted drivers.
Latest update is definitely at fault.
Still ,why is it keeps coming back as unclaimed after update installation  ?:confused:

---

