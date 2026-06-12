---
title: "Howto Connect to P2P network"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by perito on 2008-03-25
First I changed my IP to static IP using this method
```
sudo nano /etc/network/interfaces
auto eth1
iface eth1 inet static
address 192.168.0.3
netmask 255.255.255.0
sudo /etc/init.d/networking restart

```

but after that I cant connect to any network, I dont see the network in the Wireless Networks and if I typed its name in Connect to other wireless networks, it sees it but never connects (I guess its trying to acquire an ip address)

If I go to manual configuration, and I manually remove roaming and put a static IP address.. well it never happens, as soon as I close the manual configuration, it returns to roaming without a static IP address...
what should I do?
Im trying to connect to a wireless P2P network to play a game...

---

### Post by feanil on 2008-03-25
Do you need a static ip to connect to the p2p network?  Speaking as a bittorrent user, I have not heard anything like this before.  Is it something that network requires?  

==

If you're trying to get a static ip on a personal network that should be pretty easy to do but if you want a static web ip this might be more difficult depending on your ISP.

---

### Post by northern lights on 2008-03-25
> **perito said:**
> Im trying to connect to a wireless P2P network to play a game...

What sort of p2p is it you're talking about? Do you wanna play some sort of online/browser game or connect to some other comp gatewaying it's internet connection?

How did you come up with the idea of having to have a static IP?

---

