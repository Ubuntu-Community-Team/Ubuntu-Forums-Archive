---
title: "network manager question"
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by psylocat on 2006-09-15
I have just got network manager up and running, but in the drop down menu below it's icon, no networks are being listed below the Wireless Networks heading. I know I'm in an area with at least one working wireless network. Any thoughts??

Thanks!

---

### Post by Kobalt on 2006-09-15
Hello,

Can you give us the result of this command line : 
```
ifconfig
```

Cheerio !

---

### Post by psylocat on 2006-09-15
no problem:

eth1   Link encap:Ethernet  HWaddr 00:14:A5:95:E5:88
       UP BROADCAST MULTICAST  MTU:1500  Metric:1
       RX packets:0 errors:0 dropped:0 overruns:0 frame:0
       TX packets:630 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:1000
       RX bytes:0 (0.0 b)  TX bytes:26460 (25.8 KiB)
       Interrupt:225 Base address:0xc000

lo     Link encap:Local Loopback
       inet addr:127.0.0.1  Mask:255.0.0.0
       inet6 addr: ::1/128 Scope:Host
       UP LOOPBACK RUNNING MTU:16436 Metric:1
       RX packets:17 errors:0 dropped:0 overruns:0 frame:0
       TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:0
       RX bytes:872 (872.0 b)  TX bytes:872 (872.0 b)

---

### Post by Kobalt on 2006-09-15
All right, your ethernet card is well recognised though no connection is using it. 
How do you connect yourself to the internet : I mean the type of modem/connection ?
You can try to activate your eth1 interface to configure it with the network manager with this command : 
```
sudo ifup eth1
```

---

### Post by psylocat on 2006-09-15
I have been able to connect via a wired connection, but here I am specifically trying to access a wireless network (VPN network). To "sudo ifup eth1", the reply I get is "interface eth1already configured"

---

### Post by Kobalt on 2006-09-15
Damn am I dumb or what... You wrote you wanted a Wireless connection and I was on configuring an ethernet connection. Sorry, my mistake. So, from the begining : your wireless connections does not appear in "ifconfig". Can you try ```
sudo ifup wlan0
```
and then ```
ifconfig
``` again. If you still don't see your wireless interface (wlan0,1...) there, it means your wireless card is not recognized. And so, we would need the model of that card to help you out. 

Sorry again I made you lose some time ](*,)
Way too much Ubuntu :)

---

### Post by Najand on 2006-09-15
His Wireless Network uses "eth1" and not "wlan0"
Check [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide) for troubleshooting and have a look at [https://help.ubuntu.com/community/WifiDocs/WirelessNetworking](https://help.ubuntu.com/community/WifiDocs/WirelessNetworking) after your driver installed.

---

### Post by psylocat on 2006-09-15
no problem. to "sudo ifup wlan0" I am being told there is no such device. However, under system->administration->networking, a wireless connection is being detected (as eth1). Also, I have just previously been through the process of setting up my drivers to get my wireless card recognized and functioning, and everything went smoothly...right up until this netwrok manager problem.

---

### Post by psylocat on 2006-09-15
Any other thoughts out there?

---

### Post by Kobalt on 2006-09-15
What's the name/brand of your wireless card ? What type is it : pci, usb, ... ? When you say you installed the correct drivers etc, do you mean you used ndiswrapper to do so ? If not, what method did you use ?

---

### Post by steve.horsley on 2006-09-15
The output from **iwconfig** and **iwlist scan** might be interesting.

---

### Post by Cylon on 2006-09-15
I've installed Ubuntu on a laptop and it's the first and only Linux system in our organization and might be one of the first for a state agency in Washington. All this promise of how Unbuntu is easy to use prompted me to give it a try. At home, I run SuSE on my family PC and PCLinuxOS on my own PC - both systems have gotten me by happily for years and my family uses them without any issues.

So I setup a Gateway MD-200STM laptop with Ubuntu, using a Linux Journal disk that includes all the different flavors of Ubuntu in a single install. The installation went smoothly and I was up and running in about 30 minutes. Everything worked fine in tests outside of my work's network but now I'm having an issue with the network manager - and wireless in general.

If I'm in an area with unsecured wireless then the system automatically connects without any configuration. However, I'm now at work and trying to connect to our secure wireless connection but nothing shows up in the available networks.

All the manual configuration stuff might be great for getting things working but I can't pass this laptop off to the average user and expect them to go through all this trouble. So I'm seeking a solution that will just work, not a bunch of config files that need tweaking. I hope something exists because I'd like to be able to bring Linux into our organization through Ubuntu.

While the wireless network is the first snag, I thought I'd also mention that dual-monitor setup was the second but will address this later when it's more necessary. Thanks for any help.

---

