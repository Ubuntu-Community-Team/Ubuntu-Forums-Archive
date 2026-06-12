---
title: "'eth0' failed: Invalid argument"
date: 2006-01-27
forum: Absolute Beginner Talk
---

### Post by drifterman2006 on 2006-01-27
Hi Guys,

Sorry if this is a simple question but I've installed linux and when I plug my laptop into my D-link internet router nothing seems to happen. When I try 

sudo  mii-tool eth0

i get 
'eth0' failed: Invalid argument

Also when do 
route -n

nothing comes back on the IP routing table.

The router is connecting ok with another pc (running windows) to the Net.

any thoughts, apologies again if this is a stupid question.
cheers,
Al

---

### Post by ubuntuuser on 2006-01-27
Please give us the output of ```
ifconfig
``` and, if it shows no information about eth0, give us the output of ```
ifconfig eth0
``` instead. Try to ping your adapter and your router with ```
ping IP.address.here.please
``` and present that output, too. Maybe we can help you more then. What exactly did you do to setup your adapter?

---

### Post by drifterman2006 on 2006-01-28
Thanks for the reply, the first thing I should say is that I didn't configure my adapter, all I did was plug in my ethernet cable from my laptop into the adapter. I haven't set up and adapter before so apologies is this is such a simple mistake. What steps do I need to take to configure the adapter ?

As to the outputs...

ifconfig 

Link encap: Local Loopback
inet addr:127.0.0.1 Mask 255.0.0.0
inet6 addr ::1/128  Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:16112 errors:0 dropped:0 overruns:0 frame:0
TX packets:16112 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:1457601 (1.3 MiB) TX bytes:1457601 (1.3 MiB)

ifconfig eth0

Link encap: Ethernet HWaddr 00:40:D0:42:6C:5F
BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes: 0 (0.0 b) TX bytes:0 (0.0 b)
Interrupt:10 Base address:0xe300


Some extra information :-

when I do **ipconfig **from the windows machine which is also connected to the Router I get the following output :

0 Ethernet adaptador :
	Direcci¢n IP . . . . . . . . . . . . . : 0.0.0.0
	M*scara de subred  . . . . . . . . . . : 0.0.0.0
	Puerta de enlace predeterminada  . . . : 

1 Ethernet adaptador :
	Direcci¢n IP . . . . . . . . . . . . . : 192.168.0.154
	M*scara de subred  . . . . . . . . . . : 255.255.255.0
	Puerta de enlace predeterminada  . . . : 192.168.0.1

the output is in Spanish because I'm in Chile at the minute.

Thanks again for any help, and apologies if this is all basic stuff I'm missing.

cheers,
Al

---

### Post by ubuntuuser on 2006-01-28
The easiest thing to try would be to open a terminal window and type ```
sudo ifconfig eth0 up
sudo dhclient eth0
```

This works if your router has DHCP enabled. If you are using GNOME, you could also try System -> Administration -> Network. After entering your password a window opens where you could easily select and setup your ethernet adapter as well your as gateway and DNS server, if needed.
Be a bit creative with the menu names, I use the German version.

---

### Post by drifterman2006 on 2006-01-29
Resolved......

Thanks for the info, the commands :

sudo ifconfig eth0 up
sudo dhclient eth0

did the trick. Thanks again for your help.

cheers,
Al

---

