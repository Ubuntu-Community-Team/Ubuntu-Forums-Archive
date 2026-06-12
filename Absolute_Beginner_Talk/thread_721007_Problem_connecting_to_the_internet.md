---
title: "Problem connecting to the internet"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by jazmo14 on 2008-03-10
Ok I have recently installed Ubuntu 7.10, and am having problems connecting to the internet. I used [this link]("https://help.ubuntu.com/community/ADSLPPPoE") to try and help me, but I just can't get connecting. 

When I run the command "sudo pppoeconf" it says it found 1 ethernet device "eth0", I then hit yes and it scan's my ethernet device, after scanning it it tell's me "Sorry I scanned 1 interface, but the Access Concentrator of your provider did not respond. Please check your network and modem cables. Another reason for the scan failure may also be another running pppoe process which controls the modem"

My cables are all fine and I'm pretty sure there is no other pppoe process which controls the modem.

If you need any other information, just ask me and I will provide you with whatever you need.

---

### Post by forrestcupp on 2008-03-10
Are you using a router?  If so, you should be able to set it up to log on to your pppoe account, and Ubuntu will just detect the internet without having to really set it up.  If you do have a router, you can call their tech support and they will be able to tell you specifically how to do that with your device.

---

### Post by jazmo14 on 2008-03-10
> **forrestcupp said:**
> Are you using a router?  If so, you should be able to set it up to log on to your pppoe account, and Ubuntu will just detect the internet without having to really set it up.  If you do have a router, you can call their tech support and they will be able to tell you specifically how to do that with your device.

Yes I am using a router. I thought Ubuntu would just pick it up, as it is already set up. On my Ubuntu machine if I try and go on launchpad.net, it say's at the bottom left of the FireFox window "Connecting to lauchpad.net...", then after so long it just times out. So I'm thinking my machine is connected to the internet, but something is stopping it from accessing websites. I think maybe something in System>Administration>Network?

---

### Post by Shazaam on 2008-03-10
In terminal try this (ping google.com)...
```
ping 64.136.53.38
```
Ctrl+c to stop pinging.

---

### Post by jazmo14 on 2008-03-10
> **Shazaam said:**
> In terminal try this (ping google.com)...
```
ping 64.136.53.38
```
Ctrl+c to stop pinging.

PING 64.136.53.38 (64.136.53.38) 56(84) bytes of data.
64 bytes from 64.136.53.38: icmp_seq=1 ttl=240 time=213 ms
64 bytes from 64.136.53.38: icmp_seq=2 ttl=240 time=212 ms
64 bytes from 64.136.53.38: icmp_seq=3 ttl=240 time=214 ms
64 bytes from 64.136.53.38: icmp_seq=4 ttl=240 time=213 ms
64 bytes from 64.136.53.38: icmp_seq=5 ttl=240 time=213 ms
64 bytes from 64.136.53.38: icmp_seq=6 ttl=240 time=213 ms
64 bytes from 64.136.53.38: icmp_seq=7 ttl=240 time=214 ms
64 bytes from 64.136.53.38: icmp_seq=8 ttl=240 time=213 ms

--- 64.136.53.38 ping statistics ---
8 packets transmitted, 8 received, 0% packet loss, time 7000ms
rtt min/avg/max/mdev = 212.945/213.755/214.805/0.679 ms

Was the result of the ping.

---

### Post by jazmo14 on 2008-03-11
Anyone else able to help?

---

### Post by bumanie on 2008-03-11
Try disabling ipv6 in firefox
Type about:config in firefox address bar --> hit enter
Type ipv6 into the filter --> hit enter
Right click on the ipv6 line and choose toggle to set the value to true.
It worked for me on gutsy.

---

### Post by 504harry on 2008-03-11
Here goes....is your Ubuntu PC the same one that previously worked with the router? (  - so how are you writing to us?).....and if not, ( you have another PC), then does this still work - ie as well as the Ubuntu being present?

I'm not as advanced as a router - I just use a 20m cable - but the modem appears to "know" which PC is connected ( and I don't dual-boot, rather I change the HDD) - so I have to switch-OFF the modem - it then restarts and accepts Ubuntu things. . . . . all very confusing . . . but I'm grateful it works at all.

Your Router manufacturer may have a "Help-Forum" - that's probably better than their paid-for help-desk, who may  be less familiar with Linux, than you are (now). 

If you are borrowing a connection ( OR at a local Cafe, etc.) - then back home, try without the router - this will prove the fault's not anywhere else . . .  just a thought . . .  .hope it helps....slightly.

---

### Post by jazmo14 on 2008-03-11
> **bumanie said:**
> Try disabling ipv6 in firefox
Type about:config in firefox address bar --> hit enter
Type ipv6 into the filter --> hit enter
Right click on the ipv6 line and choose toggle to set the value to true.
It worked for me on gutsy.

Thank you so very very much! It worked, I'm now able to connect to the net on my Gutsy machine :D

---

### Post by jazmo14 on 2008-03-11
Thanks for your reply 504harry, but the post before yours helped me resolve my issue, and my internet is working fine now.

---

