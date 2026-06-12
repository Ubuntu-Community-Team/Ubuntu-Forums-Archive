---
title: "How to find MAC address?"
date: 2006-04-12
forum: Absolute Beginner Talk
---

### Post by aktiwers on 2006-04-12
Hi guys!

Can anyone tell me how I can find my computers MAC address? 
I Need this to setup our Network, on my D-Link Router.

Thanks

---

### Post by taurus on 2006-04-12
```

/sbin/ifconfig

```

---

### Post by aktiwers on 2006-04-12
Thanks!

Can you help me find the MAC Address?

This is what it spits out!

```
user@ubuntu:~$ /sbin/ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0D:60:F0:9D:C7
          inet addr:192.168.0.177  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:60ff:fef0:9dc7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5699 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5198 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3848878 (3.6 MiB)  TX bytes:666158 (650.5 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10505 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10505 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:800551 (781.7 KiB)  TX bytes:800551 (781.7 KiB)

user@ubuntu:~$
```

---

### Post by Harleen on 2006-04-12
[QUOTE=aktiwers]Thanks!

Can you help me find the MAC Address?
[/Quote]

It's the part labeled as HWaddr (hardware address).

```
user@ubuntu:~$ /sbin/ifconfig
eth0      Link encap:Ethernet  HWaddr [COLOR="red"]00:0D:60:F0:9D:C7[/COLOR]
          inet addr:192.168.0.177  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:60ff:fef0:9dc7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5699 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5198 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3848878 (3.6 MiB)  TX bytes:666158 (650.5 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10505 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10505 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:800551 (781.7 KiB)  TX bytes:800551 (781.7 KiB)

user@ubuntu:~$
```[/QUOTE]

---

### Post by fng on 2006-04-12
Here it is:

```
HWaddr 00:0D:60:F0:9D:C7
```

---

### Post by aktiwers on 2006-04-12
Thanks a lot!

---

### Post by zerhacke on 2006-04-12
[QUOTE=aktiwers]
```
 HWaddr 00:0D:60:F0:9D:C7
```[/QUOTE]
Looks like you're running an IBM adapter.  Let us know how that works out for you, I have a couple IBM 10/100 cards that I've not used on Linux yet.

---

### Post by aktiwers on 2006-04-12
Yeah it is an IBM!

How did you know?

We are having some problems here though...

 We are trying to set up a network between this computer and another one. Both are running Ubuntu and when I connect them seperatly to the internet, without using the D-link router, they connect fine. But when I connect them both to the routor, and connect the routor to the internet, only the IBM gets internet access.

 I dont know how to check if the Network between the PCs, but im almost sure it doesnt work currect. :(

Anyone have a guide or some advice?

---

### Post by zerhacke on 2006-04-12
[QUOTE=aktiwers]Yeah it is an IBM!

How did you know?[/QUOTE]
[http://coffer.com/mac_find/](http://coffer.com/mac_find/)  I had a hunch that it may be an IBM nic from the MAC, since I've used them before for Windows and the MAC looked familiar.  I used [http://coffer.com/mac_find/](http://coffer.com/mac_find/) to check and be sure.

---

### Post by IYY on 2006-04-12
Try pinging the router from the computer that can't connect to the internet.

(ping -c1 192.168.0.1)

Does it reach the router?

---

### Post by AnRkey on 2007-10-18
> **zerhacke said:**
> [http://coffer.com/mac_find/](http://coffer.com/mac_find/)  I had a hunch that it may be an IBM nic from the MAC, since I've used them before for Windows and the MAC looked familiar.  I used [http://coffer.com/mac_find/](http://coffer.com/mac_find/) to check and be sure.

You are truly hardcore and your digital kung fu is very strong!

This technician is impressed =D>

---

