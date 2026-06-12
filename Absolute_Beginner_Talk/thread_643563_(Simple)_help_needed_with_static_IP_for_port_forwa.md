---
title: "(Simple) help needed with static IP for port forwarding"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by laffinet on 2007-12-17
Hi,

I currently connect to my router via a wireless connection with WPA1 & DHCP, ESSID broadcast enabled. 

I set this up using this [guide]("http://ubuntuforums.org/showthread.php?t=202834&highlight=wpa+security") and everything works fine.

For torrents etc. I would now like to forward some ports, which means I have to switch from DHCP to static, otherwise I'll lose the forwarding everytime I re-connect to the router. 

My router is a Netcomm 5Bplus4W and I know how to set up the forwarding on it. However, what do I have to change in the "/etc/network/interfaces" to achieve this ? I know I have to change to something like this:

iface wlan0 inet static
address 192.168.168.40
gateway 192.168.168.230 
dns-nameservers 192.168.168.230
netmask 255.255.255.0
wpa-driver wext
etc.

but which addresses do I have to use ? Also, do I have to change something on the router as well or just the "interfaces" file ?

I'm not exactly a network buff, so a simple explanation would be greatly appreciated.

The LAN configuration on my router looks like this:
[IMG]http://farm3.static.flickr.com/2108/2119740220_ae0eb18b5e.jpg?v=0[/IMG]

Thanks in advance for the help from this great community ! 

laffinet

---

### Post by spiderbatdad on 2007-12-17
[http://ubuntuforums.org/showthread.php?t=629769&highlight=port+forwarding](http://ubuntuforums.org/showthread.php?t=629769&highlight=port+forwarding)

---

### Post by laffinet on 2007-12-17
> **spiderbatdad said:**
> [http://ubuntuforums.org/showthread.php?t=629769&highlight=port+forwarding](http://ubuntuforums.org/showthread.php?t=629769&highlight=port+forwarding)

Wow, I probably understood 30% of that thread and I can't really see how this helps me.

Maybe I should have said "I'm a network noob, especially with Ubuntu" instead of "I'm not exactly a network buff" :mrgreen:

I don't really need help with the port forwarding side of things (I think), it's the static vs dynamic (DHCP) stuff I'm confused about. :confused::confused:

Thanks.

---

### Post by spiderbatdad on 2007-12-17
take a look at this first poster. I know you're not setting up a sever but he shows how to simply set up static ip   [http://ubuntuforums.org/showthread.php?t=632841&highlight=static+sever](http://ubuntuforums.org/showthread.php?t=632841&highlight=static+sever)

---

### Post by laffinet on 2007-12-17
Ah. Seems to make more sense now. Some questions remain, though:

1. What does the gateway do and do I need that line ?
2. What address do I have to use ? Anything 192.168.1.xxx (except for 192.168.1.1, which is the router) ?
3. Looks like I don't have to change anything on my router, correct ?

---

### Post by LaRoza on 2007-12-17
> **laffinet said:**
> 
2. What address do I have to use ? Anything 192.168.1.xxx (except for 192.168.1.1, which is the router) ?

2. I would set it to an address that is already assigned by your network, so at least some of the time it will work.

---

### Post by spiderbatdad on 2007-12-17
looks like 192.168.168.40 judging by your OP
gateway is a node that allows access to the network from your computer, so...yes```
ifconfig
``` should show your ip address
inet address is what you want

---

### Post by laffinet on 2007-12-17
> **spiderbatdad said:**
> looks like 192.168.168.40 judging by your OP
gateway is a node that allows access to the network from your computer, so...yes```
ifconfig
``` should show your ip address
inet address is what you want

Sorry for all these questions, but as I said, I really need this step by step. So

- ifconfig
- find inet
- use that as "address" in my interfaces ?

What do I use for gateway ?

Thanks

---

### Post by spiderbatdad on 2007-12-18
```
netstat -rn
```

---

