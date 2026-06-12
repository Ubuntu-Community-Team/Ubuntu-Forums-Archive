---
title: "Cannot access Internet"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by IronicLogic on 2007-09-16
Hi,

I've installed Ubuntu 7.04 as a dual boot with windows XP, and cannot access the internet through Ubuntu once it is installed on my computer. I have no problems logging on via windows, and I can also connect with the Ubuntu live CD. However, after installing the CD I cannot access the internet at all.

I have run the pppoe conf utility and entered the correct information, but when I open Firefox it does not load. My network adapter connects directly to an ADSL modem via ethernet cabling. My computer is a Sotec Winbook WV731 with a Sis 900-series chipset and has an AMD Sempron 2800+ CPU.

I've tried a few of the suggestions on the forum, like performing a manual configuration with sudo pon dsl-provider, but it makes no difference. I've also reset the network connection but that does not help. I really don't understand why it would work using the live CD but not work with the installed version.

I'm a complete beginner with Linux so any help would be greatly appreciated!

Thanks,
Greg

---

### Post by paulvas on 2007-09-16
Can you post ifconfig -a output?

---

### Post by IronicLogic on 2007-09-17
Hi, here is the ipconfig output:

eth0      Link encap:Ethernet  HWaddr 00:03:0D:33:B1:CE  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0 
          inet6 addr: fe80::203:dff:fe33:b1ce/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:4101 (4.0 KiB)  TX bytes:3698 (3.6 KiB) 
          Interrupt:21 Base address:0xd800  

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:84 (84.0 b)  TX bytes:84 (84.0 b) 

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:221.185.149.184  P-t-P:219.160.3.141  Mask:255.255.255.255 
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1454  Metric:1 
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:3  
          RX bytes:539 (539.0 b)  TX bytes:54 (54.0 b)

---

### Post by funkintelecky on 2007-09-17
I am experiencing the same issue, came to the forums for help as well.
When I am using the live CD my ethernet internet connection works wonderfully, but after the install nothing :/
I am behind a router and can view the router page 192.168.1.1 through firefox jsut fine, even my DSL modem page 182.168.0.1 comes up great, but no internet...

natuntu@natuntu-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0B:CD:0B:11:58
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:cdff:fe0b:1158/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1346 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1449 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:102797 (100.3 KiB)  TX bytes:88609 (86.5 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)


i can ping my router and dsl modem, but 100% packet loss pinging google

---

### Post by funkintelecky on 2007-09-17
WOOT! fixed!
i went into firefox like another thread said and disabled ipv6!

goddamn i love these forums, ubuntu pwns!

---

### Post by IronicLogic on 2007-09-17
Great, but can you post the thread so that I can see it too - how do I disable ipv6?

Thanks

---

### Post by Maestro23 on 2007-09-17
> **IronicLogic said:**
> Great, but can you post the thread so that I can see it too - how do I disable ipv6?

Thanks

Open new tab in FF.

In the address bar type: about:config

Scroll Down until you see: **network.dns.disableIPv6**

Double Left-click to toggle it to **TRUE.**

Close Browser and restart FF.

---

### Post by IronicLogic on 2007-09-17
Well, I've tried disabling ipv6 but no improvement. I disabled it both in Firefox with about:config and by using gedit /etc/modprobe.d/aliases. I still get no internet access. Can someone perhaps check out my ipconfig output and make a suggestion based on that?

I'll post it again here:

eth0      Link encap:Ethernet  HWaddr 00:03:0D:33:B1:CE  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0 
          inet6 addr: fe80::203:dff:fe33:b1ce/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:4101 (4.0 KiB)  TX bytes:3698 (3.6 KiB) 
          Interrupt:21 Base address:0xd800  

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:84 (84.0 b)  TX bytes:84 (84.0 b) 

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:221.185.149.184  P-t-P:219.160.3.141  Mask:255.255.255.255 
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1454  Metric:1 
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:3  
          RX bytes:539 (539.0 b)  TX bytes:54 (54.0 b) 

Thanks,
Greg

---

### Post by Crafty Kisses on 2007-09-17
Can you post the following output:
```
lspci
```

---

### Post by IronicLogic on 2007-09-17
Hi, here is the lspci output:

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03) 
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202 
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25) 
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller 
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] 
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0) 
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0) 
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) 
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) 
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller 
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91) 
00:06.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) 
00:09.0 CardBus bridge: O2 Micro, Inc. OZ711M1/MC1 4-in-1 MemoryCardBus Controller (rev 20) 
00:09.1 CardBus bridge: O2 Micro, Inc. OZ711M1/MC1 4-in-1 MemoryCardBus Controller (rev 20) 
00:09.2 System peripheral: O2 Micro, Inc. OZ711Mx 4-in-1 MemoryCardBus Accelerator 
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration 
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map 
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller 
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control 
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

---

### Post by IronicLogic on 2007-09-17
Well, I am posting this using the Ubuntu live CD - no problems accessing the internet, but when I try accessing the internet using the installed version then I cannot access the internet at all. 

If anyone knows why, and how I can fix this problem, then please post a reply. Please take a look at the info I posted above.

Thanks,
Greg

---

### Post by janesac1978 on 2007-11-22
I'm in same boat. My ethernet card is reading, cable modem is showing connectivity but I can't get an internet signal. Ihave done steps outlined in several forums and no luck.

---

