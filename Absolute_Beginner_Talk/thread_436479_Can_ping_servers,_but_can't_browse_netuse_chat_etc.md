---
title: "Can ping servers, but can't browse net/use chat etc"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by ferahl on 2007-05-07
Hey,

I'm using kubuntu 7.04

I have a sagem fast 800 modem, so I've configure ueagle-atm and its recognizing my modem & connecting to the net just fine.

from the console if i ping a server, like google.com I get the correct ping responses back

HOWEVER

when i try to browse the net, connect to IM etc its not working.

If i check Network Interfaces I have two interfaces: eth0 + eth1, under Domain Name System the 2 nameserver entries are correct.

For connection info check my post lower down

------------------------------

I think that when I browse the net its trying to use eth0 or eth1 perhaps? Is it strange the network settings->network interfaces only returns eth0 +eth1 and no pp0 interface?

really appreciate any help, cant wait to have linux finally connected to the net lol ;/

---

### Post by tbg58 on 2007-05-07
What is the output of ifconfig?

---

### Post by Happy_Man on 2007-05-07
Yay! I had this exact problem! Right-click on the ethernet icon down in the taskbar, and choose manual configuration. Make sure that your IP address and settings are ok. For example, my router punches through 192.168.x.xxx, but the IP gateway was set at 0.0.0.0. So I just had to fix that and everything's ok! Hope this helps!

---

### Post by ferahl on 2007-05-07
happy man, do u mean the ico i can right click on -> manual configuration... -> Routes tab -> enter ip in edit box there? i tried that and it wasnt working but ill try once more now

@tbg58 - im gonna have to put this here later cause i dont have my usb stick to xfer the dump to my laptop which has internet lol (and its a lot to type - 6 entries). thanks thou and ill post back here tomorrow with it.

---

### Post by ferahl on 2007-05-08
K here is my network info:

eth0      Link encap:Ethernet  HWaddr 00:50:70:23:08:32
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0x8000

eth1      Link encap:Ethernet  HWaddr 00:50:70:2A:08:2D
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0x9000 Memory:fd000000-fd020000

eth0:avah Link encap:Ethernet  HWaddr 00:50:70:23:08:32
          inet addr:169.254.2.180  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0x8000

eth1:avah Link encap:Ethernet  HWaddr 00:50:70:2A:08:2D
          inet addr:169.254.2.176  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Base address:0x9000 Memory:fd000000-fd020000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2464 (2.4 KiB)  TX bytes:2464 (2.4 KiB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:80.47.103.192  P-t-P:212.74.111.219  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:3132 (3.0 KiB)  TX bytes:3035 (2.9 KiB)


Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
lon-2-llu.as910 *               255.255.255.255 UH    0      0        0 ppp0
link-local      *               255.255.0.0     U     0      0        0 eth0
link-local      *               255.255.0.0     U     0      0        0 eth1
default         *               0.0.0.0         U     0      0        0 ppp0


network config:
[http://elitepicturehost.com/viewpic.php?code=69d7ca9091eed68a56e0af1b2c4b5a5e](http://elitepicturehost.com/viewpic.php?code=69d7ca9091eed68a56e0af1b2c4b5a5e)
[http://elitepicturehost.com/viewpic.php?code=f550491cf99a389725fa20b7e82725bf](http://elitepicturehost.com/viewpic.php?code=f550491cf99a389725fa20b7e82725bf)
[http://elitepicturehost.com/viewpic.php?code=30098595d8fff6f46d62e1a2e4dbb1fa](http://elitepicturehost.com/viewpic.php?code=30098595d8fff6f46d62e1a2e4dbb1fa)


hope some1 knows how i can resolve this ridiculous problem, thanks!

---

### Post by ferahl on 2007-05-08
bump (sry, really wanna move from win to unix)

---

### Post by josephfley on 2008-01-10
I have the same problem, we have a win xp machine sharing the connection, my pc get a ip assigned and I can ping web servers and that works, but I cant browse o.O, it works in windows, but as soon as I boot on kubuntu it stops working -_-

---

### Post by kyphi on 2008-01-10
You might find an answer here -

[http://ubuntuforums.org/showthread.php?t=201127](http://ubuntuforums.org/showthread.php?t=201127)

---

