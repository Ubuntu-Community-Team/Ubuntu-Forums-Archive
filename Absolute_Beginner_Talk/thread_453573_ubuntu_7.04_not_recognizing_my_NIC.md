---
title: "ubuntu 7.04 not recognizing my NIC"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by rallenk on 2007-05-24
I have recently installed 7.04 from Live CD and followed instructions to re-partion my hard drive in order to have both XP and Ubuntu on my PC which has plenty of resources. all works fine except......

I have cable internet service and it seems Ubuntu isn't recognizing the NIC. No internet service. 
I have it set for dhcp and networking is set properly...What next? 

Should be something simple...right?;)

---

### Post by louieb on 2007-05-25
Thats strange. I throw in just any old NIC I have around  and Ubuntu or any other Linux flavor picks it up and connects to net no problem. But I'm on DSL and my modem is connected to a router. Maybe you need  to run ppoe config 
open applications>accessories>terminal and enter ```
ifconfig 
``` 

if you have an entry for **eth0** thats you card if all you have is an **lo **then its not picking up your card. By example here is what mine looks like 
```

lou@blackboxu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:2F:D5:4E:0A
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:2fff:fed5:4e0a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:71604 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57772 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:48115707 (45.8 MiB)  TX bytes:6609764 (6.3 MiB)
          Interrupt:233 Base address:0x8400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:472 (472.0 b)  TX bytes:472 (472.0 b)



```

---

### Post by rallenk on 2007-05-25
Yep...It shows my Ethernet card.....
But when I open Firefox and attempt to
browse anywhere, I get the message that
basically I'm not connected...You know
the White Box message I speak of right?

Suppose I have a bad copy of Firefox? 
It was in the install. I used LiveCD to
Install and partion HD in order to Dual
Boot with XP

---

### Post by louieb on 2007-05-25
try disabling ipv6 in Firefox in address bar enter [B]about:config
[/B]look for **network.dns.disableIPv6  **and set it to [B]true.

[/B]if that doesn't help try pinging Google ```
ping -c3 www.google.com
```results shoud end like this if they do then there is something wrong with firefox.
> 
--- [www.l.google.com]("http://www.l.google.com") ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2011ms
last but probably first look in the ifconfig for eth0 and see if you have an ip address  it will look something like this [B] inet addr:192.168.1.3
[/B]
if not then the modem is not talking to the NIC and I'm out of gas. You'll just have to compare you windows internet setting and duplicate them in Ubuntu. Good luck.

---

