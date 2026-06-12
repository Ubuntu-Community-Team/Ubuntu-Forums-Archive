---
title: "[SOLVED] Ethernet / Internet issue in Gutsy"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by BOZG on 2007-10-14
There seems to be some problem with my internet connection when using Gutsy.  Download and loading speeds are as normal but it takes an abnormal period of time for things to begin loading.  If I attempt to open a page in Firefox, it can be looking up a page for 20-30 seconds before it starts to load the page and this is on a 3mb connection.  I've tried Windows and there are no issues with the connection. 

It's also affecting my ability to download through Synaptics because it takes so long to load, Synaptics assumes that the connection has just failed and so doesn't give me updated lists or is unable to download updates.

Does anyone have any ideas about how to fix this?

---

### Post by steve.horsley on 2007-10-14
No, but it sounds like it might be a DNS issue. If you enter the command 
**ping ubuntuforums.org**
how long does it take before telling you the IP address it is pinging? It should be very quick.

Also, if you try and ping your own host by name?

The only actual check I can think of is to see that your host name is mentioned in /etc/hosts, and that localhost is also mentioned. For instance, my PCs hostname (in /etc/hostname) is StevesPC and my /etc/hosts file contsins these entries:
> 127.0.0.1       localhost
127.0.1.1       StevesPC


Oh, another thing. If DNS lookups for othert addresses is taking a long time, you could make sure that all the serversnamed in file /etc/resolv.conf are actually reachable. It could be that the first one mentioned isn't reachable and you are having to wait for DNS to time out and try the second server.

---

### Post by BOZG on 2007-10-14
Pings are at normal speed, in the low ms.

All servers are reachable.

---

### Post by steve.horsley on 2007-10-14
Nah - I was wondering it when you said ping ubuntuforums.org if it might take 20-30 seconds before coming back and saying  91.189.94.186 which would indicate that it's the DNS lookup that's taking the time.

My next step would be to install wireshark and take a trace, see what packets are going up and down the line during that time.

---

### Post by ghost_ryder35 on 2007-10-14
> **BOZG said:**
> There seems to be some problem with my internet connection when using Gutsy.  Download and loading speeds are as normal but it takes an abnormal period of time for things to begin loading.  If I attempt to open a page in Firefox, it can be looking up a page for 20-30 seconds before it starts to load the page and this is on a 3mb connection.  I've tried Windows and there are no issues with the connection. 

It's also affecting my ability to download through Synaptics because it takes so long to load, Synaptics assumes that the connection has just failed and so doesn't give me updated lists or is unable to download updates.

Does anyone have any ideas about how to fix this?
I had this problem when my router was putting its address for Primary DNS server and the secondary DNS server as the real dns server.  I fixed the problem by using a static IP address and setting the DNS servers manually that way my router is bypassed as a DNS server.

---

### Post by BOZG on 2007-10-15
> **ghost_ryder35 said:**
> I had this problem when my router was putting its address for Primary DNS server and the secondary DNS server as the real dns server.  I fixed the problem by using a static IP address and setting the DNS servers manually that way my router is bypassed as a DNS server.

I've tried setting a Static IP address but I always have problems with it. The router that I got from my ISP would never work for me so I used a friend's router from a different ISP which has locked some of the settings and stops me from setting up a static address.

---

### Post by realvz on 2007-10-15
BOZG,
I think there's a problem with the DNS servers...i have had this problem too recently...
I am using open DNS...why dont you give this a shot...and let us know if it helps at all..

here is the link
[https://www.opendns.com/start?device=ubuntu](https://www.opendns.com/start?device=ubuntu)

---

### Post by Warren Watts on 2007-10-15
I recently began experiencing slow DNS lookups in Feisty, and discovered the problem was the order of the DNS servers that get placed into the /etc/resolv.conf file by dhcpcd (the DHCP client daemon).

I wrote a handy Perl script to analyze the relative speeds of each DNS server and display them for me, so I could customize the order they appear in /etc/resolv.conf.  

Here is a link to the post:

[http://ubuntuforums.org/showpost.php?p=3397192&postcount=16]("http://ubuntuforums.org/showpost.php?p=3397192&postcount=16")

---

### Post by BOZG on 2007-10-15
I'm not home at the moment but I'll check your suggestions out later.

Though I'm wondering why it would be an issue on Linux but not on Windows.  From what I can remember, when I checked resolv.conf there was only a single DNS and when I was trying to set up a Static IP recently, I think I only had a single DNS too.

---

### Post by BOZG on 2007-10-15
> **realvz said:**
> BOZG,
I think there's a problem with the DNS servers...i have had this problem too recently...
I am using open DNS...why dont you give this a shot...and let us know if it helps at all..

here is the link
[https://www.opendns.com/start?device=ubuntu](https://www.opendns.com/start?device=ubuntu)



Tried to configure OpenDNS but I got this response:

```
stephen@stephen-desktop:~$ sudo ifdown eth0 && sudo ifup eth0
ifdown: interface eth0 not configured
Ignoring unknown interface eth0=eth0.
stephen@stephen-desktop:~$ 

```

I assume that eth0 not being configure could be the issue and if it is, how do I configure it. Thanks.

---

### Post by BOZG on 2007-10-15
In case it's relevant, here's the response from pinging my DNS address:

```
stephen@stephen-desktop:~$ ping 192.168.1.254
PING 192.168.1.254 (192.168.1.254) 56(84) bytes of data.
64 bytes from 192.168.1.254: icmp_seq=1 ttl=255 time=0.346 ms
64 bytes from 192.168.1.254: icmp_seq=2 ttl=255 time=0.343 ms
64 bytes from 192.168.1.254: icmp_seq=3 ttl=255 time=0.334 ms
64 bytes from 192.168.1.254: icmp_seq=4 ttl=255 time=0.338 ms

```

---

### Post by BOZG on 2007-10-15
Well this is quite odd.

If I go to [http://www.ireland.com](http://www.ireland.com), it opens immediately but no other site does?

---

### Post by BOZG on 2007-10-15
I've also noticed that when a site finally loads, the load times within that site, if I'm moving from page to page is quicker than opening up a new site.

---

### Post by BOZG on 2007-10-16
Any more suggestions?

---

### Post by BOZG on 2007-10-16
> **realvz said:**
> BOZG,
I think there's a problem with the DNS servers...i have had this problem too recently...
I am using open DNS...why dont you give this a shot...and let us know if it helps at all..

here is the link
[https://www.opendns.com/start?device=ubuntu](https://www.opendns.com/start?device=ubuntu)


I tried Open DNS again and it worked this time.  Thanks a lot realvz.

---

### Post by moe_syzlak on 2007-11-29
this prolem has been solved here ---> [http://ubuntuforums.org/showthread.php?t=616744](http://ubuntuforums.org/showthread.php?t=616744)

please search the forums for a solution BEFORE asking for help. many problems advanced and some of the noob problems (such as "how do i get root on my computer," or "how to install xxxxx package" that is in the repository) have been fixed. and you can get the answers to your problem by searching

---

