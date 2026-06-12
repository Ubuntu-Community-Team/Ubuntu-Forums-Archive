---
title: "Setting up Edgy for internet thru wired net"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by bobborn on 2007-02-05
I just installed Edgy (6.10) on a recycled computer and am having a problem connecting to the internet. I have a USR5461 router which shows an active (wired) connection to the Edgy computer, and I checked Network Settings for interface eth0: enable is on and configuration is set to automatic. Edgy recognized my  wired connection with an address set to DHCP. I'm sure I've overlooked something simple, but I can't find any clues on the forum. Can someone please help? I'm writing this from my XP computer on the same network.

---

### Post by Ryan450 on 2007-02-05
> **bobborn said:**
> I just installed Edgy (6.10) on a recycled computer and am having a problem connecting to the internet. I have a USR5461 router which shows an active (wired) connection to the Edgy computer, and I checked Network Settings for interface eth0: enable is on and configuration is set to automatic. Edgy recognized my  wired connection with an address set to DHCP. I'm sure I've overlooked something simple, but I can't find any clues on the forum. Can someone please help? I'm writing this from my XP computer on the same network.

if you've got a dhcp address from your router then I'd suggest checking to make sure your dns servers are correct in /etc/resolv.conf. 

I've also use dhclient in my terminal to auto configure resolv.conf as well as dhcp, try this in terminal.

dhclient eth0

---

### Post by bobborn on 2007-02-05
Thanks for the quick reply. I tried both suggestions but terminal returned with "Permission denied". It didn't prompt me for a password, and I logged on with one so I assumed I have admin privileges. Please excuse my ignorance.

---

### Post by Ryan450 on 2007-02-05
sorry my bad, try it again with 

sudo dhclient eth0

also try 

sudo vi resolv.conf (I like using nano myself instead of vi if you have it installed)

then add in the dns servers manually.
it should ask for your username password then it should go through.

---

### Post by bobborn on 2007-02-05
Well, the dhclient returned the following:
Listening on LPF/eth0/00:40:f4:6c:ec:47
Sending on LPF/eth0/00:40:f4:6c:ec:47
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 on port 67 interval 4
ditto intervals 10, 20, 15, 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Trying Firefox after this still gives me "server not found" when I go to yahoo.com

I tried nano to open the resolv.conf file but I don't know how to use it to input the DNS server info. While we're on that subject, can you clear up why I would do that anyway? I understand my router is a DHCP server, but the DNS is outside my network, isn't it? Like at [www.yahoo.com?](www.yahoo.com?)

---

### Post by Ryan450 on 2007-02-05
well I see above you got no dhcp offer.

that means you arent getting a dhcp address from your router, therefore no connectivity. Be sure to check your router and that it is indeed offering DHCP, the next step would be to ensure that your cables are porperly connected, maybe even try using a spare cable that you KNOW works fine.

Also do you have multiple ethernet nics? if you do try switching the cable to the other nic as you might have just plugged cable into wrong port.

---

### Post by bobborn on 2007-02-05
Perfectly logical, but I don't see any obvious problem. My router status reports DHCP on the WAN and all the other devices (3) on my network are listed under clients except for the Ubuntu one. I know the cable is good because I swapped it out from an XP PC that ran fine on the network, That leaves the NIC (only one port, btw) as a question, but device manager doesn't report any problems with it. Of course, I don't know the significance of "status" = status!? Under Device, it says:
Vendor: National Semiconductor Corp.
Device: DP83815 (MacPhyter) Ethernet
Status: Status
Bus Type: PCI
Device Type: Unknown
Capabilities: Unknown

Do you think it's worthwhile to call my router tech support? I wouldn't think that Ubuntu would be any different than Windows to connect over ethernet.

---

### Post by bobborn on 2007-02-05
Perfectly logical, but I don't see any obvious problem. My router status reports DHCP on the WAN and all the other devices (3) on my network are listed under clients except for the Ubuntu one. I know the cable is good because I swapped it out from an XP PC that ran fine on the network, That leaves the NIC (only one port, btw) as a question, but device manager doesn't report any problems with it. Of course, I don't know the significance of "status" = status!? Under Device, it says:
Vendor: National Semiconductor Corp.
Device: DP83815 (MacPhyter) Ethernet
Status: Status
Bus Type: PCI
Device Type: Unknown
Capabilities: Unknown

Wait!!!!!!!!!!!! Ryan, you are a friggin genius! I got out my flashlight and looked at the back of the PC. There is an add-in NIC that I completely overlooked. I had the cable plugged into the motherboard port. When i switched to the add-in and rebooted the PC, my router recognized the client and I can get on the 'net. Thanks for your patience. :)

---

### Post by Ryan450 on 2007-02-05
hehe, no worries mate. Glad to help :). if you dont want to do the cable swap then its pretty simple use 

ifconfig -a

to list all the network nics you have on your compy. dhclient eth1 to bring it up manually. You can also use the gui to manage your network interfaces via the administration menu. I used that to configure my wireless to be brought up at boot, pretty straight forward to use.

also, no need to reboot for something so simple, dhclient the thing again to ask for another dhcp request and your router should pick it up as well.

---

### Post by steve.horsley on 2007-02-05
First off, run the command **ifconfig** and look at the output. Look at eth0 and look for the word RUNNING. If that's not there, the interface isn't working properly. You can also look at RX packets and TX packets, to verify that packets are beig both recieved and transmitted.

---

