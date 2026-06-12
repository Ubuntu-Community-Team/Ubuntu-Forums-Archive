---
title: "firefox/internet access problems"
date: 2005-12-02
forum: Absolute Beginner Talk
---

### Post by newblacknoise on 2005-12-02
i've been searching the forums for the answer to this question, but have been unable to find it so far. here's hoping someone can help:

i have installed ubuntu 5.04 on my toshiba tecra A2 notebook, along with Windows XP Pro, on a dual boot setup. At the moment i am just trying to get a plain ethernet connection setup for internet access. the notebook is currently connected via ethernet cable (the tech name escapes me) to a D-Link DI-624+ wireless router, which is in turn connected to a D-Link DI-502 ADSL modem. It seems like the connection itself is working ok. I've setup the network card in the GUI network setup application (in System Tools) to use DHCP, and i can now successfully ping both the modem and the router, as well as a number of external addresses (eg. [www.hotmail.com](www.hotmail.com), [www.ubuntulinux.com)](www.ubuntulinux.com)). however, when i open firefox, i can't get any internet access. it just times out trying to connect. the following is the output when i used 'ifconf' in the terminal (i'm not sure what it all means, but i saw a lot of people requested this info when trying to sort out similar problems on the forums):

```
eth0      Link encap:Ethernet  HWaddr 00:0E:35:AB:BC:88
          inet6 addr: fe80::20e:35ff:feab:bc88/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5694 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2552 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0x8000 Memory:cffff000-cfffffff

eth1      Link encap:Ethernet  HWaddr 00:0E:7B:55:5F:5D
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:7bff:fe55:5f5d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:818 errors:0 dropped:0 overruns:0 frame:0
          TX packets:240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:266174 (259.9 KiB)  TX bytes:20628 (20.1 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4195 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4195 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:379974 (371.0 KiB)  TX bytes:379974 (371.0 KiB)




```

now, the fact that it shows i have gotten an IP address, and that the ping works fine, tells me it's probably some dead simple setting in firefox i've not configured properly. i really hope that's all it is. i've been a windows user for a long time, and whilst i'm keen to get down and dirty with linux, i don't know what i'm doing yet :) windows has always done all the hard work for me, so i never really had to tinker with these settings before. once i get this sorted out, i can tackle to fun problem of my wireless setup (oh happy day!) :D 

anyway, i appreciate any help that can be given.
after reading a lot of the forums, i can see that there is a very helpful community around ubuntu, and one which i hope i can contribute to one day, once i figure all this stuff out!

adrian.

---

### Post by adduds on 2005-12-02
Hey adrian!

I'm running the same DI-624, i'm not exactly sure about your firefox problem. But what I saw from you code it looks like the DHCP is assigning eth1 your ip address 192.168.0.100.  But i'm very new w/ linux I have Ubuntu 5.10 and what i could tell you is to sudo apt-get firefox and sudo apt-get firefox-gnome-support.

---

### Post by newblacknoise on 2005-12-02
thanks for the reply adduds, but those commands you recommended didn't work for me. however, i did (eventually) find a post which fixed the problem lovely jubbly!

[http://www.ubuntuforums.org/showpost.php?p=533158&postcount=26](http://www.ubuntuforums.org/showpost.php?p=533158&postcount=26)

so for anyone having the same problem, follow the instrucitons given and hopefully it can work for you too. i'm going to do a little research into what this IPv6 thing is.

now to figure out my wireless connection... :)

---

