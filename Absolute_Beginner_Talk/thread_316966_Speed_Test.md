---
title: "Speed Test"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by Drakkor on 2006-12-11
Those of you dual-booting, in using the Speakeasy Speed Test 
[http://www.speakeasy.net/speedtest/](http://www.speakeasy.net/speedtest/)
Does anyone else see a huge difference in download speed ?
I use Comcast high speed cable, and the difference with Ubuntu and Windows
is about 3mb/s on Ubuntu, and over 6mb/s on Windows :-k

---

### Post by orb9220 on 2006-12-11
Sounds like a comcast thing. Since I ran the test on a free-wifi spot I use for xp and ubuntu. And they both are at around 1100-1200 mbs which is normal for my setup.

---

### Post by AndrewB on 2006-12-11
Both my XP and Ubuntu boxes get almost identical UL/DL speeds on the same network/router/DSL modem.

2350 Down
450 Up

and the XP box is wireless G too boot!

---

### Post by Drakkor on 2006-12-11
First XP speed,then Ubuntu speed:

---

### Post by PriceChild on 2006-12-11
My Ubuntu always got higher on my usb adsl modem or wireless.

---

### Post by Doug11 on 2006-12-11
Mine run almost identical with wireless. Maybe a tad faster with ubuntu. Drakkor, are you a moderator from another forum community?

---

### Post by Drakkor on 2006-12-11
Lol,Doug,not that I recall,if I am, I have been seriously derelict,lol :D

---

### Post by amd-64 on 2006-12-11
I am wondering about this too. I always get different results. Consider the case below, when running Windows on a VM I get better download rates. The thing is, my ISP caps the speed at 256 kbps for the lite speed DSL, which I have. I would love to hear a good explanation for this. I could run more tests if needed.

**Results from Edgy on AMD64 machine **
Download Speed: 251 kbps (31.4 KB/sec transfer rate)
Upload Speed: 253 kbps (31.6 KB/sec transfer rate)
[B]

Results from Windows 2000 in VMPlayer running on Edgy on the same machine [/B]
Download Speed: 568 kbps (71 KB/sec transfer rate)
Upload Speed: 192 kbps (24 KB/sec transfer rate)

Note: tests were repeated twice, from the same server. No other processes were using the net.

---

### Post by PriceChild on 2006-12-12
amd-64 I think you'd get a MUCH fairer comparison if you compared the two on host OSs... VMs will manage their networking differently.

---

### Post by nixclusive on 2006-12-12
Same speeds on both the OS. However web browsing is really enhanced with Squid Proxy installed in Ubuntu. ;-)

---

### Post by amd-64 on 2006-12-13
> **PriceChild said:**
> amd-64 I think you'd get a MUCH fairer comparison if you compared the two on host OSs... VMs will manage their networking differently.

I agree, I also dual-boot and found similar ul and dl rates on both xp and edgy. I only have a significant difference when I compare between a vm and the host OS. 

I still would like to know if anyone else is seeing an improvement with vmware and any ideas how the vm gets around the ISP cap on bandwidth. I have an idea but it has not been tested. If the limit is 256 kbps per nic, even that I have a router/firewall, it is possible that the bridged network connection between the vm and the host OS is treated as two clients and I may be doubling the bandwidth. Is this even possible.

---

### Post by gn2 on 2006-12-14
Just for amusement I tried the speakeasy test, with various results depending on location of server.

New York was twice as fast as Seattle for example, but when I used one closer to home (UK), the results were twice as fast as New York

Anyone know why the speed varies with distance?

Here's a UK version if you want to try: [http://www.speedtest.bbmax.co.uk/](http://www.speedtest.bbmax.co.uk/)

---

