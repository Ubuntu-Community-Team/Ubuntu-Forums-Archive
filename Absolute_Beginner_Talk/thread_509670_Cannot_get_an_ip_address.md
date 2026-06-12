---
title: "Cannot get an ip address"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by Chemical22 on 2007-07-25
Hey i am having troubles getting an ip address in Ubuntu. I am new to Linux and have no idea how to trouble shoot it. I have gone over some other posts but it just seems giberish to me. Could someone assisnt me in getting a connection. Thanks

---

### Post by Blutack on 2007-07-25
Firstly, how are you connecting?
We can go on from there...

---

### Post by Chemical22 on 2007-07-25
I am connecting through wire. I was connected to a router so i tried connecting directly to my cable modem and it did the same thing. 

Not sure if you want this information but here is computer specs.

Processor: Intel(R) Core(TM)2 CPU 4400  @ 2.00GHz (2 CPUs)
Memory: 2032MB RAM
Display Devices: Radeon X1950 Pro
Motherboard: Asus P5B-VM
Realtek RTL8168/8111 PCI-E Gigabit Ethernet NIC

---

### Post by Blutack on 2007-07-25
Do you see an icon with 2 computers at the top right of the screen with a cross through?  If you click that and have the option click on "Wired Network" and see what happens.  (I'll have to go btw but someone else should help out.)

---

### Post by Chemical22 on 2007-07-25
Ya i see that there is no cross or anything its just the 2 computers over each other and if i click on it i see Wired Network but its greyed out

---

### Post by Blutack on 2007-07-25
I don't want to patronise but just unplug and plug everything back in again between the pc and router, and make sure the router is on and ok.  Does your internet work?

---

### Post by lisati on 2007-07-25
> **Chemical22 said:**
> Ya i see that there is no cross or anything its just the 2 computers over each other and if i click on it i see Wired Network but its greyed out

I'm a "networking noob" and a "Linux noob" so I might not be able to give a full answer - one question comes to mind: what appears when you right-click on the two computers? On my laptop it gives me the option of enabling wireless and another option for enabling wired networking.

---

### Post by Chemical22 on 2007-07-25
Ok, so i reconnected my router and it showed 2 monitors with a red triangle with an ! in it. 

If i right click the monitors i get a menu showing Enable Wired wich is selected.

---

### Post by ddrichardson on 2007-07-25
First lets check if the interface is correct, tyoe the following in a command prompt and post the result here:

```
ifconfig
```

---

### Post by Chemical22 on 2007-07-25
Ok here is my results for ifconfig

chemical@Chemical:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1A:92:90:2F:87  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

---

### Post by ddrichardson on 2007-07-25
OK so the interface appears configured, post the output of:

```
sudo dhclient
```

---

### Post by Chemical22 on 2007-07-25
Ok here is my sudo dhcleint 

chemical@Chemical:~$ sudo dhclient
Password:
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1a:92:90:2f:87
Sending on   LPF/eth0/00:1a:92:90:2f:87
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
chemical@Chemical:~$

---

### Post by ddrichardson on 2007-07-25
These two commands let us know that a. your card is configured, loaded into the kernel ad active; b. that the router is not responding to your requests for an ip address.

In laymans terms - Ubuntu is working, something between your network card and ISP is not.

First things first - check your network card - if it's one of the type with two leds visible on the back then you should see one flashing when you issue the dhcp command.

Then check the cabling and the router.

Lastly, check that your router doesn't have a static ip address. I have to go for a while but I'll check again in a few hours.

---

### Post by Chemical22 on 2007-07-25
Ok i will double check those but answer me this. If it is a hardware issue why can i connect fine with Windows XP but not Ubuntu? That doesnt make sense to me.

---

### Post by ddrichardson on 2007-07-25
Did this router/modem come with installation software from your ISP?

The other thing you can try is altering the time that dhcpclient waits for a DHCPOFFER repsonse and the number of DHCPREQUEST that are made.

Also you did not make mention of Windows XP connecting in your initial post - it is very difficult to diagnose network faults in person, even harder over the Internet.

---

### Post by Chemical22 on 2007-07-25
I checked the link lights at the back of my network card and they don't flash or even light up. I also checked my router and tried all different ports and nothing. 

The router i am using is a D-Link DI-604 if that means anything to you and my modem is Motorola SB5100 and no there is no software. My mobo cd has Linux drivers for the network card but i have no idea how to install them. Is it possible that my NIC is just not compatible?

---

### Post by Chemical22 on 2007-07-25
Ok so i tried my dvd boot copy of Knoppix and it does the same thing can't connect to internet. I brought it down to my dads computer and tried it in his and i was able to connect to the internet with the Knoppix cd.

So pretty much it's my NIC on my computer that must not be compatible or needs a driver update. Tell me what you think?

---

### Post by Chemical22 on 2007-07-25
Also when i downloaded Ubuntu under "What type of computer do you have?" i selected "64bit AMD and Intel computers" so that means i have the 64bit version correct?

---

### Post by Chemical22 on 2007-07-25
I found this [http://gentoo-wiki.com/HARDWARE_RTL8168]("http://gentoo-wiki.com/HARDWARE_RTL8168")  could this be what is causing my problem?

---

### Post by oilchangeguy on 2007-07-25
try powering down the modem and router. and reboot the computer, then you should be able to get online.

---

### Post by Chemical22 on 2007-07-25
OMG i fixed it. It had to do with windows disabling the network card upon shutdown. I went to device manager and than to my network properties and went to advanced and selected Wake-On-Lan after shutdown and changed it from disable to enable. I am now able to connect to the internet.

---

### Post by p_quarles on 2007-07-25
> **Chemical22 said:**
> I found this [http://gentoo-wiki.com/HARDWARE_RTL8168]("http://gentoo-wiki.com/HARDWARE_RTL8168")  could this be what is causing my problem?
Probably not. According to that post, that bug started in kernel v. 2.6.21.3, and Ubuntu hasn't implemented that version yet. So, unless the bug really started earlier and no one reported it, or you compiled your own kernel, it's unlikely. 

Are you able to get into the configuration program for your modem? With many modems, you can find by it typing the modem's internal IP address (something like 192.168.0.1) into a web browser.

---

### Post by DBStevens on 2007-07-25
p_quarles, you might want to reconsider that post has been edited.

Edit: Problem with dual-booting with Windows exist also in 2.6.19.5 and 2.6.20.8 kernel, so it is safe to assume that it will concern all 2.6 kernels until the kernel developers update the drivers for RTL8168 to the version that will be able to turn on the NIC from disabled state. (Corey)

---

### Post by p_quarles on 2007-07-25
> **DBStevens said:**
> p_quarles, you might want to reconsider that post has been edited.

Edit: Problem with dual-booting with Windows exist also in 2.6.19.5 and 2.6.20.8 kernel, so it is safe to assume that it will concern all 2.6 kernels until the kernel developers update the drivers for RTL8168 to the version that will be able to turn on the NIC from disabled state. (Corey)
D'oh. That's what I get for not reading past the first paragraph. My apologies, and glad the problem was fixed.

---

