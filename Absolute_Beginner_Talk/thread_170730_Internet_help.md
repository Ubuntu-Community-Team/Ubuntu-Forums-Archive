---
title: "Internet help"
date: 2006-05-05
forum: Absolute Beginner Talk
---

### Post by yellow beard on 2006-05-05
No i do not have a usb modem. Im going through a dlink router. The thing is, ive got the internet working before on ubuntu the first time i installed it. I recently tried fc5 and i got it working on that and now im back on ubuntu but i cant seem to remember how the hell i got it working the first time. ive set my ip up all correctly. i think. im pretty sure its because i need to configure linux to be part of my home workgroup which is called wapa but i dont know how. any ideas? ive got apt-get update working through terminal but i cant get on the web on firefox.

---

### Post by JShadow on 2006-05-05
A little more information would be helpful.

Are you using wired or wireless networking? What kind of network card?

Also, could you please post the results of the command "ifconfig -a" entered into the terminal?

---

### Post by browndog on 2006-05-05
Yes, if you could provide complete details about the network card installed in your computer and how you are trying to access the internet (wirelesss or wired), whether you use DHCP, etc... I'm sure we could help you.

---

### Post by yellow beard on 2006-05-05
OK. well its a wireless router but im connected to it via my intel pro/100 internal lan. im not using DHCP although it is enabled. its ip is 10.1.1.1 and mine is 10.1.1.14 with a subnet of 255.0.0.0. The connection is working since i can ping it fine. Im in windows at the mo so ill reboot into ubuntu and get the ifconfig -a details.

---

### Post by yellow beard on 2006-05-05
ath0      Link encap:Ethernet  HWaddr 00:13:46:5F:B1:37
          inet addr:10.1.1.14  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::213:46ff:fe5f:b137/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5 errors:225 dropped:0 overruns:0 frame:225
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:414 (414.0 b)  TX bytes:1059 (1.0 KiB)
          Interrupt:22 Memory:f8b80000-f8b90000

eth0      Link encap:Ethernet  HWaddr 00:0D:61:02:EA:F2
          inet addr:10.1.1.14  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::20d:61ff:fe02:eaf2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:60 (60.0 b)  TX bytes:378 (378.0 b)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:176 errors:0 dropped:0 overruns:0 frame:0
          TX packets:176 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:13779 (13.4 KiB)  TX bytes:13779 (13.4 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by yellow beard on 2006-05-05
anything?

---

### Post by catlett on 2006-05-05
in wrong post,sorry

---

### Post by yellow beard on 2006-05-05
err what?

---

### Post by yellow beard on 2006-05-05
help i really need to get my connection working!

---

### Post by pommattski on 2006-05-05
Have you tried pinging your router or any external addresses from within Ubuntu?
(System Tools -> Network Tools, "ping")

---

### Post by yellow beard on 2006-05-05
...[QUOTE=yellow beard]The connection is working since i can ping it fine.[/QUOTE]

---

### Post by Jason_25 on 2006-05-05
What does 
```

cat /etc/resolv.conf

```
show?

---

### Post by pommattski on 2006-05-05
OK.  (It sounded as though you were in Windows when pinging)
Anyway...  What about external address?

Try google.com or if that doesn't work try 72.14.207.99 or 64.233.187.99 (both google IPs)

If the IPs work but the domain name doesn't, I think you need to have a look at your dns settings.

Matt.

---

### Post by yellow beard on 2006-05-05
Ive already tried google but it just times out. Ill give the ip's a try and look at the resolv.conf.

---

### Post by yellow beard on 2006-05-05
OK so i tried the google ip address and it came up fine. A normal web address will not work though. Any tips as to how to fix my dns settings?

---

### Post by pommattski on 2006-05-05
There maybe an alternate setup which will work using your router as the dns server, but this is how I'm set up...

Your ISP will have given you (probably) 2 IP addresses of their DNS servers.

Go to:  System -> Administration -> Networking, select the dns tab and enter your dns IPs here.
(once entered, they are also viewable in /etc/resolv.conf as mentioned by jason25)

Matt.

---

### Post by yellow beard on 2006-05-05
Cheers that fixed it.

---

