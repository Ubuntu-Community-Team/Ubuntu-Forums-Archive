---
title: "new Badger (5.10) install can't connect to Internet?"
date: 2006-03-16
forum: Absolute Beginner Talk
---

### Post by beej101 on 2006-03-16
as above... do i need to confgure anything? i did ifconfig and the network card seems to be set up just fine... and i have my IP address correct. 
i think it's supposed to be straightforward that i should be able to connect to internet after installation right?
TIA.

---

### Post by Zelut on 2006-03-16
you should be able to connect, yes.  Can you post the output of ifconfig?  Are you using DHCP or static?  If DHCP try the following:

> sudo dhclient

That will try to retrieve a DHCP assigned address.  Normally this should happen upon boot, but we're going to try a few things & see why it hasn't.

---

### Post by beej101 on 2006-03-17
maybe what you have in mind is that my network i/f isn't getting an assigned IP address? if so, then no i don't think this is the problem since ifconfig does show me an assigned address and i think it's dhcp although i always get assigned the same private ip (i'm not visible outside).  
having said that, i will post the output of my ifconfig shortly.  sorry for this noob question but would posting the output of my ifconfig in this forum make me vulnerable to hacks? are there info there that would make this so?
thanks!

---

### Post by beej101 on 2006-03-17
the following is the output of my ifconfig
```
eth1      Link encap:Ethernet  HWaddr 00:12:3F:0A:C8:CD
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:3fff:fe0a:c8cd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:411 errors:0 dropped:0 overruns:0 frame:0
          TX packets:370 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:454662 (444.0 KiB)  TX bytes:70384 (68.7 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:511 errors:0 dropped:0 overruns:0 frame:0
          TX packets:511 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:44695 (43.6 KiB)  TX bytes:44695 (43.6 KiB)
```
and the following is the output of sudo dhclient
```
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/sit0/
Sending on   LPF/sit0/
Listening on LPF/eth0/00:12:f0:80:92:73
Sending on   LPF/eth0/00:12:f0:80:92:73
Listening on LPF/lo/
Sending on   LPF/lo/
Listening on LPF/eth1/00:12:3f:0a:c8:cd
Sending on   LPF/eth1/00:12:3f:0a:c8:cd
Sending on   Socket/fallback
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.2 -- renewal in 1463 seconds.

```
interestingly, i can connect occasionally to ubuntuforums.org but not to any other sites(they time out, take too long which shouldn't be cuz i'm on broadband)... also, i could ping for external sites... 

i know i've been asking a lot in this forum but i've really exhausted solutions i have in mind and it makes me cringe to think that i would have to reinstall the whole OS just to get the internet working... 

again TIA

---

### Post by beej101 on 2006-03-17
hi if anyone out there can point me in the right direction how to solve this it would really be greatly appreciated.  i'm kind of stuck and confused why i can't connect to internet wiht my ubuntu install when i think my network i/f is configured properly with it's ip address and i can even ping internet hosts?
:confused:

---

### Post by beej101 on 2006-03-17
:-# bump!

---

### Post by _simon_ on 2006-03-17
If you can occasionally view this forum then you do have a connection, it sounds like a DNS issue.

Find the DNS for your ISP and enter them into the DNS bit. Remove any that are already listed.

System -> Administration -> Networking -> DNS tab

---

### Post by steve.horsley on 2006-03-17
I _presume_ that your local router is 192.168.1.1? 
    If so, can you ping it reliably?
What is the output of the command **netstat -r**?

Can you ping [www.ubuntuforums.net](www.ubuntuforums.net) with the command **ping [www.ubuntuforums.net](www.ubuntuforums.net)**?
If not, can you with the command **ping 64.20.39.27**?
If either of the above doesn't work, post the output.

If you're using Firefox, try disabling IPv6: Type the address about:config and then filter on **v6**. If it;s not disabled, double-click the line and then try again.

---

### Post by beej101 on 2006-03-17
simon,

the DNS set for me is 192.168.1.1 which is my router gateway. (is it correct to say router gateway or just either router or gateway?)
if it's indeed a DNS problem, how do i determine the correct DNS server? shouldn't my router gateway (192.168.1.1) have a DNS server running since it's a gateway to internet?

steve,

i can ping the internet ip addresses but when i ping say, [http://www.cnn.com](http://www.cnn.com) or [http://www.ubuntuforums.org](http://www.ubuntuforums.org) i get unknown host.  if i ping ubuntuforums.org i get a single reply.
um what do you mean by about:config?

thanks!

> **steve.horsley]I _presume_ that your local router is 192.168.1.1? 
    If so, can you ping it reliably?
What is the output of the command **netstat -r**?

Can you ping [www.ubuntuforums.net](www.ubuntuforums.net) with the command **ping [www.ubuntuforums.net](www.ubuntuforums.net)**?
If not, can you with the command **ping 64.20.39.27**?
If either of the above doesn't work, post the output.

If you're using Firefox, try disabling IPv6: Type the address about:config and then filter on **v6**. If it said:**
> 


[QUOTE]If you can occasionally view this forum then you do have a connection, it sounds like a DNS issue.

Find the DNS for your ISP and enter them into the DNS bit. Remove any that are already listed.

System -> Administration -> Networking -> DNS tab

---

### Post by beej101 on 2006-03-17
lastly, if it's a DNS problem, thing is i have a dual boot and one is XP.  when i boot with XP i don't have any problem connecting to the internet.  and since i haven't changed anything on my XP, it must be using the 192.168.1.1 as DNS (which is what is set as DNS for my Ubuntu install)? am i right or my reasoning is wrong?
this is getting a bit frustrating as i have a deadline :(

---

### Post by comppsyco on 2006-03-17
The NIC was configured fine, but the connection kept timing out. Funnily enough, one day I booted up my computer and the connection was there. You can find your DNS servers by typing 192.168.1.1 into a browser on a computer that does have a good connection, and looking at the config stuff. On my Netgear router the correct page is called "router status," so it's probably something somewhat similar to that.

---

### Post by beej101 on 2006-03-17
this may seem funny but it's starting to get annoying, really... so, how do i do my browsing?... i ping the machine server i.e.```
ping google.com
```... once it spits out the ip address, i type ```
http://64.233.167.99
```... but even then i can usually only get to ubuntuforums.org... with most other sites, it seems to try to connect but times out afterwards... :-k

---

### Post by jbmalone on 2006-03-18
You need to reset your modem.  That should reset the DNS servers to what they should be from the ISP.  I had the same problem and this is what fixed it.  The router just gets in the way, and tries to do more than it needs to.

---

### Post by beej101 on 2006-03-18
is this one of those forums where you can rank users who helped out? if so, how to do it?  i just wanna thank the guys who helped... my internet is now working... thanks!

---

### Post by beej101 on 2006-03-18
so changing the DNS entry to my ISP's assigned DNS servers in the network monitor  worked... but i don't understand why after a few minutes it expires and the old entry (IP address of my router) is placed there again? :-k

---

### Post by guysmiley on 2006-03-19
I'm not too sure about the expired IP, but I know Firefox gave me a real run for my money.  

I noticed someone said earlier to try disengaging ipv6 on Firefox...  Did this work for you?  It did for me and all's well now.

gs

---

### Post by beej101 on 2006-03-19
how do you disengaged ipv6? thanks! can you step by step this one for a noob? thanks!

---

### Post by mikes34 on 2006-03-19
type about:config in address bar in firefox, press go, filter ipv6 and double click on it... that's all

---

