---
title: "Setting up netgear router"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by madddonkey255 on 2006-09-18
I was wondering how I could set up my netgear router, with encryption, through dapper.  I have no idea how to go about doing this.
Thanks,
Nolan

---

### Post by mejy on 2006-09-18
If you type ifconfig in a terminal, there should be an entry for gateway ip or something similar (I'm at work right now so I can't be sure).  Enter the IP listed for that in a web browser, and you should be able to configure it through a web interface.  After that, things should be pretty self explanitory but if not just google the netgear model and you should be able to find some sort of instructions (or you could just search for generic netgear instructions).

---

### Post by jpeddicord on 2006-09-18
[http://routerlogin.net](http://routerlogin.net) - This should take you directly to the Netgear management page. Click on Knowledge Base on the left for help on that.

You can connect to the router with WEP if you are on wireless. Go to System > Administration > Networking for both wired and wireless.

---

### Post by madddonkey255 on 2006-09-18
I tried that command and then cutting and pasting the numbers and kept getting "Server not found"  Here's what I get when I type that in:
> eth0      Link encap:Ethernet  HWaddr 00:0F:1F:17:11:51
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:1fff:fe17:1151/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:4726 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4763 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3399677 (3.2 MiB)  TX bytes:722253 (705.3 KiB)
          Interrupt:177

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:560 (560.0 b)  TX bytes:560 (560.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:0F:66:2E:82:1D
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:0 dropped:1 overruns:0 frame:0
          TX packets:3534 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:180 (180.0 b)  TX bytes:130758 (127.6 KiB)
          Interrupt:169 Memory:e0a7e000-e0a7e100

Thanks,
Nolan

---

### Post by mejy on 2006-09-18
I think 192.168.0.255 is what you should put in.

---

### Post by madddonkey255 on 2006-09-19
Thanks for the help, but the number gives me the same server not found page.  Also I'm an idiot and didn't specify that it's a wireless router that I'm trying to change the ssid and wep key so that my crafty neighbors don't steal my wireless.  Jerks.
Thanks,
Nolan

---

