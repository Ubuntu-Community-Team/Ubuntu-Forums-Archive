---
title: "No internet"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by Bill49 on 2007-04-18
Hello all. This is my first post and I'm a complete noobie - no linux experience at all.
I downloaded the 6.10 64 bit amd image yesterday, checksumed it, burnt my cd, and installed it without problem.  All was fine apart from no internet connection. I re-installed on the off chance, but still no connection! 
My connection is  shared wired adsl. The router is a linksys wrt54gs flashed with dd-wrt 3rd party firmware with an ip address of 192.168.193.1. All the other user (including 1 linux user) are having no problems.
Looking about the forums etc. I found the ifconfig command :-

eth0      Link encap:Ethernet  HWaddr 00:19:DB:32:31:7F  
          inet6 addr: fe80::219:dbff:fe32:317f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:2520 (2.4 KiB)
          Interrupt:233 Base address:0xf200 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

It does'nt mean anything to me, but remember I'm a know-nothing. Any sugestions on what to do next would be greatly appreciated. Thanks
Bill

---

### Post by mikewhatever on 2007-04-18
Have you tried System>Administration>Networking, and entering the ip in Properties for the Wired Connection?

---

### Post by Sulli on 2007-04-18
i remember when i first installed ubuntu 6.10 i had no internet via the default browser, and i was told to:

open firefox
in the address bar type about:config
then scroll down to network.dns.disable ipv6 and double click it to set it to true.

that worked for me but by the looks of your post you want to use ipv6?

if you dont want/need to use it give that ago

Sulli

---

### Post by Bill49 on 2007-04-18
Thanks for the quick replies you two.  I'm just back from work so I will look into things later on tonight. I will post what happens (good or bad).
Bill

---

### Post by Bill49 on 2007-04-19
I tried both your sugestions last night, but no luck, I'm afraid.  Again, thaks for your ideas.
Bill

---

### Post by dfox8895 on 2007-04-19
in a terminal type:

sudo dhclient 

This is like the ipconfig release/renew function in windows.  Based on the network statistics you posted it looks as if the router is not giving out IP's.  Do you have some kind of security set on the router?

---

### Post by dfox8895 on 2007-04-19
Your IFCONFIG results:

eth0 Link encap:Ethernet HWaddr 00:19B:32:31:7F
inet6 addr: fe80::219:dbff:fe32:317f/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:2520 (2.4 KiB)
Interrupt:233 Base address:0xf200 

My IFCONFIG results:

eth0      Link encap:Ethernet  HWaddr 00:0D:9D:4D:26:EE
          inet addr:192.168.2.40  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:9dff:fe4d:26ee/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:620688 errors:0 dropped:0 overruns:0 frame:0
          TX packets:789581 errors:0 dropped:0 overruns:0 carrier:0
          collisions:163456 txqueuelen:1000
          RX bytes:115930669 (110.5 MiB)  TX bytes:852074463 (812.6 MiB)
          Interrupt:209

Comparing the two, I can tell that you are connected by ehternet to the router directly (no hubs).  Your ethernet card is not set statically and your card is sending request  for an IP to the router, but has not recieved a response.  I would definately verify that the router is giving out IPs like it is suppose to.

---

### Post by nautilus on 2007-04-20
yes it has nothing to do with ipv6, firefox, or the like.

```
sudo gedit /etc/network/interfaces
```

it should look similar to this:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

```

and please, stop disabling ipv6.  it won't fix any issues whatsoever in feisty fawn.

---

### Post by Bill49 on 2007-04-20
At last - it's fixed !!
Thanks for all the help.  I tried your various suggests, but nothing worked.  It's a new computer so, in the end, I thought it must be a bad ethernet card.  I plugged one in I had hanging around and it worked right off.
It all goes to show that Ubuntu works when you have a working computer.
Thanks again
Bill

---

