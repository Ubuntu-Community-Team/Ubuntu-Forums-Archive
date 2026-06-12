---
title: "No go for Gateway MT3708 wireless card"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by peaceforall on 2007-06-19
Hello, Any ideas about how to get my onboard Intel Pro wireless working?

---

### Post by scrooge_74 on 2007-06-19
Check if your card is supported 

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

which I think it should since Intel chips have good support.  Then go from there with any other questions hou have

---

### Post by peaceforall on 2007-06-20
Thank you Scrooge.  I checked some more and I have a Realtek 8185L which is supposed to work out of the box for Ubu 6.06.  I have 7.04.  How do I tell if it is working or not?

---

### Post by scrooge_74 on 2007-06-20
just type on a command line ifconfig and you should see references for your wired card and your wireless, also from System>Admin>Network you should be able to see which cards are recognize

Then since you have 7.04 network manager should be already install, so if it not on the bar on top open a terminal and type nm-applet to get it going it would simplify going online with a wireless card

---

### Post by peaceforall on 2007-06-20
I checked sys/admin/network and only wired connection and modem.


here is what I got from terminal

f@f-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:25:43:3F:7F  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::203:25ff:fe43:3f7f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1889 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1711 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1720990 (1.6 MiB)  TX bytes:272018 (265.6 KiB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

f@f-laptop:~$ c

what to do next?  This machine came bundled with vista which a immediately scrapped in favor of Ubu.

---

### Post by scrooge_74 on 2007-06-20
It would seem is not working, check this thread [http://ubuntuforums.org/showthread.php?t=416993&highlight=8185L](http://ubuntuforums.org/showthread.php?t=416993&highlight=8185L)

you are not alone

---

### Post by peaceforall on 2007-06-21
Thanks Scrooge.  Looks like I'm SOL until the next version of Ubu comes out.

---

### Post by scrooge_74 on 2007-06-21
You still have ndiswrapper and madwifi to play with and try to get it working

---

### Post by peaceforall on 2007-06-22
Scrooge,  Thank you for the encouragement.  I looked at wrapper and madfir, both require moderate programming skills that I don't have.   For now I'll watch visualizations of Jimi Hendrix playing watchtower.

---

### Post by dagowop on 2007-10-19
I don't have a working install of ubuntu running right now but the wireless driver just needs to be enabled in the black list.  Google the driver blacklist and you should be able to find it.  I know it was that easy for me and I have the exact same laptop.

---

