---
title: "iMac g5 plastic, intel, Linux Mint. No wifi"
date: 2012-09-20
forum: Any Other OS
---

### Post by palito1980 on 2012-09-20
I have iMac G5. Ubuntu does not want to install on it, Linux Mint 13 installs without any problems. The biggest issue is that even when I install restricted driver for my wifi card I cannot make it work. Any help with that?

My iMac is probable G5 from 2007. It has 1.83 Intel processor and 512 RAM.

---

### Post by 2blue on 2012-09-20
Wifi drivers can be difficult. Have you identified your card? There might be a few options to try out. 

If you plan on using the computer I can recommend adding a bit more RAM if you can. I added 1GB of RAM to my old G4 iBook (ppc) which originally had 512MB RAM. Processor is only 1.42GHz. Even though RAM usage is hardly ever above 400-500MB whatever applications I run, swap doesn`t kick in anymore. It looks like the system alway keep some RAM free to run, and it seems like an advantage not to run on swap. It`s not major, but it runs noticeably smoother.

---

### Post by palito1980 on 2012-09-21
mintwifi gives me something like that:

-------------------------
* I. scanning WIFI PCI devices...
  -- Broadcom Corporation BCM4311 802.11a/b/g (rev 01)
      ==> PCI ID = 14e4:4312 (rev 01)
-------------------------
* II. querying ndiswrapper...
-------------------------
* III. querying iwconfig...
lo        no wireless extensions.

eth0      no wireless extensions.

-------------------------
* IV. querying ifconfig...
eth0      Link encap:Ethernet  HWaddr 00:17:f2:d1:50:a3  
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
          RX packets:47 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4600 (4.6 KB)  TX bytes:4600 (4.6 KB)

-------------------------
* V. querying DHCP...
-------------------------
* VI. querying nslookup google.com...
;; connection timed out; no servers could be reached

---

### Post by Perfect Storm on 2012-09-21
Moved to Other OS/Distro Talk.

---

### Post by mips on 2012-09-21
> **palito1980 said:**
> Ubuntu does not want to install on it, Linux Mint 13 installs without any problems. The biggest issue is that even when I install restricted driver for my wifi card I cannot make it work. Any help with that?

Do you mean Ubutnu does not install at all but Mint does and that's what you are using now although in Mint the wifi does not work?

I'm assuming the above is correct and why you posted in other os forum.

Did you try the alternate ubuntu image, [64-bit Mac (AMD64) alternate install CD]("http://cdimage.ubuntu.com/releases/12.04.1/release/ubuntu-12.04.1-alternate-amd64+mac.iso")?

---

