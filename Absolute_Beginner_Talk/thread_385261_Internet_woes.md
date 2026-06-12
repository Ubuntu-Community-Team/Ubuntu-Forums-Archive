---
title: "Internet woes"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by peterpan_champ on 2007-03-15
I finally get edgy 6.10 to install and now I can't get the internet to work.  I have two computers connected through an ethernet switch.  I dual boot Ubuntu/XP on my laptop... internet works fine when booting with xp, nothing when booting with Ubuntu.  Knowing absolutely nothing about the os doesn't help but I found networking tools and it seems to notice my ethernet adapter and states that it is active but no connection can be established.  Any suggestions would be quite helpful

---

### Post by lamalex on 2007-03-15
try manually renewing your dhcp lease?

```

sudo ifdown eth0
sudo ifup eth0

```

eth0 is usually your wired port, try that first, wireless is a different issue usually

---

### Post by schms on 2007-03-15
1. Does DNS work ?

Try: 

nslookup   [www.cnn.com](www.cnn.com)

r794@niesen:/appl$ nslookup [www.cnn.com](www.cnn.com)
Server:         192.168.1.1
Address:        192.168.1.1#53

Non-authoritative answer:
Name:   [www.cnn.com](www.cnn.com)
Address: 64.236.16.52
Name:   [www.cnn.com](www.cnn.com)
Address: 64.236.24.12
Name:   [www.cnn.com](www.cnn.com)
Address: 64.236.29.120
Name:   [www.cnn.com](www.cnn.com)
Address: 64.236.91.21
Name:   [www.cnn.com](www.cnn.com)
Address: 64.236.91.22
Name:   [www.cnn.com](www.cnn.com)
Address: 64.236.91.23
Name:   [www.cnn.com](www.cnn.com)
Address: 64.236.91.24
Name:   [www.cnn.com](www.cnn.com)
Address: 64.236.16.20

r794@niesen:/appl$



2. Do you have a default gateway and can you ping it ?

Below, the default gateway is 192.168.1.1 


r794@niesen:/appl$ netstat -nr
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0
r794@niesen:/

r794@niesen:/appl$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=255 time=0.505 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=255 time=0.485 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=255 time=0.501 ms


3.
Is there anything written in /var/log/messages ?

cat  /var/log/messages

---

### Post by peterpan_champ on 2007-03-15
I get: No DHCPOFFERS received. 
         No working leases in persistent database - sleeping.

---

### Post by peterpan_champ on 2007-03-15
I tried both of your suggestions now I am showing no IP address, no nothing. I am quite confused, but thanks for the replies

---

### Post by peterpan_champ on 2007-03-16
When I ping the dns I get nothing.  Any thoughts?

---

### Post by Kay The Bantu on 2007-03-16
you can try from the gui, System>Adminstration>Network Tools that should give you nearly all the options you need. hope it helps

---

### Post by Mr. C. on 2007-03-16
Open a Terminal window and type:

```
ifconfig -a
```

Show the output.  Show your LAN IP address, netmask, gateway and broadcast address configured on your router.

MrC

---

### Post by peterpan_champ on 2007-03-16
ipconf -a shows my ethernet adapter, wireless card, loopback, and link.  But I do not understand most of the things showing in the terminal.

---

### Post by Mr. C. on 2007-03-16
> **peterpan_champ said:**
> ipconf -a shows my ethernet adapter, wireless card, loopback, and link.  But I do not understand most of the things showing in the terminal.

That's Ok, I do.  That's why as I asked you to show the output.  Copy/paste here.

MrC

---

### Post by peterpan_champ on 2007-03-16
sit0             Link encap:IPv6-in-IPv4
                  NOARP   MTU:1480   Metric:1
                  RX packets:0  errors:0  dropped:0  overruns:0  frame:0 
                  TX packets:0  errors:0  dropped:0  overruns:0  carrier:0
                  collisions:0 txqueuelen:0
                  RX bytes:0  (0.0 b)    TX bytes:0  (0.0 b)

---

### Post by peterpan_champ on 2007-03-16
somehow made a new post.  was supposed to be a reply.  

sorry

---

### Post by peterpan_champ on 2007-03-16
nevermind I did the right thing.  See, this has me all flustered.

---

### Post by Mr. C. on 2007-03-16
Ok, you do have an IP address.

With Ubuntu, show output from:

```
ping 17.254.3.183
cat /etc/resolv.conf
```

You said you have a switch with two computers hooked up.  A couple of questions required for clarfication.

  1) is it "switch", or "router"
  2) If it is a switch, does your ISP allow multiple computers to be connected via switch?
  3) If it is a switch, show the IP addresses, netmask, gateway, broadcast, and DNS servers of the other computer that is connected at the same time as your Ubuntu

MrC

---

### Post by peterpan_champ on 2007-03-16
It is a switch.
Yes, my isp allows multiple computers to be connected.
I showed ip and what not on other computer.

When I ping that address it just says Destination Host Unreachable.
The other thing gives me

---

### Post by Mr. C. on 2007-03-16
I don't think you understood the implications of my question #2; it wasn't about what your ISP *allows*, it was about what they provide you with.  So let me re-phrase.

Does your ISP provide you with *multiple* dynamic or static IP addresses.

If they do not, you **cannot **connect two computers to a switch which then connects to a single-IP'd connection.  In other words, you cannot share a single IP with a switch.  You need a NAT'ing router to do this.

Since you have an IP address, but cannot ping anything, it is reasonable to assume there is an IP address conflict.

How is your Ubuntu IP address configured- manually by you, or dynamically?

MrC

---

### Post by peterpan_champ on 2007-03-16
My IP is dynamically setup.  I pretty sure my isp allows for multiple dynamic, because I dual boot xp/Ubuntu on the computer and windows has no trouble connecting to the internet. Windows is also setup to connect automatically.  That is what lead me to believe the problem is with Ubuntu. I just don't see how it could be anything else. But i guess you could be right...  maybe there is an ip conflict.  The IP address differs on both computers as well as the subnet and what not.  The only thing the same is the dns.

---

### Post by Mr. C. on 2007-03-16
> **peterpan_champ said:**
> ...differs ... as well as the subnet...

This might be the problem.  The subnets would typically be the same, but I don't know your ISP, nor what they provide.

Without seeing the IP info, I can't be more definitive.

Try not to get caught up in the "it works in XP, therefore..." mentality.  All that tells you is that it *can* work, not why it doesn't.  There are many reasons why one configuration works, but another doesn't.  Stay focused on the current configuration and settings, and work with that.

I'm not big into playing dice with computers.  Either you *know* your ISP supports multiple IP addresses, or you *don't know*.  Guess or giving percentages serves no purpose.

Let's see the data...
MrC

---

### Post by peterpan_champ on 2007-03-17
I finally found a fix for the problem.  I reinstalled both xp and Ubuntu and magically now I can connect to the internet.  Mr.C thank you for all your very helpful input, and putting up with an Ubuntu noob.  I'm glad I didn't just get frustrated and scrap linux because I really dislike windows.  It good to see that there are people willing to help.

---

### Post by Mr. C. on 2007-03-17
Great news!  Thanks for the update and kind words.

MrC

---

