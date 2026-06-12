---
title: "Another Wireless issue"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by smakaho2daflo on 2008-04-02
Hey guys, 
I am a noob with Ubuntu, but I decided to make the switch just because I like it better that Vista. I am currently having alot of trouble getting my wireless card working. I have looked at a few other post and I have followed those instructions, but I still have dont have anything that has helped.

I am currently using 8.04.   
I saw that I am supposued to run iwconfig and if config. here is the output of both.
Any help would be greatly appreciated.

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:d3:09:34:71  
          inet addr:192.168.1.68  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d3ff:fe09:3471/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1074 errors:0 dropped:0 overruns:0 frame:0
          TX packets:940 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:905836 (884.6 KB)  TX bytes:175892 (171.7 KB)
          Interrupt:20 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:194 errors:0 dropped:0 overruns:0 frame:0
          TX packets:194 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9700 (9.4 KB)  TX bytes:9700 (9.4 KB)

THanks so much.:)

---

### Post by cmnorton on 2008-04-03
Please post the kind of hardware you have.

Two things to look at would be if wireless support was installed.

If this is a laptop, is there a wireless on/off switch? This could be a physical switch or could be a virtual toggle of some kind.

---

### Post by smakaho2daflo on 2008-04-03
Hey sorry about that. Here are my specs.

It is an HP DV2025NR laptop.
Microprocessor  1.6 GHz AMD Turion™ 64 X2 Mobile Technology TL-50  
Microprocessor Cache  256KB+256KB L2 Cache 
Memory  1024MB 533MHz DDR2 System Memory (2 Dimm) 
Memory Max  2048MB  
Video Graphics  NVIDIA GeForce Go 6150  
Hard Drive  100GB 5400RPM 
Multimedia Drive  LightScribe Super Multi 8X DVD±R/RW with Double Layer Support  
Display  14.1” WXGA High-Definition BrightView Widescreen Display (1280 x 800) 
Fax/Modem  High speed 56k modem  
Network Card  Integrated 10/100BASE-T Ethernet LAN (RJ-45 connector) 
Wireless Connectivity  802.11b/g WLAN  
HP Features  HP Pavilion WebCam with Integrated Microphone  
Sound  Altec Lansing  

Broadcom Wireless 1390 WLAN Mini-PCI Card.


There is a switch to turn on the wireless, but it does not do anything. There is nothing in the bios to switch it on or off either.

---

### Post by m60dude5 on 2008-04-03
When you click System, Preferences, Hardware Information, can you find your wireless card? Look for something with "wireless" or "networking interface", etc. something that shows its a wireless network card. Then see if its name is listed in the right panel. Let us know what it says. because then we can find out if your card is recognized or if you'll need to install ndiswrapper to let you use windows drivers in ubuntu.
EDIT: This is for 7.10, but I'm assuming its the same / similar in 8.04. Someone correct me if I'm wrong.

---

### Post by smakaho2daflo on 2008-04-03
> **m60dude5 said:**
> When you click System, Preferences, Hardware Information, can you find your wireless card? Look for something with "wireless" or "networking interface", etc. something that shows its a wireless network card. Then see if its name is listed in the right panel. Let us know what it says. because then we can find out if your card is recognized or if you'll need to install ndiswrapper to let you use windows drivers in ubuntu.
EDIT: This is for 7.10, but I'm assuming its the same / similar in 8.04. Someone correct me if I'm wrong.

I cant find where is says hardware information. I see that in administration it is showing my wireless as a broadcom b43, but it is not enabled. When I try to enable it does nothing, even after a restart. I installed ndiswrapper 1.52, but it did not do anything.

---

### Post by m60dude5 on 2008-04-03
I'm not an expert with ndiswrapper, but I believe to install the windows driver, you type
```

ndiswrapper -i LINK TO THE INF

```
in the terminal.
But, if it recognizes your card then you can shouldn't need to do that. Do you see up in the top right hand corner of the screen, there is a pair of computers? Click that and see if your wireless network is listed. If so, click it. If not, choose Manual configuration and then click the connections tab, right click wireless network, choose properties, uncheck "roaming mode enabled" enter your wireless info (you'll need the ip, router ip, your gateway, etc for this). Then click ok or close. Now chose the hosts tab and choose add. Add the ip address of your router and give it a name like router.
This should "enable" your card. But since it's already recognized, I wouldn't fool with ndiswrapper yet.
Let me know how that works.

---

### Post by cmnorton on 2008-04-03
> **smakaho2daflo said:**
> I cant find where is says hardware information. I see that in administration it is showing my wireless as a broadcom b43, but it is not enabled. When I try to enable it does nothing, even after a restart. I installed ndiswrapper 1.52, but it did not do anything.

You get to Hardware Information by clicking on System on the top menu, and then choosing Preferences and then Hardware Information.

---

### Post by smakaho2daflo on 2008-04-03
Is this the same in 8.04, because I don't see it.

---

### Post by ghost_ryder35 on 2008-04-03
```

sudo apt-get install bcm43xx-fwcutter
sudo modprobe bcm43xx

```
restart and all should be good.

If this does not work try removing the "b43-fwcutter" package via Synaptic Package manager and then **reissuing the above commands**.  I have the exact same card as you and I was able to just 
System, Administration, Hardware Drivers, and put the checkmark under enable next to the wireless card, rebooted and it worked perfectly fine.

---

### Post by smakaho2daflo on 2008-04-04
> **ghost_ryder35 said:**
> ```

sudo apt-get install bcm43xx-fwcutter
sudo modprobe bcm43xx

```
restart and all should be good.

If this does not work try removing the "b43-fwcutter" package via Synaptic Package manager and then **reissuing the above commands**.  I have the exact same card as you and I was able to just 
System, Administration, Hardware Drivers, and put the checkmark under enable next to the wireless card, rebooted and it worked perfectly fine.


You are the man. That worked great. Thanks so much.:)

---

