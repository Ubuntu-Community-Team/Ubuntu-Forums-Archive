---
title: "Permanently disabling internal Airport card"
date: 2006-07-30
forum: Apple PPC Users
---

### Post by marklid on 2006-07-30
Hi,

I have a Powerbook G4 running Kubuntu 6.06.
It has an internal Airport card (regular, not the Extreme version) so I bought a PCMCIA wireless card as my wireless network uses WPA encryption which wasn't compatible with the Airport card.

I can connect to my network fine using the PCMCIA card (ra0) by hardcoding the essid and key into /etc/network/interfaces.
I'd like to use KNetworkManager so I can change networks "on the fly" but for some reason it always tries to use the Airport card (eth1) which of course doesn't connect to my WPA network.

I have tried :
disabling it in System Settings > Network Settings
commenting out all lines referring to eth1 in /etc/network/interfaces

..but every time I try to sue KNetworkManager it always tries to connect using eth1.

Is there any way (apart from physically removing the card) that I can permanently disable this card, or force KNetworkManager to 
use the ra0 device ?

I appreciate this is a Ubuntu forum (not Kubuntu) but as this particular section is aimed at PPC users I'm hoping there have been others with a similar experience.

Thanks in advance for any help.

---

### Post by mgor on 2006-07-30
have you checked if there's some option in "bios" ?

otherwise, have you tried something like this in /etc/network/interfaces?
```
#auto eth1
iface eth1 inet dhcp
```

in other words, don't comment all the lines, just the ones that says it should be brought up automaticlly.

---

### Post by marklid on 2006-07-30
Hi,

As far as I'm aware the Powerbook doesn't have a bios so I can't disable the card from there.

I tried your other suggestion - only commenting out the auto line - this seems to have made KNetworkManager use the ra0 interface - but with no option of WPA !
I tried manually configuring the connection by selecting "Connect to Other Wireless Network" and selecting WPA but it won't connect :-(

---

### Post by rasec on 2006-07-30
marklid, to disable the airport card you need to prevent its driver from loading. To do that, add "blacklist airport" to /etc/modprobe.conf. 

Now, about that ra0 card, it supports wpa in an unconventional way that's currently incompatible with network manager. To get it working, you need a modify you /etc/network/interfaces file manually. See the ralink wiki for more details ([https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500)). 

Also, I wouldn't spend too much time getting wpa to work with network manager as libnm-util0, which handles the encryption for network managers, is compiled incorrectly for the powerpc arch so it only able to connect to open and wep networks. I made a bug report, and included a fix for it, over at launchpad.net but so far they haven't done anything about it.

---

### Post by marklid on 2006-07-31
OK thanks for the replies - looks like I will stay with my original configuration for now i.e. leave Airport alone and configure the Ralink card through /etc/network/interfaces

---

