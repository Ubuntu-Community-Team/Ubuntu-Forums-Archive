---
title: "Where's my IP ?"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by slink on 2007-10-15
Hi, 

that's my [FONT="Courier New"]ifconfig[/FONT] output:

```
eth0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xb400

eth0:avah Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:169.254.9.22  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0xb400

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:86 errors:0 dropped:0 overruns:0 frame:0
          TX packets:86 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6564 (6.4 KiB)  TX bytes:6564 (6.4 KiB)
```


Is it correct that I have no ifconfig eth0 IP ?

Is it correct that my IP is under eth0:avah ?

What is exactly eth0:avah ?

If i need to renew my IP ( as ipconfig/release in Windows ), do I need to 

[FONT="Courier New"]sudo dhclient eth0 [/FONT]

or

[FONT="Courier New"]sudo dhclient eth0:avah[/FONT] ?

---

### Post by aktiwers on 2007-10-15
inet addr:169.254.9.22

[www.whatismyip.com](www.whatismyip.com)

---

### Post by slink on 2007-10-15
Uh, I should had started from the beguinning...

That output is from a PC that has no internet connection. 

I am trying to understand if eth0:avah is as valid as eth0 and if that output appears to be *normal*...

---

### Post by ghost_ryder35 on 2007-10-15
the ip address of 169.254.0.0 is given out to computers who are set up to DHCP but fail to get an IP address from the DHCP server.  Overall the command looks perfectly normal if it is not hooked up any physical cables connecting it to a network

---

### Post by slink on 2007-10-15
> the ip address of 169.254.0.0 is given out to computers who are set up to DHCP but fail to get an IP address from the DHCP server. Overall the command looks perfectly normal if it is not hooked up any physical cables connecting it to a network


I lost connection during a lightning storm. The provider gave back service after 2 days. Since then I can only get 169.254.xxx.xxx adresses. 

They say my network card (ethernet) can be possibly damaged. 

Does that make sense ? 

I can
> [FONT="Courier New"]felix@ordinador:~$ lspci | grep Ethernet
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)[/FONT]
but
> [FONT="Courier New"]felix@ordinador:~$ route
Kernel IP routeing table
Destination Gateway Genmask Flags Metric Ref Use Iface
link-local * 255.255.0.0 U 0 0 0 eth0
default * 0.0.0.0 U 1000 0 0 eth0

felix@ordinador:~$ sudo mii-diag
Password:
Using the default interface 'eth0'.
Basic registers of MII PHY #1: 3000 7849 0000 8201 01e1 0000 0000 0000.
Basic mode control register 0x3000: Auto-negotiation enabled.
Basic mode status register 0x7849 ... 7849.
Link status: not established.
End of basic transceiver information.

felix@ordinador:~$ sudo mii-tool
eth0: no link[/FONT]

Just, how can I check if my card works properly ?

---

