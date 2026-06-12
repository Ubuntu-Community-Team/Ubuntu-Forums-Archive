---
title: "[SOLVED] Macbook Wifi"
date: 2008-06-14
forum: Apple Hardware Users
---

### Post by jessem on 2008-06-14
I installed Ubuntu 8.04 on a partition on my Macbook just to play around with.

So far I haven't been able to get wireless working, so that basically is keeping me from doing anything on it.

Ubuntu fails to connect to my ethernet, so I cannot download things directly as in [this guide](https://help.ubuntu.com/community/MacBook#head-e4a1f2cde8ad66bc01c97bfdadc85996ad80f688). However, I downloaded the tar.gz of the Madwifi driver in OS X and tried to follow the instructions from there in Ubuntu, but I had no luck. I get lots of errors when I try to do "make". The same thing happens with ndiswrapper.

Does anybody know what to do? I'm confused as to why the guides won't work as I am following line for line.

Edit: Here are my system specs if that helps.

Hardware Overview:

  Model Name:	MacBook
  Model Identifier:	MacBook2,1
  Processor Name:	Intel Core 2 Duo
  Processor Speed:	2 GHz
  Number Of Processors:	1
  Total Number Of Cores:	2
  L2 Cache:	4 MB
  Memory:	2 GB
  Bus Speed:	667 MHz
  Boot ROM Version:	MB21.00A5.B07
  SMC Version:	1.13f3
  Serial Number:	*removed&\*
  Sudden Motion Sensor:
  State:	Enabled

---

### Post by cyberdork33 on 2008-06-14
you have to install build-essentials in order to compile.

Why is your ethernet not working? There should be no issue with that.

---

### Post by jessem on 2008-06-14
Okay, that makes sense. I didn't really know what build-essentials was.

Is there a direct download that I can download to my Mac HD since my ethernet doesn't work? I really have no idea why it doesn't. It works fine on my PC and in OS X.

Edit: I found a .deb package for it. I'll give it a shot.

---

### Post by jessem on 2008-06-15
Okay, I was able to install the packages I need by adding the Ubuntu CD to the repositories. I was then able to install the Madwifi drivers.

But Ubuntu still acts as if I don't even have a wireless card. All that shows up in Network Manager is wired connection.

---

### Post by cyberdork33 on 2008-06-15
what is the output of 'ifconfig'

---

### Post by jessem on 2008-06-15
> **cyberdork33 said:**
> what is the output of 'ifconfig'

```
jesse@jesse-macbook:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:17:f2:d7:e5:4a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1938 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1938 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:97092 (94.8 KB)  TX bytes:97092 (94.8 KB)


```

However, I installed ndiswrapper and my driver file with ndisgtk. Ndisgtk shows that the driver is installed and it says I have the hardware required, but Network Manager fails to see my wireless card.

---

### Post by cyberdork33 on 2008-06-15
> **jessem said:**
> However, I installed ndiswrapper and my driver file with ndisgtk. Ndisgtk shows that the driver is installed and it says I have the hardware required, but Network Manager fails to see my wireless card.'ndiswrapper -l' should tell you if the driver is installed and working, but you still have to load the ndiswrapper module for it to work.

---

### Post by jessem on 2008-06-16
Ok, so my driver is installed and working, but "sudo modprobe ndiswrapper" results in "FATAL: module ndiswrapper not found" or something like that.

---

### Post by jessem on 2008-06-16
It appears that the ndiswrapper.ko file was not placed in the correct place, but I can't find it anywhere on my system. How can I get this file back?

**Edit: I was able to get the ndiswrapper.ko file and put it in the correct location, and now I am happy to say that I am posting this from Ubuntu. Thanks for the help :)**

---

