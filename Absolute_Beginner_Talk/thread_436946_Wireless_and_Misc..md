---
title: "Wireless and Misc."
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by nonpareilpearl on 2007-05-08
I decided to test out Feisty on my Laptop (Dell Inspiron 5150, Par. with XP and now Feisty). After a few initial glitches I have been amazed at the shininess of it all.

One thing I was really hoping for, is that my wireless would finally work! I am going to be traveling and will need access to wireless to use the internet (and I was hoping to use Ubuntu). At first Feisty seemed to recognize the fact that I have a wireless card, and now it doesn't seem to. I was wondering if anyone that can use wireless with Feisty can put up a small screenshot of what the connections look like (or if someone who cannot). I need to figure out whether Feisty just doesn't recognize the card, or if the wireless signal strength is just too weak (also possible, then I know I could get internet if I could find someplace with stronger signal).

Thanks!

---

### Post by davahmet on 2007-05-08
First, let's find out how Feisty is viewing your wireless card.  Then we can figure out how to get your wireless up and running smoothly.

Please post the results of the commands:
ifconfig
iwconfig
sudo iwlist <wireless interface> scanning  ##Substitute <wireless interface with what your laptop calls your wireless card, often eth1 or wlan0

---

### Post by nonpareilpearl on 2007-05-08
ifconfig
> eth0      Link encap:Ethernet  HWaddr 00:0D:56:3B:EB:92
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:56ff:fe3b:eb92/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1277 errors:0 dropped:0 overruns:0 frame:0
          TX packets:953 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:513945 (501.8 KiB)  TX bytes:100014 (97.6 KiB)
          Interrupt:17

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)


iwconfig
> lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I didn't do the last one, because I guess it's not recognizing the card.  I guess that's what I get for having a Linksys, although I was really hoping Feisty would be able to help me out on this one.

Any help for getting it to work would be awesome :) I tried ndiswrapper when I used Edgy, but that didn't seem to fix it (even though on the list of supported cards it seemed to indicate that it would work for my card (Linksys WPC54GS v 2 if that helps).

---

### Post by tallsamoan on 2007-05-15
**This post could be related to an Ubuntu bug filed at**: [www.kosmaczewski.net/blogs/tech/archives/2006/02/how_to_install_1.php](www.kosmaczewski.net/blogs/tech/archives/2006/02/how_to_install_1.php) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi,

I have the exact same problem, I can't get the WPC54GS vers.2 to go. I could not get it to go in Edgy and now that I upgraded to Feisty, same result. I have followed all links and forums, installed ndiswrapper-utils, copied the driver location from XP as suggested elsewhere and followed all steps in the Dummies book, but nada.

Below my result from the earlier suggestion

ifconfig
> eth0      Link encap:Ethernet  HWaddr 00:0A:E4:44:27:5E  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:e4ff:fe44:275e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1230 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1509 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:979577 (956.6 KiB)  TX bytes:244248 (238.5 KiB)
          Interrupt:11 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:300 (300.0 b)  TX bytes:300 (300.0 b)


 iwconfig
l> o        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:

Regarding the wireless interface scanning, it does not "support interface scanning" 

I followed the steps in the link below on both version of Ubuntu, all that came up was "invalid driver"
I must admit I am very new to Ubuntu but am certain I tried all steps as directed.

Appreciate any assistance.

THX!

---

