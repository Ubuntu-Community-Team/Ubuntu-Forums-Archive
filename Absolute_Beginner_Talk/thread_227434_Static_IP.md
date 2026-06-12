---
title: "Static IP"
date: 2006-08-01
forum: Absolute Beginner Talk
---

### Post by jbomber on 2006-08-01
Hello! I wasn't able to get internet w/ 5.10, but I reformated and got 6.06 and the internet works fine. However, I get dropped here and there, and I have to restart to get my internet back. So i think I need a static IP.

i wanted to ask if anyone knows how to set up a static ip on ubuntu 6.06. When I go to the terminal and type in "ifconfig" i get:
```

eth0      Link encap:Ethernet  HWaddr 00:14:22:92:5E:D2
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:22ff:fe92:5ed2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3353 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7375 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2604999 (2.4 MiB)  TX bytes:722869 (705.9 KiB)
          Interrupt:209
```

Before the forums went down I was reading this was the info i needed to set up the static ip. However when I go to put in the static ip info i have to fill in:

ip address:
subnet mask:
gateway address:

I don't know what to fill in since I did not understand the info I got beforehand. I am on optimum online and have a linksys Wireless-G Broadband Router WRT54G.

---

### Post by sas on 2006-08-01
I.P. address - you want to avoid having an IP address that your router might give someone else - the range your router will use is probably configurable on your router, anything between 192.168.1.2 and 192.168.1.100 is probably a safe bet though.

Your subnet mask is 255.255.255.0 (as seen on the "mask" bit on the ifconfig output)

your default gateway is presumably 192.168.1.1

---

### Post by halfvolle melk on 2006-08-01
You can edit /etc/network/intefaces for this.
```
sudo gedit /etc/network/interfaces
```
and make it look something like this
```
auto  lo
iface lo inet loopback

auto  eth0
iface eth0 inet static
	address 192.168.1.101
	netmask 255.255.255.0
	gateway 192.168.1.1
```
You'll need to adjust eth0 to your needs.

---

### Post by jbomber on 2006-08-01
address 192.168.1.101
	netmask 255.255.255.0
	gateway 192.168.1.1

that did the trick! thanks

---

### Post by sas on 2006-08-01
Uhm, that's fine till your computer is off, and someone else connects to the router and the router automatically gives it the 192.168.1.101 address, then you put your computer on and suddenly you have two machines with the same ip address.

Change that 192.168.1.101 to something between 192.168.1.2 and 192.168.1.100 :)

---

