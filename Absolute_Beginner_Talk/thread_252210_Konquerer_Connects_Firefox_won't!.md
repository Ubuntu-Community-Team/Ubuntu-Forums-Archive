---
title: "Konquerer Connects Firefox won't!"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by cregy on 2006-09-06
Hi

Up until Friday my Kubuntu box was connecting fine. On Monday I return to work to discover a weird problem. Konquerer will connect to the net and I can collect mail but I cannot connect via Firefox and I cannot connect via apt-get.

I am using a router linked to a d-link switch.

I installed a second computer today and guess what that can't connect. My Mac can with no problems.

Ifconfig and route show this:
ifconfig
eth0 * * *Link encap:Ethernet *HWaddr 00:14:6C:81:F1:E8
* * * * * inet addr:192.168.1.4 *Bcast:192.168.1.255 *Mask:255.255.255.0
* * * * * inet6 addr: fe80::214:6cff:fe81:f1e8/64 Scope:Link
* * * * * UP BROADCAST RUNNING MULTICAST *MTU:1500 *Metric:1
* * * * * RX packets:9347 errors:0 dropped:0 overruns:0 frame:0
* * * * * TX packets:9376 errors:0 dropped:0 overruns:0 carrier:0
* * * * * collisions:0 txqueuelen:1000
* * * * * RX bytes:2278807 (2.1 MiB) *TX bytes:840230 (820.5 KiB)
* * * * * Interrupt:193 Base address:0xa000

lo * * * *Link encap:Local Loopback
* * * * * inet addr:127.0.0.1 *Mask:255.0.0.0
* * * * * inet6 addr: ::1/128 Scope:Host
* * * * * UP LOOPBACK RUNNING *MTU:16436 *Metric:1
* * * * * RX packets:11 errors:0 dropped:0 overruns:0 frame:0
* * * * * TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
* * * * * collisions:0 txqueuelen:0
* * * * * RX bytes:1290 (1.2 KiB) *TX bytes:1290 (1.2 KiB)

route
Kernel IP routing table
Destination * * Gateway * * * * Genmask * * * * Flags Metric Ref * *Use Iface
192.168.1.0 * * * * * * * * * * 255.255.255.0 * U * * 0 * * *0 * * * *0 eth0
default * * * * mygateway1.ar7 *0.0.0.0 * * * * UG * *0 * * *0 * * * *0 eth0

My router is on 192.168.1.1.

Can anybody help please?

Thanks

Rich
[http://www.cregy.co.uk/](http://www.cregy.co.uk/)

---

### Post by bigken on 2006-09-06
in the firefox address bar type about:config then in the filter type ipv6 and its value from fales to true just double click it hope this helps ;)

---

### Post by cregy on 2006-09-06
> **bigken said:**
> in the firefox address bar type about:config then in the filter type ipv6 and its value from fales to true just double click it hope this helps ;)

Hi

Thanks that was brilliant and it works fine but doesn't fix the apt-get problem!

Any ideas please?

Thanks

Rich

---

### Post by msandersen on 2006-09-06
It's most likely an IPv6 problem. Your ISP may have changed something on their end. Do a search here. For instance [this post]("http://www.ubuntuforums.org/showthread.php?t=246185&page=2"). 
here's another one:
[http://www.ubuntuforums.org/showthread.php?t=168204&highlight=ipv6+konqueror+Firefox](http://www.ubuntuforums.org/showthread.php?t=168204&highlight=ipv6+konqueror+Firefox)
Wiki page on disabling IPv6:
[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

The problem is whereas Linux is IPv6-enabled and tries that first, very few places has enabled it, and it can cause some confusion in the system.

---

### Post by cregy on 2006-09-06
> **msandersen said:**
> It's most likely an IPv6 problem. Your ISP may have changed something on their end. Do a search here. For instance [this post]("http://www.ubuntuforums.org/showthread.php?t=246185&page=2"). 
here's another one:
[http://www.ubuntuforums.org/showthread.php?t=168204&highlight=ipv6+konqueror+Firefox](http://www.ubuntuforums.org/showthread.php?t=168204&highlight=ipv6+konqueror+Firefox)
Wiki page on disabling IPv6:
[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

The problem is whereas Linux is IPv6-enabled and tries that first, very few places has enabled it, and it can cause some confusion in the system.

Hi

Thanks for that. I have completed this. I still cannot connect to apt-get update. The servers list is coming up with "Network unreachable".

Firefox connects no problems now and the ip a | grep inet6 shows nothing.

Any ideas please?

Thanks

Rich

---

### Post by cregy on 2006-09-07
Hi Guys

The journey continues. Having sorted out ipv6 the only area that won't connect is apt-get.

I have two computers with the same problems. One now has a static IP address and the other connects through dhcp. Does apt-get use its own dns servers when connecting to the net please. How can I set dns servers please? What I would like to be able to do is to set the router address and also the dns addresses for my isp and tell apt-get to connect through that.

Many thanks.
-- 
Rich
[http://www.cregy.co.uk](http://www.cregy.co.uk)
Embracing what God does for you is the best thing you can do for him.
Romans 12 v 1

---

### Post by msandersen on 2006-09-07
Did you restart?
Short of following the Wiki page for *Disabling IPv6 on Dapper*, I don't know.
If you do find something, it may be worth adding a note to the Wiki.

---

### Post by cregy on 2006-09-07
> **msandersen said:**
> Did you restart?
Short of following the Wiki page for *Disabling IPv6 on Dapper*, I don't know.
If you do find something, it may be worth adding a note to the Wiki.
Hi

Yes I restarted - no joy with apt-get still. I will add a note to the wiki but where do I add it please?

Thanks.

Rich

---

### Post by msandersen on 2006-09-07
The Wiki isn't a support forum, so best wait til you have some answers. When you've got an account on the Wiki, there's an Edit link at the top.
Out of curiosity, is the same thing happening with the Ubuntu LiveCD on the same machines? Or even different machines on the same network?
Although you shouldn't crosspost, this might be a question for the [Networking forum]("http://www.ubuntuforums.org/forumdisplay.php?f=136").

---

