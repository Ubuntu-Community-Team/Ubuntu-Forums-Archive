---
title: "arg. losing my mind but want to stick with it!"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by noobbutnotboob on 2007-06-21
I installed Ubuntu 7.04 i386 on my laptop after I decided to hate windows xp. I had tried installing the latter for 2 weeks but couldn't get it to work when a friend mentioned Ubuntu. I tried it and it loaded perfectly the first time, leading to my infatuation with it. 

BUT I cannot get my internet connections - whether wired or wireless - to work. Thus I can't install any of the cool apps like Beryl, etc. I can establish the connection (wireless at a public hotspot or through my wired Cox cable modem) and the system will tell me so ("you are now connected, etc...") but then when I run Mozilla it says it can't find the webpage (of any site I try). When I try to install some apps (particularly Wine and the Wifi-radar), it says I don't have a network connection. I've tried evertyhing I can think of and many ideas for similar problems from the forums but haven't had any luck. 

Anyone have any idea what I am doing wrong? BTW I used to work for Microsoft (helped them develop Word 1989-1991, but I am a Linux virgin).

thanks!

---

### Post by Happy_Man on 2007-06-21
Dude..... did you really help make Word? That's awesome.... 

But back to the matter at hand. What ethernet adapter and wireless card are you using?

---

### Post by samuraiCat on 2007-06-21
> **noobbutnotboob said:**
> I installed Ubuntu 7.04 i386 on my laptop after I decided to hate windows xp. I had tried installing the latter for 2 weeks but couldn't get it to work when a friend mentioned Ubuntu. I tried it and it loaded perfectly the first time, leading to my infatuation with it. 

BUT I cannot get my internet connections - whether wired or wireless - to work. Thus I can't install any of the cool apps like Beryl, etc. I can establish the connection (wireless at a public hotspot or through my wired Cox cable modem) and the system will tell me so ("you are now connected, etc...") but then when I run Mozilla it says it can't find the webpage (of any site I try). When I try to install some apps (particularly Wine and the Wifi-radar), it says I don't have a network connection. I've tried evertyhing I can think of and many ideas for similar problems from the forums but haven't had any luck. 

Anyone have any idea what I am doing wrong? BTW I used to work for Microsoft (helped them develop Word 1989-1991, but I am a Linux virgin).

thanks!


Out of curiosity, did you try a dual boot? That allowed me to import all my internet settings from Windows when I installed Ubuntu to the other partition. I might never go back to that 20G of crap called my XP partition, but it's there if I need it, and all my settings appear to be working.

---

### Post by noobbutnotboob on 2007-06-21
ethernet is eth0 and the card is a Netopia 3D reach 802.11b...

let me know if that's not the right info... LOL I can't be sure of anything with this new os... :)

---

### Post by noobbutnotboob on 2007-06-21
dual boot? wish I could, but I formatted the system to do a clean install of Ubuntu - I was afraid of contamination PLUS there is malicious code in Win that will undermine installs of another OS over time (heck, it undermines itself over time). So the answer is I haven't and don't have the means to try. Thanks for the good idea!

---

### Post by Happy_Man on 2007-06-22
I need the actual model of the physical card sitting in the box....

---

### Post by noobbutnotboob on 2007-06-22
oh LOL.... I am so s.m.a.r.t. :P

The wireless card is a netopia 3d reach 802.11b
According to iwconfig the ethernet is Intel 82557/8/9 Ethernet Pro 100

---

### Post by theonlyalterego on 2007-06-22
Have you looked here yet?
linkey -> [Wifi]("http://doc.gwos.org/index.php/Networkwifi")

You should probably specifically checkout the section on ndiswrapper which basically allows you to run the wifi card using windows drivers (assuming your card lacks linux ones, I didn't search for it).

---

### Post by Skrynesaver on 2007-06-22
You have established a local connection on eth0/eth1, can you see your router ?

if so do you need to turn on your ppp run ppoeconfig then pon <dsl-provider> should autoload on boot after installation

---

### Post by christhemonkey on 2007-06-22
According to this link:
[http://www.netopia.com/equipment/pdf/3D_R_Wireless_Adapt_DS.pdf](http://www.netopia.com/equipment/pdf/3D_R_Wireless_Adapt_DS.pdf)

There are drivers available from a 3rd party.

Will have a look for you!

EDIT: Could you give the output of:
```
lsusb 
```

---

### Post by noobbutnotboob on 2007-06-22
hi alterego! very helpful suggestion, thank you...

I just looked at the page you suggested and came to realization that my wireless card is a motorola (it doesn't say so on the card, so that was new2me). It says IEEE 802.11b TER/WPC11N1 model # SWL-2300N, but nothing that directly tells me what the chipset is. The help forums have info on the 520 (Prism) and 825 (Broadcom), but I can find no number on the card that is even similar.... Any ideas?

---

### Post by noobbutnotboob on 2007-06-22
thanks Chris! I looked all over netopia.com... must have missed that!

---

### Post by christhemonkey on 2007-06-22
No worries!
Did you see my edit?

Could you post the output of:
```
lsusb 
```

---

### Post by noobbutnotboob on 2007-06-22
Hi again Chris!

Something *really* weird happened while I was poking around grub and my system completely shut down. Now I can't get it to boot at all without the rescue disk. I think it tried to go into hibernation and but instead decided to commit suicide instead of just taking a nap. It's just not booting anything - like it turns on, I hear the drive fire up, and then *poof* it shuts off. Battery is fine (actually am plugged in). So I'm going to start from scratch and reformat the drive. I've heard form colleagues at Microsoft that there is some malicious code built into xp so that if you try to remove it it will do just such a thing (obstensibly forcing the user to reinstall the last working os - windows). So I am going to format the drive clean and reinstall ubuntu. I'll post the output to lsusb when it is back up.

Thanks for your help!

---

### Post by noobbutnotboob on 2007-06-22
ok lsusb returns:

[COLOR="RoyalBlue"]Bus 001 Device 001: ID 0000:0000[/COLOR]

reading what you sent about the card from Netopia seems the WPA might be the problem as I've seen lots of threads on that. What do you make of lsusb?

---

### Post by owise1 on 2007-06-22
Mate...you appear to have two threads running on this - bit confusing for those trying to help you....

Your hard wired ethernet connection to your cable modem should be a snap with DHCP.  Did you try restarting the cable modem?

---

### Post by noobbutnotboob on 2007-06-22
hi again!

sorry about the dual thread thing... I started the networking one (you recently answered) hours ago but didn't get a response so I reposted a new thread (need to figure this thing out asap before work on Monday). Sorry I panicked!

I did try all the rebooting, restarting of the system and the cable modem - with no luck. The wired connection still won't work.

After looking at the driver info, I think I must need the ndiswrapper... installing that now. Will let you know if it works. :)

---

### Post by noobbutnotboob on 2007-06-22
ok getting nowhere again... this is what I get from ifconfig:

[COLOR="RoyalBlue"]link encap:Ethernet  HWaddr 00:02:78:E6:FF:CA
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX Packets: 0 errors:0 dropped:0 overruns:0 frame:0
TX Packets: 0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueulen:1000
RX bytes:0 (0.0b)  TX bytes: 0 (0.0b)
Interrupt:ll Base address:0x1400[/COLOR]

When I run lshw:

[COLOR="royalblue"]*-network
description: Wireless Interface
product: ACX 100 22Mbps Wireless Interface
vendor: Texas Instruments
physical id:0
bus info: pci@02:00.0
logical name: wlan0
version:00
serial: 00:02:78:e6:ff:ca
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical wireless
config: broadcast=yes driver=acx_pci latency=64 multicast=yes wireless= IEEE 802.11b+
resources: ioport:1400-141f iomemory:1401000-1410fff iomemory:14000000-1400ffff irq:11[/COLOR]

When I look at Windows Wireless Drivers from the Admin menu, under currently installed drivers there is nothing. If I try to install new driver, I can find no location with an inf. Network settings show Wireless and Wired connection set to roaming. No modem is configured.

Also, when I try to get at that driver and remove in the case it is blocking the ndis, it says "module acx_pci not found".

Hope that info helps as I am stumped and starting to wonder if I made a mistake in switching from windows. :(

---

### Post by theonlyalterego on 2007-06-29
Well if you've already considered it, I'd do a clean Ubuntu install before giving up. I had some untraceable problems in the past when I had a dual boot setup, but a clean install and upgraded version of ubuntu in working just fine using a wired connection.

---

### Post by byunique on 2007-06-29
Don't give up!! The payoff is big when once you get it working. Just FYI, it usually takes some patience if things don't work out of the box for some reason with Linux. But once it does work, its ROCK solid, which makes it ALL worth it. :p

I would concentrate on getting the wired connection working, just because it WILL be easier that doing the wireless connection with the ndiswrapper stuff. From your "ifconfig" it seems Ubuntu does see the card, but no IP address is assigned. The main hurdle is the driver loading, which it is doing, proved from the fact that ifconfig has "eth0" listed. If the driver was not working, you wouldn't even see "eth0".

To configure the IP address of eth0, go into System, Administration, Network. Click on the wired connection and put in a static ip address or use DHCP (DHCP preferred). Let me know if this helps!

---

### Post by Ralob on 2007-06-29
Hey man, this is not as much an answer to your problem as it is support for you sticking with Ubuntu. I am a newbie myself and have spent the last week learning what the hell I am doing. But trust me, the payoff if immeasurable. Ubuntu is so much more efficient than Windows. Just stick with it. Once you fix the problem (and you will, trust me), you will scream eureka. 

I am sorry I have no actual help for you. Like I said, I am a newbie myself. But stay with it, you won't regret it. :)

---

