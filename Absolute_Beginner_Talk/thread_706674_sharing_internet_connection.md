---
title: "sharing internet connection"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by thomas7.10 on 2008-02-24
HI!

I know there are a lot of threads about this and i followed the instruction on [http://ubuntuforums.org/showthread.php?t=91370]("http://ubuntuforums.org/showthread.php?t=91370") . But it still doesn't work.

What i want to do is sharing my internet connection with 3 other PCs by using a netgear router and my computer. I have two network interfaces one is going directly to the internet (eth0) and the other should provide internet access to the network (eth1).

When i connect my pc to the router using a LAN slot i can ping it from another pc. I do neither use DHCP nor DNS.
The ifconfig is basically that:

eth0      Link encap:Ethernet  HWaddr 00:19:DB:37:55:B3  
          inet addr:87.130.73.36  Bcast:89.160.93.255  Mask:255.255.255.0
          inet6 addr: fe80::219:dbff:fe37:55b3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:494320 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8939 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:36342665 (34.6 MB)  TX bytes:910561 (889.2 KB)
          Interrupt:20 Base address:0xc800 

eth1      Link encap:Ethernet  HWaddr 00:17:9A:B4:97:C1  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::217:9aff:feb4:97c1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:155390 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4566 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15431887 (14.7 MB)  TX bytes:521282 (509.0 KB)
          Interrupt:19 Base address:0xf800 

On the Windows laptop i set the IP adress to 192.168.0.2 the submask to 255.255.255.0 and the gateway to 192.168.0.1. I tried both leaving the DNS blank or using the DNS of the provider i have. Both didn't work.

I installed firestarter as well. When i activate it and block everything i can see that 192.168.0.2 was trying to get something from HTTP if i try to visit the google website.

I tried aswell to connect the eth1 to the WAN slot of my router. If i do so the router says it is recognizing my internet connection as a fixed ip and i was asked to enter the IP adress gateway and DNS. I tried to configure it as i did with the laptop but i can't connect.

I thought maybe it is about the router but it isn't i connected the laptop to my PC directly. I can ping the PC from the laptop but i can't visit google.

So could someone please help me and tell me what i did wrong? 

By the way. My firewall is blocking lots of strange packages comming from MY OWN external IP on very high UDP ports and packages that are comming from nearly the same IP adress on the samba ports. With nearly the same i mean i have for example 87.130.73.36 and it is comming from 87.130.73.96. What does this mean?

I would be really happy about some answers i keep on plugging things in and out, reading in this forum, trying this and that for about 4 hours.

Thomas

---

### Post by willmcgree on 2008-02-24
From what I can see, your connection looks like this:

Internet - Modem - Your PC - Router - Other PCs

If not, let me know.

The simplest solution to this problem (as far as I can see) would be to use the router at the top and just connect every computer to it:

Internet - Modem - Router - All PCs

Maybe you've tried this and it hasn't worked, but by letting the router handle where your packets go, there's less translation involved. My setup works like this, with the modem directly plugged into the router.

If you were using a USB modem, the solution you propose might be suitable, but since everything is Ethernet, it's far easier to let a dedicated device do it.

I can't imagine any real benefit in shoehorning your PC between the modem and the router. Heck, I'm thinking about running a home server and media tank with remote outside access, but I'll still be leaving that box behind the router. From a security point of view, it's safer for machines that talk to the Internet not to have an 80-something IP address since that leaves them wide open to attacks from the Web. Being behind a router means your address has to be translated from 80-something to 192.168.0.xxx and back when you use the Internet, meaning attackers can't (easily) get around your router. This isn't as good as a firewall, but really, you should be running one of these on each machine for optimum protection.

You also won't have to wrangle with things like assigning individual IP addresses (*sigh*... like the old days) since DHCP on the router will handle that. If you want, you can turn DHCP off and use fixed addresses if they're absolutely mission-critical, but why bother most of the time?

Hope this helps.
Will

---

### Post by thomas7.10 on 2008-02-24
Thanks for your answer!

My connection looks like this:

Internet - PC - Router - other PCs

I live in Stockholm (Sweden) and we have a network slot in the wall. We don't need to log in or something it just works. Well it is supposed to just work but it doesn't when using a router. We tried two different routers but it's always the same problem. Suddenly the internet is becoming very slow and then it strikes. You can fix this by removing the power supply for the router for about 20 sec. and then it works again. But this can be quiet annoying. When connecting a PC to this network slot in the wall everything works just fine. We were told by the local internet provider that something is wrong with our network settings or with our router. So that's why i'm trying to get it to work that way..
But after trying to get this to work for several hours i can get used to the thought that we have 4 cables in front of the network slot and just one person can use internet at the same time.

Thomas

---

### Post by thomas7.10 on 2008-02-24
got it to work - thanks anyway

---

