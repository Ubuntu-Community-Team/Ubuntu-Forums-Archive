---
title: "FiOS Modem+Router bit torrent port"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by arkhamdc on 2007-12-27
I just got FiOS and i have the fastest connection ive ever. FiOS comes with a modem+router given to you by verizon. My connection is slow when using bit torrent clients for example on ktorrent i get the yellow triangle that says no incoming connections possibly firewalled. i tried to open port 6881 using iptables commands but nothing happened. I cant forward the ports with any programs because my computer only thinks it is a router. Is anyone else having this problem???

---

### Post by jas0 on 2007-12-27
First of all, I just want to say that I'm very jealous

I assume that you don't have your Ubuntu box connected directly to your modem since you do list the router. The router acts as a NAT on you network, with your Ubuntu box being behind it. So you want to clear the path for your BitTorrent packets starting from the NAT. Login to your router and forward a random 5-digit port to the IP of your Ubuntu box. For example open port 39843 and forward it to 192.168.1.100 (i.e. your Ubuntu box). Then in Ktorrent select your port to be the same as the one you opened on the NAT. The reason for picking a random port is the fact that sometimes port 6881 is throttled by default by ISPs. Some of them don't want to bother with expensive traffic shaping equipment, so they just setup cheap QoS.

Once you have all this done, you should be fine. If you have enabled some custom iptables rules, just open the same port there as well.

---

### Post by arkhamdc on 2007-12-30
no verizon gave me a modem and router all in one thing so it like a combo thing. Also i do not even know how to login to my router?

---

### Post by Zack McCool on 2007-12-30
You'll likely have to call Verizon, then, and ask them how to configure the router.  

Perhaps if you gave the actual model of the router, someone here might be able to help...

---

### Post by node42 on 2008-01-04
> **arkhamdc said:**
> I just got FiOS and i have the fastest connection ive ever. FiOS comes with a modem+router given to you by verizon. My connection is slow when using bit torrent clients for example on ktorrent i get the yellow triangle that says no incoming connections possibly firewalled. i tried to open port 6881 using iptables commands but nothing happened. I cant forward the ports with any programs because my computer only thinks it is a router. Is anyone else having this problem???

I'm getting my FiOS on next Thursday (15mbps up and down)! Did you need to have a Windows computer available for the install? With my cable modem the installer wanted to walk unless I had a Windows system for him to set up - but that was a couple of years ago. :mad:

---

