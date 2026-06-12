---
title: "Internet Sharing on a home network"
date: 2005-07-23
forum: Absolute Beginner Talk
---

### Post by darkblue1893 on 2005-07-23
I posted this question before with no luck in getting it solved, so I will now give it another go.

I now have a dual boot system on my gateway pc and it is connected to the client pc by a crossover cable, internet connection is by a broadband modem from Blueyonder.

The client pc runs Windows 2000.

When i am running Windows Xp I have no problems sharing my internet connection, its is only when i use Ubuntu on the Gateway that the client Pc running Windows 2000 fails to connect to the Internet. So i do not believe i have a hardware problem.

The Internet Protocol setup on the Client Windows 2000 pc is -

Obtain an IP  address automatically
Obtain DNS server address automatically

The internet settings for the Gateway pc when booted from Ubuntu are:

Eth0 - DHCP connection

Eth1 -DHCP connection

The network settings panel says both cards are active.

So with these settings i have no problem connecting to the internet through the gateway pc, but the client pc fails to connect.

I have installed Firestarter and enabled Internet sharing.

I am completely new to Ubuntu and Linux so any help would be appreciated.

Thanks!

---

### Post by jasmuz on 2005-07-23
I did the same but with Guidedog & dnsmasq, both are supremely easy to manage. I would recomend you look into Guidedog.

In Ubuntu, you must tell the system to foward your ip towards the EthX you are using to connect the client.

You must have an private  ip assigned to the client (192.xxx.xxx.xxx) , and you must be able to ping it, and from the client ping the server machine.

---

