---
title: "how to connect to internet???"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by kyusstool on 2007-03-17
hi.completely new to linux.had probs with my speedtouch modem so have now got a d-link dsl 504t modem router.i still cant connect to internet though but this may be because i dont know what i am doing.if someone could explain it to me or point me in the direction of instructions that would be good.by the way i am using 6.06lts live cd,isp is tiscali.thanks alot!:)

---

### Post by Bachstelze on 2007-03-17
Are you connecting your PC to your router with an Ethernet cable ? If so, it will be very simple, run *ifconfig -a* in a terminal ant paste what you get.

---

### Post by kyusstool on 2007-03-17
yeah its with an ethernet cable!will i have to do anything else after that?will i need to do this everytime i use the live cd?cheers

---

### Post by Bachstelze on 2007-03-17
The Live CD ? It should automagically detect the connection and set it up for you...

---

### Post by kyusstool on 2007-03-17
right ill give it a go!cheers

---

### Post by kyusstool on 2007-03-17
eth0      Link encap:Ethernet  HWaddr 00:13:D3:2D:2F:0B
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d3ff:fe2d:2f0b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1538 (1.5 KiB)  TX bytes:1854 (1.8 KiB)
          Interrupt:225 Base address:0x6000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:372 (372.0 b)  TX bytes:372 (372.0 b)

---

### Post by az on 2007-03-17
> **kyusstool said:**
> hi.completely new to linux.had probs with my speedtouch modem so have now got a d-link dsl 504t modem router.

> **kyusstool said:**
> eth0      Link encap:Ethernet  HWaddr 00:13:D3:2D:2F:0B
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          

Your computer is connected fine to your router.  Now, you must make sure your router is connected to the internet.  Does your router have a configuration page - a page you visit in a browser and where you can tell it to run the setup wizard.  It should be able to detect the kind of connection you have and connect you.

Usually, the configuration page is an ip address, like 192.168.0.1 or 192.168.0.100

---

### Post by kyusstool on 2007-03-17
yeah its got a configuration page that works in windows with firefox but could not get it to load in firefox in ubuntu!!

---

### Post by kyusstool on 2007-03-20
anyone else got any ideas??:)

---

