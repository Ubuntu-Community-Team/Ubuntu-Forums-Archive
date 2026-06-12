---
title: "How Do I change from Dynamic IP to Static?"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by Old Jimma on 2006-12-05
Ubuntuers:

I want to change from dhcp to static. my /etc/network/interfaces for AMD64 Dapper looks like

[COLOR="Blue"][B]auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp[/B][/COLOR]

and my sudo ifconfig looks like

[COLOR="Navy"][B]eth0      Link encap:Ethernet  HWaddr 00:01:02:2C:2B:C9
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:133949 errors:0 dropped:0 overruns:0 frame:0
          TX packets:86668 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:118154600 (112.6 MiB)  TX bytes:7483058 (7.1 MiB)
          Interrupt:9 Base address:0xe000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:388298 errors:0 dropped:0 overruns:0 frame:0
          TX packets:388298 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:31517825 (30.0 MiB)  TX bytes:31517825 (30.0 MiB)[/B][/COLOR]



Thank you!
Phil Smith
Duluth, GA

---

### Post by Shatrat on 2006-12-05
I see from your IP you're behind a router, you could just go into the router config and fix the DHCP client addresses there by mac address.
If you want to do it on your desktop you can edit /etc/network/interfaces I believe.

---

### Post by scxtt on 2006-12-05
/etc/network/interfaces:

[indent]auto eth0
iface eth0 inet static
address 192.168.1.103
netmask 255.255.255.0
gateway 192.168.1.1[/indent]

then a **sudo ifdown eth0** / **sudo ifup eth0** should make it take effect ...

---

### Post by jalapena on 2006-12-06
> then a sudo ifdown eth0 / sudo ifup eth0 should make it take effect ...


Once the static information is entered, where do I enter the 'sudo' command?

---

### Post by bodhi.zazen on 2006-12-06
In a terminal....

---

### Post by jalapena on 2006-12-06
Great, thanks for your prompt response.

---

