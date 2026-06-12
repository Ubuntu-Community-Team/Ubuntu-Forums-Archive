---
title: "Very defiant wireless PCMCIA card"
date: 2008-01-23
forum: Apple PPC Users
---

### Post by Aphoxema on 2008-01-23
I have an EW-7108PCg PCMCIA card  I got specifically because Edimax is so well supported and has open specifications and all that. I'm using it on a Powerbook Pismo under Ubuntu 7.04 (I'd install 7.10 if I could)

When I use the card at home, which is WEP to make it painless for now, it works fantastically. I saw a suggestion somewhere to not use the network-admin tool for it, but it works fine with it at home.

I go to a community college with open wireless G using a series of dummy routers. Let's say the ESSID is SOMECCPublic. I can get it to work but I don't have a reliable way of doing it. For now I gave up with the shell script I made and I'm using network-admin in 'roaming mode', then I wait a while and try dhclient, see if it gets a lease, and if it doesn't I keep trying again. Sometimes it works fine the first time, sometimes I have to spend 10 minutes getting it to cooperate.

My friend, though, gets her laptop with Windows and some Broadcom in it to connect instantly without any trouble, it performs very well for her every time.

I want to find a reliable way to get connected as rapidly at the college as I can at home. Here's the script I tried using...

#! /bin/bash
ifconfig eth0 down
sleep 1
ifconfig ra0 up
sleep 1
iwconfig ra0 mode managed
sleep 1
iwpriv ra0 set NetworkType=Infra
sleep 1
iwpriv ra0 set AuthMode=OPEN
sleep 1
iwpriv ra0 set EncrypType=NONE
sleep 1
iwpriv ra0 set SSID="SOMECCPublic"
sleep 4
dhclient ra0

I did the sleeps to see if waiting between commands helped, which it doesn't really.

---

### Post by c.cam108 on 2008-01-29
I am having a very similar problem.

I can connect fine to my own WEP network at home, but at university I cannot connect to the public wireless, a similar setup to what you describe.

In the network setup dialogue I am given the option of multiple identical ESSIDs to choose from (presumably from the different dummy access points), but I cannot seem to connect to any of them.

Any help? I'm using 6.06 if that helps.

Colin Cameron

---

### Post by stmiller on 2008-02-13
I have that exact same wireless card. In fact, that chipset (rt61 driver) is perhaps the best you can get for Linux. The problem is gnome-networkmanager, or knetworkmanager most likely.

There is a new driver for the card in the 2.6.24 kernel. So it will work better with the upcoming Hardy release also. (Or you can compile your own 2.6.24 kernel for your current distro and enable the rt61 driver).

---

### Post by Aphoxema on 2008-03-31
I installed Hardy, it was much less painless than Gutsy was actually. I'll try it at the college soon, maybe tomorrow.

---

### Post by kaginken on 2008-03-31
If the college wireless is not WEP, i.e. if it's WPA encryption, do you have WPA Supplicant packages installed?

---

### Post by Aphoxema on 2008-04-01
At college there is no encryption, at home I use WPA2 which works fine.

---

### Post by Aphoxema on 2008-04-02
I disabled network-manager in session and added

auto lo wlan0
iface wlan0 inet dhcp
wireless-essid SOMECCPublic

and it seems to have fixed the problem

---

