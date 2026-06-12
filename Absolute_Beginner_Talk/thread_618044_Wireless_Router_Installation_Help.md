---
title: "Wireless Router Installation Help"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by lookmomimonlinux on 2007-11-20
How do I get my router configured to work with ubuntu? I'm still very new to this

---

### Post by JawsThemeSwimming428 on 2007-11-20
What type of router is it and what type of Internet connection do you have? If you have a wireless router you would set it up the same way you would if you have a Windows or Mac machine. It is the wireless adapter you need to configure to work with Ubuntu, IF it does not work out of the box (which is becoming more and more the standard).

---

### Post by lookmomimonlinux on 2007-11-20
It is a "Belkin Wireless G Router", I connected the cable internet modem to the wireless router and the wireless router to my desktop. When that's setup I cannot get an internet connection to the desktop. How do i configure this?

---

### Post by CCNA_student on 2007-11-20
To configure your wireless router type in the IP address of you router in your web browser, and then tell the router to use DHCP to assign addresses and you should be fine.

---

### Post by lookmomimonlinux on 2007-11-20
Where do I find the IP address of my router?

---

### Post by CCNA_student on 2007-11-20
Try 192.168.0.1.

---

### Post by lookmomimonlinux on 2007-11-20
ok, so i type 192.168.0.1.in my web browser, you mean like the firefox search bar? it didn't do anything but say "Probelm loading page" if so

---

### Post by CCNA_student on 2007-11-20
How are you connected to the router, by a wireless connection or by an ethernet cable?

---

### Post by markharding557 on 2007-11-20
is your pc connected to router via cable or wireless

---

### Post by lookmomimonlinux on 2007-11-20
Right now I am connect through my cable modem, when I plug in my wireless router I cannot get online.

---

### Post by CCNA_student on 2007-11-20
So you connect to the router through an ethernet cable?

---

### Post by markharding557 on 2007-11-20
what we mean is the connection between router and computer

---

### Post by markharding557 on 2007-11-20
when you plug in your router is this wireless or cabled

---

### Post by lookmomimonlinux on 2007-11-20
The connection between the router and computer is cabled, sorry if i'm being slow about this, this is all new to me.

---

### Post by CCNA_student on 2007-11-20
I brought that up because many wireless NIC's, like most of those from Broadcom do 
not run properly on Linux. Try 192.168.1.1 in your web browser. This is how most wireless routers can be configured.

---

### Post by _oOMOo_ on 2007-11-20
[http://192.168.0.1](http://192.168.0.1) OR [http://192.168.0.254](http://192.168.0.254) OR [http://192.168.1.1](http://192.168.1.1) as CCNA says should bring up the web interface for the router.

When the cable is plugged in to the router from your computer, does an LED show up on the router to indicate connectivity - some ethernet cards need a few xtra settings but if the LED shows up (assuming there is one) then you should be fine

---

### Post by lookmomimonlinux on 2007-11-22
When i enter in all of those links you gave me the connection times out and the internet light just blinks on the wireless router.

---

### Post by Nessa on 2007-11-22
While you're plugged into any of the numbered ports on the router, open a terminal and type in "ifconfig" without the quotation marks and post the results.

---

### Post by lookmomimonlinux on 2007-11-22
eth0      Link encap:Ethernet  HWaddr 00:13:20:53:D9:C6  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::213:20ff:fe53:d9c6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:30726 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1782 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3178072 (3.0 MB)  TX bytes:299073 (292.0 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1000 (1000.0 b)  TX bytes:1000 (1000.0 b)

---

### Post by Nessa on 2007-11-22
Open a browser and type in 192.168.2.2 or 192.168.2.255. You should get a login screen for your router. If you don't know the router's username and password, check the brand's manual or website.

---

### Post by lookmomimonlinux on 2007-11-22
nothing happens when i type those in, connection just times out

---

### Post by stevemu on 2007-11-22
Try 192.168.2.1  that is what most Belkin Routers use - I think.

---

### Post by bobpur on 2007-11-22
I agree with stevemu. I have a Belkin Pre N router that uses 192.168.2.1.

---

### Post by Nessa on 2007-11-22
Since it's cable, you might need to do a "mac address clone" on the router so that it can get a public ip address from the modem. Btw, can other computers go online on the router or do you only have your ubuntu box to work with?

---

### Post by lookmomimonlinux on 2007-11-22
that line timed out as well and i only have my ubuntu box. how do i perform a "mac address clone"?

---

### Post by Nessa on 2007-11-22
We have to find out your router's ip address first. 

1) Using the terminal, type in "ping xxx.xxx.x.x" (ex. ping 192.168.2.1) on each of those sets of numbers and let us know which set gives you replies. To stop the ping, just press control and C on the keyboard. 

2) If none of them gives you replies. Uplug the router for a few seconds then plug it back in. 

3) If still no replies on any of them, you might need to do a reset on the router first. 

Was the router working before or is this an initial setup?

---

### Post by lookmomimonlinux on 2007-11-23
this is the initial setup and i think the example you provided did what it was supposed to:

PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
64 bytes from 192.168.2.1: icmp_seq=1 ttl=64 time=0.498 ms
64 bytes from 192.168.2.1: icmp_seq=2 ttl=64 time=0.496 ms
64 bytes from 192.168.2.1: icmp_seq=3 ttl=64 time=0.493 ms
64 bytes from 192.168.2.1: icmp_seq=4 ttl=64 time=0.491 ms
64 bytes from 192.168.2.1: icmp_seq=5 ttl=64 time=0.488 ms
64 bytes from 192.168.2.1: icmp_seq=6 ttl=64 time=0.499 ms
64 bytes from 192.168.2.1: icmp_seq=7 ttl=64 time=0.492 ms
64 bytes from 192.168.2.1: icmp_seq=8 ttl=64 time=0.509 ms
64 bytes from 192.168.2.1: icmp_seq=9 ttl=64 time=0.493 ms
64 bytes from 192.168.2.1: icmp_seq=10 ttl=64 time=0.503 ms
64 bytes from 192.168.2.1: icmp_seq=11 ttl=64 time=5.19 ms
64 bytes from 192.168.2.1: icmp_seq=12 ttl=64 time=0.493 ms

--- 192.168.2.1 ping statistics ---
12 packets transmitted, 12 received, 0% packet loss, time 10996ms
rtt min/avg/max/mdev = 0.488/0.887/5.195/1.299 ms

^that's when i cancelled it

---

### Post by Nessa on 2007-11-23
On your browser try typing in [http://192.168.2.1](http://192.168.2.1) on the address bar. Do you still get a time out window?

(need to go to bed now, hopefully someone else can continue)

---

### Post by lookmomimonlinux on 2007-11-23
unfortunately yes, thanks to everyone that responded but i need sleep as well

---

### Post by Talon2 on 2007-11-23
Many of the helpful folks here are giving you suggestions that are based the assumption that you have your new router setup properly.  I've seen no evidence that this is the case.

I recommend that you get the owners manual for your new router and the owners manual for your dsl/cable modem and read them.  The folks in this forum can and will be very helpful with Ubuntu related problems and with hardware specific problems if you can narrow down what the problem may be.  There are a lot of different kinds of hardware and even more ways for this hardware to be configured.  How you configure your new router may depend on how your dsl/cable modem is already configured.  You need to do some work on your end and come back here with specific information about what you are trying to do, what equipment you are doing it with and how that equipment is configured.

Good luck.

---

### Post by Nessa on 2007-11-23
I got some sleep. ;)

Routers usually come with just a few pages of text about the router and a windows/mac setup cd. I'm still new to Ubuntu. I'll share what I can anyway.

-We know your router's ip address is 192.168.2.1 (ping results ok)
-Browser times out when trying to access that address

Talking about the windows environment: we usually check the browser settings and make sure there's no proxies. If we still can't access it, turn off firewalls on the pc. Not sure if that's possible on Ubuntu. If you still can't access it, turn off the router for a few seconds then back on. If still no go, do a reset on the router. If still nothing, you'll have to try it with another pc. If the same thing, maybe firmware upgrade using software from the manufacturer. (Linksys has one, I'm pretty sure other brands have their own version. They also have a model for Linux users.) If all else fails, return to store?

Once we can open that router page, we're already halfway there. Maybe someone more familiar with Ubuntu can give more input about how to access that page.

---

