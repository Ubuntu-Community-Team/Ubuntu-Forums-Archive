---
title: "Only seeing MAC on router"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by johnlh on 2007-02-24
I'm running dual boot xp - ubuntu 6.10.  Internet connection is fine, just a hair slower than XP.  I have my XP/Ubuntu wired to a Zoom X6 5590 gateway/router.  Also connected to the router (wired) is an HP 2610xi printer and two laptops (a 98se and XP - both wireless).
When  I check  the router client status, all the info - host name, mac, subnet, ip - are there for the laptop and printer, but only my network card MAC is showing for Linux.   What's the reason for this?
Thanx in advance - John:)

---

### Post by wireddad on 2007-02-24
So, you are not seeing an IP?  IFCONFIG produced just the MAC?  You are not connected.  Is this a new install?  My laptop has both wired and wireless too and had to turn wired off to use the wireless.  An then make sure the correct driver is loaded and configure the connection.

---

### Post by johnlh on 2007-02-24
Wireddad - Thanx for replying.  New, and first for me, install (02/21) w/ linux.  The install went fairly smooth.   I learn by doing - so I research, try, sometimes goof, and research and try again.  I keep lots of back ups! On to the -
ifconfig:
jubuntu@jubuntu-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0B:6A:BB:E7:90  
          inet addr:10.0.0.5  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:6aff:febb:e790/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12782 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12083 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10815786 (10.3 MiB)  TX bytes:1491135 (1.4 MiB)
          Interrupt:193 Base address:0xd400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1979 (1.9 KiB)  TX bytes:1979 (1.9 KiB)

Laptops and my pc (in both xp/linux modes) have active connections.  I can ping linux from the laptops and vice vesa.  I haven't even attempted to set up the file sharing... baby steps.  I just thought it odd no ip etc info for linux except MAC on router stat page.  - John

---

### Post by wireddad on 2007-02-25
I see.  So I mis-understood the original post.  Sorry.  Just looked at my router quickly and only see MAC too.  Have to look further.

---

