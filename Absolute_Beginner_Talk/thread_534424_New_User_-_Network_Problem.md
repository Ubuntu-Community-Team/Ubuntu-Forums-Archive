---
title: "New User - Network Problem"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by dennisl on 2007-08-25
I have two machines with Windows XP and my main PC has only XP installed and the network connection is by way of D-Link DSL-G604T Wireless modem. On my second machine I have installed Ubunto V7.04 and XP as dual boot, and am using a Netcomm NP542  Wireless PCI Card.

My problem is I have been unable to connect to the internet with Ubuntu, nothing I do seems to work.

Should I be able to get the wireless internet connection to work on the second machine that has the dual boot (XP & Ubuntu) if I don't have Ubuntu installed on the first machine ?

Thanks in advance for any help.

Regards,

dennisl

---

### Post by cmnorton on 2007-08-25
Is the wirleless card on the Ubuntu system compatible with the wireless router? It probably is, but the question is a place to start. Usually, a wireless router can be contacted through a browser. Can you do that with the first system? You might want to check your settings to see that you can have multiple clients, whether you are using encryption, and so on.

Does the working system get its internet address via DHCP? Is this the same for the Ubuntu system?

Is there encryption being used between your working system and the wireless router, and does the same hold true for the Ubuntu system?

On the Ubuntu system, go to a terminal, and enter ifconfig. Is the interface up?

eth1      Link encap:Ethernet  HWaddr 00:02:2D:56:0B:F6
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::202:2dff:fe56:bf6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

---

### Post by dennisl on 2007-08-26
Than ks for your reply, The network card that I am using Netcomm NP542 is supported by Ubuntu and works fine with Windows XP Home when I boot into this machine, but I cannot get it to work when I dual boot into Ubuntu 7.04.

I am not actually able to see my NP542 on Ubuntu (and I am not real sure how to find it) but when I go into temminal and type in NP542 I do get an IP address 169.254.255.255 and a mask of 255.255.0.0 (my ISP address is 203.21.20.20 and secondry is 203.10.1.9.)

I don't know where to look or in fact what to look for to get my network up and running.

Regards,

dennisl

---

### Post by tim15856 on 2007-08-26
169.254.255.255 shows the network card doesn't see a DHCP server so it's not getting a legitimate IP address. Make sure the ifconfig command shows you have a working eth interface. Try temporarily turning off WPA, WEP, or any other type of security on the router and then see if you can get an IP address.

---

