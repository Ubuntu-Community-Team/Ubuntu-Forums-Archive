---
title: "No Ping Reply From Locahost"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by marx2k on 2007-04-25
I am able to ping outside servers, my router, other computers on my lan but am unable to ping lo, localhost, 127.0.0.1 or my internal lan IP of 192.168.11.4

Just upgraded to Fiesty from Edgy last night

Here's the interesting part, before getting into specifics...

traceroute works:
```

marx2k@Commodore-64:/var/log$ traceroute localhost
traceroute to localhost (127.0.0.1), 30 hops max, 40 byte packets
 1  localhost (127.0.0.1)  0.096 ms  0.101 ms  0.035 ms

```

I can also ssh into locahost..

but PING produces no reply!

My IPTABLES are clean:
```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  

```

my IFconfig: 
```

eth1      Link encap:Ethernet  HWaddr 00:40:CA:70:19:A6  
          inet addr:192.168.11.4  Bcast:192.168.11.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:418582 errors:0 dropped:0 overruns:33 frame:0
          TX packets:395335 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:208230174 (198.5 MiB)  TX bytes:54261727 (51.7 MiB)
          Interrupt:19 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11001 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11001 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1979741 (1.8 MiB)  TX bytes:1979741 (1.8 MiB)

```

/etc/hosts is just one line:
127.0.0.1 localhost


/etc/network/interfaces:
```

auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

```

routing:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.11.0    0.0.0.0         255.255.255.0   U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.11.1    0.0.0.0         UG    0      0        0 eth1

```

---

### Post by johnnymac on 2007-04-25
what does your /etc/hosts look like?

you need to have this entry there

```

127.0.0.1       localhost

```

---

### Post by marx2k on 2007-04-25
I included that with my post. It may have been missed since I didnt put it inside the code blocks.. 

but yeah, 127.0.0.1 localhost is in there

---

### Post by marx2k on 2007-04-25
Here's another weird thing..

I have OpenDNS as my nameserver, so here's some interesing output

```

marx2k@Commodore-64:/etc$ ping lo
PING lo.208.67.220.220 (208.69.32.130) 56(84) bytes of data.
64 bytes from nxdomain.guide.opendns.com (208.69.32.130): icmp_seq=1 ttl=51 time=46.5 ms
64 bytes from nxdomain.guide.opendns.com (208.69.32.130): icmp_seq=2 ttl=51 time=47.6 ms
64 bytes from nxdomain.guide.opendns.com (208.69.32.130): icmp_seq=3 ttl=51 time=46.6 ms
64 bytes from nxdomain.guide.opendns.com (208.69.32.130): icmp_seq=4 ttl=51 time=46.2 ms
64 bytes from nxdomain.guide.opendns.com (208.69.32.130): icmp_seq=5 ttl=51 time=46.1 ms
64 bytes from nxdomain.guide.opendns.com (208.69.32.130): icmp_seq=6 ttl=51 time=46.1 ms
64 bytes from nxdomain.guide.opendns.com (208.69.32.130): icmp_seq=7 ttl=51 time=45.7 ms

```

When I use charter (my cable ISP provider) as my nameserver, pinging lo pings the charter nameservers

but ping loopback and 127.0.0.1 are still no good

---

### Post by Patrick K on 2007-04-25
Try putting this line under the localhost line in the hosts file
> 127.0.1.1 hostnameYou can get your host name in the networking utility in administration.

---

### Post by marx2k on 2007-04-25
Tried that. Didn't fix the issue. I actually had that previously and commented it out to remove the chance that that may have had something to do with it.

I'm beginning to think that it may be the 'ping' program and Fiesty somehow.  I'm not sure how that could be though.  I can traceroute myself which uses ICMP pinging doesnt it? It gives me results. I can definitely SSH into 127.0.0.1 and go to my web admin cups server page so we know that 127.0.0.1 is open for business. Does fiesty stealth pings and I just dont know it or something??

---

