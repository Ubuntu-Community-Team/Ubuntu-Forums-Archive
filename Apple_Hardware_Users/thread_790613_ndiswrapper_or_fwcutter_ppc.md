---
title: "ndiswrapper or fwcutter?? ppc"
date: 2008-05-11
forum: Apple Hardware Users
---

### Post by spkays on 2008-05-11
I have an ibook g4 with bcm4306 wireless card and I'm running Hardy. I can't get a wired connection to the computer because my router, for some odd reason, does not recognize my computer when I connect to it.
I do have another laptop that I can use for an internet connection. I know broadcom is difficult to deal with and there are many threads on previous releases of Ubuntu. I did at one time have wireless on Feisty but I went through a number of OS's since then.
Anyway, I need help. I've tried many threads and websites.
Here's lshw output:
> 
*-network 
             description: Network controller 
             product: BCM4306 802.11b/g Wireless LAN Controller 
             vendor: Broadcom Corporation 
             physical id: 12 
             bus info: pci@0001:10:12.0 
             version: 03 
             width: 32 bits 
             clock: 33MHz 
             capabilities: bus_master cap_list 
             configuration: driver=b43-pci-bridge latency=16 module=ssb 

odule=ohci1394 
        *-network 
             description: Ethernet interface 
             product: UniNorth 2 GMAC (Sun GEM) 
             vendor: Apple Computer Inc. 
             physical id: f 
             bus info: pci@0002:20:0f.0 
             logical name: eth0 
             version: 80 
             serial: 00:0d:93:2a:c3:6e 
             width: 32 bits 
             clock: 66MHz 
             capabilities: bus_master ethernet physical 
             configuration: broadcast=yes driver=sungem driverversion=0.98 latency=16 maxlatency=64 mingnt=64 module=sungem multicast=yes 
  *-network DISABLED 
       description: Wireless interface 
       physical id: 1 
       logical name: wlan0 
       serial: 00:0d:93:89:76:cf 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g 

Here's ifconfig:
> eth0      Link encap:Ethernet  HWaddr 00:0d:93:2a:c3:6e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:41 Base address:0xcc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:1862 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:1862 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:93100 (90.9 KB)  TX bytes:93100 (90.9 KB) 


---

### Post by zeus123 on 2008-05-11
I have an ibook g4 and to be honest didnt have anyh luck with hardy and wifi. But I was using the beta hardy. I have had success with feisty and fwcutter. Make sure your router is set to b&g and not just g cos I dont think the airport card supports g.

---

### Post by spkays on 2008-05-11
> **zeus123 said:**
> I have an ibook g4 and to be honest didnt have anyh luck with hardy and wifi. But I was using the beta hardy. I have had success with feisty and fwcutter. Make sure your router is set to b&g and not just g cos I dont think the airport card supports g.

Thanks for the advice. When I had Feisty, I used the same router, so I know the router's setup is fine. It's something with Hardy (and most likely my inability to problem solve) that isn't working.

---

