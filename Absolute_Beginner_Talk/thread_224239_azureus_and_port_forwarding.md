---
title: "azureus and port forwarding"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by qrm on 2006-07-27
Hi I have a Trendnet TW100-S4W1CAvF router and im trying to set up my port forwarding to get some decent speeds, atm i have about 9 kb/s per 22 seeds (61 in swarm) and thats kind of low :/ 

ifconfig tells me: ```
ats@zanzhu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:01:29:74:4A:A2
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::201:29ff:fe74:4aa2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:77203 errors:0 dropped:0 overruns:0 frame:0
          TX packets:81820 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:41434555 (39.5 MiB)  TX bytes:64715692 (61.7 MiB)
          Interrupt:201 Base address:0xa000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:19459 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19459 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1584696 (1.5 MiB)  TX bytes:1584696 (1.5 MiB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01
          inet addr:172.16.73.1  Bcast:172.16.73.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08
          inet addr:192.168.215.1  Bcast:192.168.215.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

so i guess my subnet mask should be 255.255.255.0; LAN ip should be 192.168.1.3 and default gateway (router) should be 192.168.1.1 . I set my eth0 connection in System -> Networking to static IP instead of DHCP and entered these values.

I followed [this]("http://www.portforward.com/english/routers/port_forwarding/Trendnet/TW100-S4W1CAvF/Azureus.htm") guide and chose the port for azureus to be @ 65533. But still my dl speed is very low. Where have I missed something or did something wrong?

---

### Post by gilgongo on 2006-07-27
If downloads are working at all, then that means your port forwarding is working and it's not an IP address setup problem (I don't think). 

Is azureus reporting any problems?

---

### Post by qrm on 2006-07-27
yes, azureus gives me an so called "error message" that i should check if my port (now ive set it to 6881 just to try) is being forwarded by my router or is not blocked

---

### Post by buyu on 2006-07-27
Do you have a software firewall?

Ray

---

### Post by qrm on 2006-07-27
I know that ubuntu comes with all ports closed (iptables?) and Ive aleady tried to open the ports from that

```
sudo iptables -I INPUT 1 -i eth0 -p tcp --tcp-flags SYN,RST,ACK SY N --dport 6881 -m state --state NEW -j ACCEPT
```

and

```
ats@zanzhu:~$ sudo iptables -I INPUT 1 -i eth0 -p udp --dport 65533 -m state --s tate NEW -j ACCEPT
```

---

### Post by buyu on 2006-07-27
might be easier to use firestarter from the repos which is a frontend to iptables

Ray

Edit

I got mine working today by picking a port (but not one between 6881-6999) and setting up _both_ udp and tcp port forwarding on my router and on my software firewall for this port

---

### Post by qrm on 2006-07-27
well, i installed firestarter and now cant figure out how to allow connections trough port 6881 - in events it shows that Bittorrent UDP connections trough port 6881 are blocked

---

### Post by jimmygoon on 2006-07-27
Azureus chooses a custom port that isn't in the usual bittorrent port range

---

### Post by qrm on 2006-07-27
> **jimmygoon said:**
> Azureus chooses a custom port that isn't in the usual bittorrent port range

explain please?

EDIT: read TFM and did a right click on an event and chose "Allow inbound service for everyone". Now it seems that its not blocking the connections on port 6881 but the speed in terribly low - it ranges from 20 kb/s to 50 b/s

---

### Post by jimmygoon on 2006-07-27
> **qrm said:**
> explain please?


well, when I started using Bittorrent there was a specific range that you had to have open to use it properly and to get good speeds. For whatever reason when I install azureus under linux, everytime I reinstall my pc and subsequently azureus, it chooses a different port. There are good reasons for this, primarily ISP's blocking bt traffic, but it is slightly annoying to try to change the port each time... anyways.... if you need to know which one is required... just goto the "Tools" menu bar and choose NAT Test... and look and see what port its testing ;)

good luck

---

### Post by qrm on 2006-07-27
thanks for the quick reply. It tests still the same port i enter in the prefrences dialog ;)

---

### Post by buyu on 2006-07-28
You can pick any port you like for your custom port, but it is best to pick one in the range [49152 - 65534]("http://www.azureuswiki.com/index.php/Port_is_blacklisted"). You can specify port to use in azureus under tools -> options -> connection -> Incoming TCP listen port. Whichever port you pick, you need to add a policy in Firestarter for it and also set up port forwarding (both tcp and udp) on your router for it

Ray

---

### Post by qrm on 2006-07-28
already knew that ;) Now i chose port 50000 and made a policy in firestarter and forwarded the port  in my router but the speed is still very low :/

---

### Post by sguart on 2006-07-28
> **qrm said:**
> already knew that ;) Now i chose port 50000 and made a policy in firestarter and forwarded the port  in my router but the speed is still very low :/

check azureus page for troubleshooting tips... is that port opend for tcp/udp traffic on your router? are you forwarding both tcp/udp traffic? are you saturating your uplink? are you allowing too many simultaneous connections? what's the avg swarm speed? you can find these out on azureus's support page.

---

### Post by qrm on 2006-08-13
gosh, i found out what was wrong, it wasnt about ubuntu, it wasnt about my router, it was all about my ISP who has closed all my ports. Need to get myself a new ISP or different connection

---

