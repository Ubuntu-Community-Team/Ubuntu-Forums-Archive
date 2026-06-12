---
title: "Help with router"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by Ali Cat on 2006-12-07
Hi, I've got the live edition of dapper. (Used to have it installed until Windoze killed my HDD) Anyway, I can't connect to the internet, I'm almost certain it's my router, as I could connect when I took my box to a friend's house, using the same Ethernet port. And I tried connecting with a PCI Ethernet port too. Any help appreciated.

My router is a Safecom Guru, my Ethernet port is built into my motherboard which is an ABIT KV8 PRO.

---

### Post by ]Nbx*cmD[ on 2006-12-07
could you paste your "ifconfig -a" output?
Did you try "sudo /etc/init.d/networking restart"?

---

### Post by Ali Cat on 2006-12-07
Will do as soon as I start up ubuntu, I'm having to use windoze at the moment. And no, I didn't, I'm completely new at linuxing.

---

### Post by Ali Cat on 2006-12-07
This is the results from ifconfig -a

```
eth0      Link encap:Ethernet  HWaddr 00:00:E8:12:DA:59
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xb000

eth1      Link encap:Ethernet  HWaddr 00:50:8D:70:CC:50
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:8dff:fe70:cc50/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3070 (2.9 KiB)  TX bytes:3133 (3.0 KiB)
          Interrupt:22 Base address:0xb400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.255.255.255
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:234 errors:0 dropped:0 overruns:0 frame:0
          TX packets:234 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:19567 (19.1 KiB)  TX bytes:19567 (19.1 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```
And I also tried sudo /etc/init.d/networking restart and it said ok, and it seemed to work a bit, but nothing would come up in FFx, don't know what to do.

---

### Post by ]Nbx*cmD[ on 2006-12-07
I guess you are using DHCP in your network,try to ping different machines, starting by your gateway (i suppose 192.168.1.1) and, if working, try to ping google's ip (for example) and, if working, try to ping [www.google.com](www.google.com)

```

# ping 192.168.2.1
# ping 64.233.183.103
# ping www.google.com

```

If the first one fails it may be a configuration problem in your network, which can come from either your router or PC.
If the first one works but the second one fails it may be a configuration problem, probably coming from your router.
If both first and second ones are working but third fails, that's for sure a problem with your DNS.

Let's test it and check what can we do :)

---

### Post by Ali Cat on 2006-12-07
How do I find out whether it's DHCP or static IP?

---

### Post by ]Nbx*cmD[ on 2006-12-07
well... you should check it in the router config, just type 192.168.1.1 in the URL bar of some web browser and you'll come with the router web, there you should be able to find it out.

---

