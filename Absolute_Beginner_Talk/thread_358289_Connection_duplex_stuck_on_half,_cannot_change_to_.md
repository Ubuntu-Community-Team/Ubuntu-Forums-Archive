---
title: "Connection duplex stuck on half, cannot change to full"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by skyhopper88 on 2007-02-10
I'm new at troubleshooting Ubuntu, so bare with me. In Windows I'm getting speeds of 6699 kbps down/8830 up. In Ubuntu however, I get 974/857! Something isn't set up right. I am running Edgy on my desktop with my ethernet coming straight from the wall to my onboard ethernet. I'm not exactly sure what the specs on my onboard card are other than it's a Nvidia Ethernet Controller, using forcedeth. In Windows I got similar (slow) speeds until I set it to full duplex, that's done with ethtool, correct? Here is the original output. 
> Settings for eth0:
Supported ports: [ MII ]
Supported link modes: 10baseT/Half 10baseT/Full
100baseT/Half 100baseT/Full
1000baseT/Full
Supports auto-negotiation: Yes
Advertised link modes: 10baseT/Half 10baseT/Full
100baseT/Half 100baseT/Full
1000baseT/Full
Advertised auto-negotiation: Yes
Speed: 10Mb/s
Duplex: Half
Port: MII
PHYAD: 1
Transceiver: external
Auto-negotiation: on
Supports Wake-on: g
Wake-on: d
Link detected: yes

if I try to set it to half, it still reports half. I have also tried changing it with autonegotiation off as well as on. When autonegotiation is on, setting it to full duplex disconnects and reconnects, but it still remains half. When it's off, changing duplex to full just disconnects and doesn't reconnect unless I change it back to on, duplex still reports half. I was unable to use Ndiswrapper, and disabling IPV6 did nothing to help. Couldn't change anything running off the Dapper or Edgy Live CD either. The Fiesty Fawn Live CD lets me change it to full with autonegotiation off, but the install freezes at 94% installing grub. Is there any way to get this working with Edgy? I don't trust Feisty for everyday use yet.

---

### Post by r4ik on 2007-02-10
Maybe this helps,

[http://ubuntuforums.org/showthread.php?t=357041&highlight=full+duplex](http://ubuntuforums.org/showthread.php?t=357041&highlight=full+duplex)

Good luck !

---

### Post by skyhopper88 on 2007-02-10
Nope, my card doesn't support mii tool. I am trying to do the same with ethtool however, to no effect. I'm in Windows right now because I unknowingly disabled IPV4 and completely diabled my connection somehow in Ubuntu.

---

### Post by r4ik on 2007-02-10
Try if this will fix it,

[http://www.ubuntuforums.org/showthread.php?t=349289&highlight=IPV4](http://www.ubuntuforums.org/showthread.php?t=349289&highlight=IPV4)

Good luck !

---

### Post by skyhopper88 on 2007-02-12
Odd, IPV4 came back after a reboot, but hadn't before. I still have my original problem though.

---

### Post by skyhopper88 on 2007-02-12
Is there a way to "steal" Feisty's networking capabilities? I was able to change the duplex on its liveCD, but not install it, not that I'm comfortable with using it anyhow.

---

### Post by skyhopper88 on 2007-02-12
Somehow I got disconnected trying to update and after another reboot my connection is dead again. Network Manager is telling me no network devices have been found. sudo DHclient eth0 is giving me

> Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:15:58:25:fd:09
Sending on   LPF/eth0/00:15:58:25:fd:09
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by skyhopper88 on 2007-02-13
Since I have Edgy installed and the Feisty livecd, can I update from within Edgy since Feisty froze on its own? I put the CD in and it recognized there were packages on it but I couldn't figure out how to get it to update through synaptic. I may be willing to do that if I can't find a workaround for my connection.

---

