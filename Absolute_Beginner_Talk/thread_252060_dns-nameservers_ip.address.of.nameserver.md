---
title: "dns-nameservers ip.address.of.nameserver"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by hollym on 2006-09-06
I was referenced the following link:
[https://wiki.ubuntu.com/StaticDnsWithDhcp?highlight=%28DHCP%29](https://wiki.ubuntu.com/StaticDnsWithDhcp?highlight=%28DHCP%29) 

and am wondering which number is the "ip.address.of.nameserver" referred to in this line.

dns-nameservers ip.address.of.nameserver

when i run ipconfig /all in windows xp i receive the following numbers

IP Address        
Subnet Mask 
Default Gateway
DHCP Server
DNS Servers

Cheers in Advance

---

### Post by Uluen on 2006-09-06
Ask your ISP, they should give you the IPs of their DNS servers.

---

### Post by hollym on 2006-09-06
i have the numbers mentioned and have followed the instructions according to the link 
[https://wiki.ubuntu.com/StaticDnsWit...ght=%28DHCP%29](https://wiki.ubuntu.com/StaticDnsWit...ght=%28DHCP%29) 
but still no internet ...
im sure it is not that hard, but i just cant see what the problem is ...
any ideas?

---

### Post by Uluen on 2006-09-06
What are you trying to do, make your DHCP server assign these DNS servers to the clients?

No internet you say, you can't ping 64.233.187.99 (google.com)?
What's the output of ```
$ route
```, ```
$ ifconfig
``` and ```
$ cat /etc/resolv.conf
```?

---

### Post by Jussi Kukkonen on 2006-09-06
> and am wondering which number is the "ip.address.of.nameserver" referred to in this line.

dns-nameservers ip.address.of.nameserver

when i run ipconfig /all in windows xp i receive the following numbers

IP Address
Subnet Mask
Default Gateway
DHCP Server
DNS Servers

ip.address.of.nameserver == DNS Servers

---

### Post by hollym on 2006-09-06
i have no idea what im doing to tell you the truth. What I would like to happen is to see internet working. It seems the network is ative as there is some activity. 
However, internet is not working.
I like in a commercial/residential building that has broadband hardwired into every apartment. I simply plug it into the wall and it works (well, in Windows anyway)
However, after installing Ubuntu i have not got any response from the internet.
very frustrated at this stage, not sure what to do. Seems that the hardware is ok.

The output $route
$route 
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref

$ifconfig
Link encap:Ethernet  HWaddr 00:0C:6E:11:1B:3B
inet6 addr: fe80::20c:6eff:fe11:1b3b/64 Scope:Link
UP BROADCAST MULTICAST  MTU:1500  Metric:1
RX packets:1633 errors:0 dropped:0 overruns:0 frame:0
TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:97980 (95.6 KiB)  TX bytes:4230 (4.1 KiB)
Interrupt:201 Base address:0x9800lo

Link encap:Local Loopback
inet addr:127.0.0.1  Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING  MTU:16436  Metric:1
RX packets:135 errors:0 dropped:0 overruns:0 frame:0
TX packets:135 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:10196 (9.9 KiB)  TX bytes:10196 (9.9 KiB)

Any help would be appreciated.


and the thrid one, well I dont know about that. I typed in the command and it just says: no such file or directory. Did a search for a file of that name, but nothing.

---

### Post by Uluen on 2006-09-06
Well it's not working because you have no route to a gateway and no IP address to use to the gateway you don't have :D

Do you use DHCP in WinXP?

Click System -> Administration -> Networking. Check properties on your network interface, is DHCP enabled?

---

### Post by hollym on 2006-09-06
not sure if I use DHCP in Windows. Is that the default system setting? I've never had to do anything in Windows to get the internet running. I just plug the cable into the wall socket and it works.

Yes, DHCP is enabled in Networking. I have also tried to use static IP and type in the numbers returned by the ipconfig /all command. Still no joy with that. 

there is a small amount of traffic on the network, but internet still not running. 

I do have a static DNS if that is of any interest and also I know the IP address of the DHCP server.

hmmmm ....

---

