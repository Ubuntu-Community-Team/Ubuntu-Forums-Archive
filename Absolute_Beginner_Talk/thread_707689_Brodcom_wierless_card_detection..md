---
title: "Brodcom wierless card detection."
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by 38-crazy on 2008-02-25
I just installed Ubuntu and an trying to access my wireless network. I am running a AMD 64x dual core notebook, with the corresponding 64x Ubuntu installed.The thing is, I am not even sure that the Ubuntu is detecting my wireless card. How do I find my wireless card on Ubuntu?

---

### Post by wormser on 2008-02-25
It would help us if we knew the exact model of the card.  Applications> Accessories> Terminal.  Post the details of the card.

```
lspci
```

I do not use 64 bit.  But, I got my Broadcom card working with Restricted Drivers.  I am not sure it will work with a 64 bit system.  System> Administration> Restricted Drivers Manager.

---

### Post by Woody@N87 on 2008-02-25
I'm no expert in this but, a simple test would be to go to the networking icon at the top of the window.  if you right click on it and you only see "Enable Networking" as opposed to two options "Enable Networking" and "Enable Wireless" then the OS probably doesn't see the card.

You could also go to System->Administration->Network and see if a wireless connection is an option.  Again, if it's not the OS probably isn't seeing the card.

---

### Post by northern lights on 2008-02-25
It might be helpful, to read [this]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy?highlight=%28bcm%29%7C%2843xx%29") also.

[EDIT]
Sorry, wrong link - updated.
[/EDIT]

---

### Post by 38-crazy on 2008-02-25
Broadcom Corporation BCM4310. I guess that answers the question if Ubuntu sees it.

So where do I go from here?

---

### Post by Victormd on 2008-02-25
Try this thread:
[http://ubuntuforums.org/showthread.php?t=572005](http://ubuntuforums.org/showthread.php?t=572005)

Note: if lspci didn't see it, try lsusb

---

### Post by Sordelka on 2008-02-25
FIrst describe what did you do, if the case may be. If not, in terminal type:

```
iwlist scanning
``` 

and output it here.

also try this: [http://ubuntuforums.org/showthread.php?t=572005](http://ubuntuforums.org/showthread.php?t=572005)

---

### Post by northern lights on 2008-02-25
This [HowTo]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy?highlight=%28bcm%29%7C%2843xx%29") should solve your problem. I had wanted to post it earlier, but copy/pasted the wrong like. My bad. If you need guidance on that HowTo, post. Cheers

---

### Post by 38-crazy on 2008-02-25
I typed in "iwlist scanning" and it said that it wasn't supported on my eth0, or my pppo (I'm going to guess that is my DSL modem). I will look though the HowTo, and see if there is any solution to the problem there.

---

### Post by 38-crazy on 2008-02-25
Upon a third and a cautionary fourth look, I find no evidence that Ubuntu sees the card. I am not finding the wireless option in my System> Admin> network, nor anywhere else for that matter.

---

### Post by Papa-san on 2008-02-25
Can you post the results of ifconfig and iwconfig, pls?

eth0 is your ethernet card and ppp0 is your internal modem. It isn't showing the wireless card, so you may not have the drivers. make sure to look through the links these posters gave you.

---

### Post by 38-crazy on 2008-02-25
ifconfig
eth0      Link encap:Ethernet  HWaddr 94:0F:40:72:1D:00  
          inet6 addr: fe80::960f:40ff:fe72:1d00/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12473 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11461 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11078605 (10.5 MB)  TX bytes:1822403 (1.7 MB)
          Interrupt:23 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:128 errors:0 dropped:0 overruns:0 frame:0
          TX packets:128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9296 (9.0 KB)  TX bytes:9296 (9.0 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:216.8.149.167  P-t-P:216.8.136.153  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:4989 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4536 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:4332335 (4.1 MB)  TX bytes:649645 (634.4 KB)

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ppp0      no wireless extensions.



I looked though the HowTo, and am slightly confused as to which drivers I need1.Do i download then from the manufacturers website?

---

### Post by Sordelka on 2008-02-25
Consequently, a question imposes:

Did you ever try to install ndiswrapper with windows drivers for your card? If not, google it and one their site, they have all the documentations you need.

---

### Post by Papa-san on 2008-02-25
I have found that ndiswrapper tends to be a better way of dealing with the bcm43xx issues.
The 'ndiswrapper' link in my signature line is pretty comprehensive and easy enough for someone with little linux experience to muddle their way through it. Give that a shot, and if it doesn't work, post back here, and I'll see what else I can do...

---

### Post by Sordelka on 2008-02-25
> **38-crazy said:**
> ifconfig
eth0      Link encap:Ethernet  HWaddr 94:0F:40:72:1D:00  
          inet6 addr: fe80::960f:40ff:fe72:1d00/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12473 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11461 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11078605 (10.5 MB)  TX bytes:1822403 (1.7 MB)
          Interrupt:23 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:128 errors:0 dropped:0 overruns:0 frame:0
          TX packets:128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9296 (9.0 KB)  TX bytes:9296 (9.0 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:216.8.149.167  P-t-P:216.8.136.153  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:4989 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4536 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:4332335 (4.1 MB)  TX bytes:649645 (634.4 KB)

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ppp0      no wireless extensions.



I looked though the HowTo, and am slightly confused as to which drivers I need1.Do i download then from the manufacturers website?

Drivers should always be taken from two places:

1. Manufacturers site
2. If you have a cd, take them from there

---

### Post by Papa-san on 2008-02-25
Right.
Download the drivers from the manufacturer or get them off the CD. You will get the standard .exe file extension. use archive manager to extract the drivers .inf and .sys to someplace you can find them. This particular driver is going to give you the choice between bcmwl5 or bcmwl5a The link I showed you on ndiswrapper has a place to find which one you need.

You will need to run ```
lshw -n
```and it will show you which card and what revision number it is. That rev number is what determines which driver...

---

### Post by Victormd on 2008-02-25
> **38-crazy said:**
> I looked though the HowTo, and am slightly confused as to which drivers I need1.Do i download then from the manufacturers website?

Check this link:

[https://help.ubuntu.com/community/Wi...ndiswrapper%29](https://help.ubuntu.com/community/Wi...ndiswrapper%29)

it has everything you might need, including installing with ndiswrapper, even if you have to compile from source (which is what worked for me - I have a broadcom 4328) and has the links to the drivers. The original file is 52Mb (gets it from Dell - I have an HP laptop and it worked fine!) but the person who created the How To removed all the unnecessary stuff and brought it down to a few kb...

---

