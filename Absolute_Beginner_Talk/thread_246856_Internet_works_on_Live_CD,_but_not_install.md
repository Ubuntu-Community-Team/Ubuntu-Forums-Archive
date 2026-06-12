---
title: "Internet works on Live CD, but not install?"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by squelly on 2006-08-29
I've been working with the Live CD for Ubuntu 6.06, trying it out and really liking it. Firefox works great, and I can get out to the internet just fine via the IBM EtherJet Cardbus PCMCIA network adapter. 

However after I ran the install, and boot up Ubuntu from the HDD, Firefox does not work, and I do not get assigned an IP address.

Resetting the router had no effect, and rebooting the PC has had not effect. 

On repeated tries the LiveCD works, the HDD install does not. I have made no alterations to the system. 

Can you think of why that might be?

---

### Post by squelly on 2006-08-29
Not sure if this helps...

Using a windows machine plugged into the same router as reference, I set up a static IP address on the ubuntu box. 

I can ping the windows box, albeit with a really high loss rate. 

Pinging the windows box from Ubuntu, the following is one of the pings, chosen at random
64 bytes from 192.168.1.3 icmp_seq=16 ttl=128 time=20018 ms

And this summary information
51 packets transmitted, 32 received, 37% packet loss, .....

I cannot ping an internet host.

---

### Post by mejy on 2006-08-29
> **squelly said:**
> Not sure if this helps...

Using a windows machine plugged into the same router as reference, I set up a static IP address on the ubuntu box. 

I can ping the windows box, albeit with a really high loss rate. 

Pinging the windows box from Ubuntu, the following is one of the pings, chosen at random
64 bytes from 192.168.1.3 icmp_seq=16 ttl=128 time=20018 ms

And this summary information
51 packets transmitted, 32 received, 37% packet loss, .....

I cannot ping an internet host.

Can you ping your router or open up its control panel?  What output do you get from typing ifconfig into a terminal?

Edit:  that's a ping of more than 20 seconds - could it be a router configuration problem?

---

### Post by squelly on 2006-08-30
THanks for the reply. I not inclined to believe it is a router problem. The reason I say this, is when I run ubuntu from the live CD, the pings are all under 2ms, and can get to the internet just fine.

Here is what I see from ifconfig from the LIVE CD:

eth0  Link encap:Ethernet HWaddr: 00:04:AC:64:75:AB
      inet addr: 192.168.1.6 Bcast:192.168.1.255 Mask:255.255.255.0
      inet6 addr: fe80::204:acff:fe64:75ab/64 Scope:Link
      UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
      RX Packets:290 errors:0 dropped:0 overruns:0 frame:0
      TX packets:113 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:1000
      RX bytes:40527 (39.3 KiB) TX bytes:10848 (10.5 KiB)
      Interrupt:11 Base Adress:0x1800

When I boot from the Hard Drive, and type ifconfig i get:

eth0  Link encap:Ethernet HWaddr: 00:04:AC:64:75:AB
      inet addr: 192.168.1.6 Bcast:192.168.1.255 Mask:255.255.255.0
      inet6 addr: fe80::204:acff:fe64:75ab/64 Scope:Link
      UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
      RX Packets:0 errors:0 dropped:0 overruns:0 frame:0
      TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:1000
      RX bytes:0 (0.0 KiB) TX bytes:1434 (1.4 KiB)
      Interrupt:11 Base Adress:0x1800


Is there any way to retain the network config from the live CD, and use that for the installed version?

---

### Post by mejy on 2006-08-30
This is very strange, because according to this the configuration on the Live CD and from the hard disk is identical (the bits that differ just show how much network usage the interface has seen).  Have you tried reinstaling from the live cd, or maybe even using the alternate install cd?

---

### Post by squelly on 2006-08-30
Yeah, it is really weird. I've reinstalled from the LiveCD, I downloaded and tried the install from the Alternate CD, with no change. 

I even tried kubuntu, hoping that might do something differently. Again, same thing. The Kubuntu Live CD worked great. A Kubuntu install booting from the HDD can't get out. 

](*,)

---

