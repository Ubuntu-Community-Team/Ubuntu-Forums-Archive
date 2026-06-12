---
title: "ethernet port"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by tchoklat on 2006-10-22
Hi,

I am 'finally' getting broadband as I live in rural Australia. I have been told by the ISP  that I need an Ethernet 10/100 (RJ-45) port. What is this and how do I know whether I have one?

I use Dapper on an XP dula boot and currently use a Winmoden diap-up. My PC is about 6 yrs old with an AMD 2400+ processor

thanks for your help,

:-D
Tchoklat

---

### Post by ReaderRat on 2006-10-22
An RJ45 plug looks like a regular phone jack plug, only larger. You probably need to install an Ethernet card, which will have a RJ45 plug for your Ethernet cable. Are you getting DSL or cable-modem for broadband?

---

### Post by newlinux on 2006-10-22
look for something on your computer that looks like a phone input but slightly bigger. You probably have one. Also, what does 
```
ifconfig
``` return (type that in a terminal). It should list all of your configured network devices.

---

### Post by tchoklat on 2006-10-22
> **newlinux said:**
> look for something on your computer that looks like a phone input but slightly bigger. You probably have one. Also, what does 
```
ifconfig
``` return (type that in a terminal). It should list all of your configured network devices.

response to command>>


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:572 (572.0 b)  TX bytes:572 (572.0 b)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:203.220.104.202  P-t-P:203.194.23.97  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:6963 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7145 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:4681789 (4.4 MiB)  TX bytes:1548796 (1.4 MiB)

---

### Post by ReaderRat on 2006-10-22
Again, what kind of broadband service will you be using?
DSL...Cable-modem...???

---

### Post by tchoklat on 2006-10-22
Two way Satelite DSL

---

### Post by ReaderRat on 2006-10-22
If you do not have a RJ45 port on theback or your computer, then you can purchase a 10/100 Ethernet card (PCI slot) for about $10 USD and install it yourself.

---

### Post by tchoklat on 2006-10-22
thanks I will do this

---

### Post by ReaderRat on 2006-10-22
Your Ethernet port (RJ45 female) will be connected to your DSL cablemodem (or router) by an Ethernet cable (RJ45 male).
Hope this helped...

---

### Post by newlinux on 2006-10-23
looks like ifconfig only sees the modem. you probably don't have a NIC, but as already mentioned, you can get them pretty inexpensive

---

### Post by tchoklat on 2006-10-24
done - thanks, now only issue is the compatibilty with my dial-up modem, see my latest post

---

