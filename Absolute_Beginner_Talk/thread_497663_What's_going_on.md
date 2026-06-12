---
title: "What's going on???"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by Amplidude on 2007-07-10
I shut down my server and on restart my network card (eth1) had crashed. Firestarter reported it as not being available and System>Administration>Networks reported that it was now eth2.  On restart it reverted to eth1. Now, a networked PC believes that it is connected to the network, but cannot find the internet because it thinks the gateway is 192.168.0.3, but the gateway is 192.168.1.1. 

This is all getting to be too much PT. I've been struggling to get the network up for DAYS!

---

### Post by ukripper on 2007-07-10
Check your interface file

```
sudo gedit /etc/network/interfaces
```

---

### Post by Amplidude on 2007-07-11
Thanks UKRipper, I did that and it was a mess. Question is: how did it get like that? I didn't change it. Does Firestarter change it? I've been messing around with that.
Thanks again

---

### Post by ukripper on 2007-07-11
Can you post output here?

---

### Post by scxtt on 2007-07-11
i've had nothing but annoyances w/ the new network manager and static IPs ... i've disabled it (avahi?) all together and don't let *networkmanager start at all ...

---

### Post by ukripper on 2007-07-11
> **scxtt said:**
> i've had nothing but annoyances w/ the new network manager and static IPs ... i've disabled it (avahi?) all together and don't let *networkmanager start at all ...

yeh true Network manager is really a pain in the a*** with statics.

---

### Post by Amplidude on 2007-07-11
> **ukripper said:**
> Can you post output here?

No, I changed the file and saved it.  Sorry.
Is the problem with firestarter or with Network manager?
I've been battling for days to get the network up and I'm not winning. Can you give me some guidance please?

BTW when I changed files a couple of days ago teh old file was retained with a tilde(~) as the last character. This isn't happening now, Does it only keep the file until a restart?

Thanks

---

### Post by Amplidude on 2007-07-11
> **scxtt said:**
> i've had nothing but annoyances w/ the new network manager and static IPs ... i've disabled it (avahi?) all together and don't let *networkmanager start at all ...

Umm... Whats avahi? Sorry, I'm a noob and I've seen it in Network manager. I thought it was a new  IP  protocol because the traditional xxx.xxx.xxx.xxx was limited and it had to be used

---

### Post by ukripper on 2007-07-11
It is a deamon for network manager

---

### Post by ukripper on 2007-07-11
> **Amplidude said:**
> No, I changed the file and saved it.  Sorry.
Is the problem with firestarter or with Network manager?
I've been battling for days to get the network up and I'm not winning. Can you give me some guidance please?

BTW when I changed files a couple of days ago teh old file was retained with a tilde(~) as the last character. This isn't happening now, Does it only keep the file until a restart?

Thanks

Don't know, sorry!

---

### Post by Amplidude on 2007-07-11
> **ukripper said:**
> Don't know, sorry!

No matter, it's hardly important. But can you give me some guidance with setting up my network please. I've read the manuals, trawled the google, and changed about everything I can think of and I still can't get it. I'd really appreciate it.

Thanks

---

### Post by ukripper on 2007-07-11
> **Amplidude said:**
> No matter, it's hardly important. But can you give me some guidance with setting up my network please. I've read the manuals, trawled the google, and changed about everything I can think of and I still can't get it. I'd really appreciate it.

Thanks

What kind of network you are setting up?

---

### Post by Amplidude on 2007-07-11
sorry about delay - I tried something else that crashed the internet connection.

I have a router connected to the internet.  The router is connected to a server with  two nic (eth0 and eth1 for the lan). eth1 is connected through a hub to PCs running XP.  I can connect to the internet through the server, but can't get the PCs to see the internet or the other computers.

Thanks for replying

My setup looks like this:

dhcpd.conf
# DHCP configuration by Firestarter
ddns-update-style interim;
ignore client-updates;

subnet 192.168.0.1 netmask 255.255.255.0 {
	option routers 192.168.1.1;
	option subnet-mask 255.255.255.0;
	option domain-name-servers Server1;
#	option ip-forwarding off;
	range dynamic-bootp 192.168.0.100 192.168.0.254;
	default-lease-time 21600;
	max-lease-time 43200;
}

etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1

auto eth1
iface eth1 inet static
address 192.168.0.1
netmask 255.255.255.0

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

Do you ned any more information?

---

