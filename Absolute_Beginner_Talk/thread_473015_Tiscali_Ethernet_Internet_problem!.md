---
title: "Tiscali Ethernet Internet problem!"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by Delfina on 2007-06-13
Hi,
I'm an absolute begginer.I've installed Ubuntu 6 and I tried an internet conection using Tiscali ADSL  with Ethernet cable.The problem is that when i lunch the FireFox browser it can be able to show me any web addresss.
I've do this
Open a terminal and write
pppeoconf
the program see the ethernet cable as etho but it say that the Access Concentrator don't respond.
Then I've open FireFox and write the IP
192.168.1.1
and the modem respond ok!
I've tried to ping from a terminal
ping 192.168.1.1
and it work ok.
The internet cocnection work well on another pc where is installed WXP and so I think it isn't the modem (pirelli).
The same problem I've got when I installed SUSE 8.0 or Mandrivia on the same machine.
This machine is a little old ,the motherboard is an ADM Atlhon,could be it?


What do you think?
Thank for your attention.
Best regards.

---

### Post by HereInOz on 2007-06-13
If you are using an Ethernet modem/router, the problem is possibly DNS.

Try going in to your Network (System > Administration > Network) and set the IP address of the Ethernet adaptor as a static IP (in the same subnet as your router), and then set the DNS addresses as those supplied by Tiscali.

That may do the trick, and also you may like to go into Firefox, type about:config in the address bar, and turn off IPv6 support.  That can also help sometimes, but I reckon your problem is DNS.

Tell us what you get when you type ifconfig in a terminal, and also the content  /etc/resolv.conf

---

### Post by Bachstelze on 2007-06-13
pppoeconf is irrelevant for most Ethernet-connected modems. Rather, try

```
sudo dhclient eth0
```

---

### Post by Delfina on 2007-06-13
The command

sudo dhclient eth0

sudo dhclient eth0

Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:13:49:aa:0f:66
Sending on   LPF/eth0/00:13:49:aa:0f:66
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.102 -- renewal in 86206 seconds.

but what it meaning?

---

### Post by rupierto on 2007-06-15
Delfina: I have the modem/router ALICE. I believe it's same problem I solved. Assuming you are connected via a modem/router and Ethernet cable (no USB!). 

Go in : System > Administration > Network
Choose: Static IP.
IP address : 192.168.1.2 [the address of your box]
netmask: 255.255.255.0
broadcast: 192.168.1.255

Gateway/Router IP: 192.168.1.1 [your router address]

DNS -> add: 192.168.1.1

restart the net.
Must warn you; now I can't control my configuration (I'm at work). If something wrong I'll correct tonight.

---

### Post by Delfina on 2007-06-15
Thanks rupierto but the problem hold over.
I've change in static ip and i can ping and connect to the modem but i can manage to connect to any
other internet adrress.
It seems that DNS it not be able to resolve the IP address.

regards

---

### Post by xpod on 2007-06-15
Tiscali use dhcp do they not so you mabey should`nt have a static ip address set.

I could be totally wrong of course.

---

### Post by Bachstelze on 2007-06-15
> **Delfina said:**
> The command

sudo dhclient eth0

sudo dhclient eth0

Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:13:49:aa:0f:66
Sending on   LPF/eth0/00:13:49:aa:0f:66
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.102 -- renewal in 86206 seconds.

but what it meaning?

That means you're connected, now you can browse the Interweb :p

There's no reason to go with static IP unless you really need it.

---

### Post by Delfina on 2007-06-16
Sorry but the problem persist.
I ping, I see the modem, I'm connected (dhclient eth0) but FireFox don't resolve the IP address.
If i write in the google box research on Firefox for example , Ubuntu ,the browser respond that it's impossible contact the server at ...etc etc and it suggest to control the cable connection or the permission of the browser (connect directly to internet)
I'm at the deadline....
What can i try to resolve?
P.S.
The same connection on my notebook with Windows XP Home Edition work very well, even with IE that FireFox.
I've notice that on my desktop pc ,Ubuntu,Suse 8.0 ,Mandrivia Spring,Knoppix and IE (when i instal windows 2000) have the same problem.
Could be a diriver problem?
I can't install on my desktop pc Windows XP.

regards

---

### Post by Delfina on 2007-06-18
Ok  now i'm surfing  with ubuntu...
I've talk with tiscali thecnical assistant  but i don't know what they have do.
Anyway the problem aren't ubuntu but tiscali...
Thank you for your support.

Best regards

---

