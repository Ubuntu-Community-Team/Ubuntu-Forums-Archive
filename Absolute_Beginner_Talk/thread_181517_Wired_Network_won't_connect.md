---
title: "Wired Network won't connect"
date: 2006-05-24
forum: Absolute Beginner Talk
---

### Post by Haulfron on 2006-05-24
Hi, I was given old PC (pentium 600MHz 128MB RAM) and am trying to set it up as a home server using Ubuntu. I have same problem when Ubuntu is installed with/without GUI. Any of 3 network cards have same problem. The NIC light is on, a connection to an XP Pc, via switch, displays "network connected" but in all cases there is no traffic. Is there a firewall in Ubuntu that has to be configured first, or some other  simple problem that this newbie has missed?

---

### Post by nanotube on 2006-05-24
hmm, can you open a terminal, and post output of 'ifconfig' ?

---

### Post by Haulfron on 2006-05-24
This is ifconfig for eth0

Link encap:Ethernet HWaddr 00:10:B5:0E:DB:77
inet addr:192.168.1.11 Bcast:192.168.1.255 Mask:255.255.255.0
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 frame:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b) 
interrupt:11 Base address:0xd400

Thanks for looking at this, by the way.

---

### Post by nanotube on 2006-05-24
hmm, that ifconfig looks good... you have the ip address and everything.
by default, ubuntu does not come with a firewall - but XP has the firewall enabled, if you have sp2 on it. maybe that's the problem?
from your ubuntu comp, you can open up a browser, and go to 192.168.1.1 (the router config page), and see if that shows up. if that works, that means that your network on ubuntu is configured properly, and that the problem lies somewhere else, and we will go from there. :)

---

### Post by costoa on 2006-05-24
Could you also post the output from /etc/network/interfaces please?

---

### Post by Haulfron on 2006-05-25
[QUOTE=nanotube]hmm, that ifconfig looks good... you have the ip address and everything.
by default, ubuntu does not come with a firewall - but XP has the firewall enabled, if you have sp2 on it. maybe that's the problem?
from your ubuntu comp, you can open up a browser, and go to 192.168.1.1 (the router config page), and see if that shows up. if that works, that means that your network on ubuntu is configured properly, and that the problem lies somewhere else, and we will go from there. :)[/QUOTE]
ok, I have installed server/no-gui version. Swapping network connection between XP PC and Ubuntu PC and pinging router works on XP, but produces message "Network is unreachable" on Ubuntu. I have also checked router for any filters, etc but it is all on default setting (including DHCP - Ubuntu IP address set manually during install within DHCP range.) I have looked at processes using "top" but I don't know what applies to networking.

---

### Post by ProjectGod on 2006-05-25
is the network using DHCP or static ips? i think you havent configured the default gateway on your ubuntu machine to point to the router.

furthermore... the XP machine is likely to have as nanotube said a firewall... in which case you must enable traffic from your ubuntu machine as being safe.

afterwards try pinging your xp machine from ubuntu and vise versa. :mrgreen:

---

### Post by Haulfron on 2006-05-25
[QUOTE=costoa]Could you also post the output from /etc/network/interfaces please?[/QUOTE]
Relevant entries (ie not commented out) are:

auto lo
iface lo inet loopback

mapping hotplug
               script grep
               map eth0

Pinging 127.0.0.1 produces a good reply.
Pinging 192.168.1.1 (router address) produces "Network unreachable"
moving connection to XP PC and pinging router works ok.

---

### Post by ProjectGod on 2006-05-25
type this at the terminal

**sudo pico /etc/network/interfaces**

scroll down cause there should be more output...

---

### Post by Haulfron on 2006-05-25
[QUOTE=ProjectGod]is the network using DHCP or static ips? i think you havent configured the default gateway on your ubuntu machine to point to the router.

furthermore... the XP machine is likely to have as nanotube said a firewall... in which case you must enable traffic from your ubuntu machine as being safe.

afterwards try pinging your xp machine from ubuntu and vise versa. :mrgreen:[/QUOTE]
Network is using DHCP but since no connection was available Ubuntu has been configured with static address within DHCP range - well clear of any assigned addresses.  XP firewall set to accept all local network.

---

### Post by Haulfron on 2006-05-25
[QUOTE=ProjectGod]type this at the terminal

**sudo pico /etc/network/interfaces**

scroll down cause there should be more output...[/QUOTE]
No more output than

auto lo
iface lo inet loopback

mapping hotplug
script grep
map eth0

---

### Post by ProjectGod on 2006-05-25
i think you'll have to enable DHCP on the ubuntu also. that is to say unless your router allows you to create and "exclusion list" or "static mappings"... 

don't worry about short dhcp leases because you can share resources... make your ubuntu machine a server with other hosts connected to it by using DNS host names...

you can't use the arrows on your keyboard to scroll down???? odd.

---

### Post by carverj on 2006-05-25
Have you input the gateway address?
I'm not 100% certain, but I believe if the error message is request timed out, the host cannot make a connection with the server/router if down.
As your message is Network unreachable, the host cannot find the server/router. 
Apologies if I have mixed these up and please post so if incorrect

______________
banging ones head will only make matters worse
:p

---

### Post by ingo on 2006-05-25
OK, try and adjust your /etc/network/interfaces to include

auto eth0
iface eth0 inet dhcp

restart your network and let us know how you get on

---

### Post by costoa on 2006-05-25
Ok, /etc/network/interfaces should have the following:

```

auto lo
iface lo inet loopback

iface eth0 inet dhcp
auto eth0

```

Then issue:
```
sudo ifdown eth0 && sudo ifup eth0
```

If all goes well you'll see the output from the DHCP process and be up. Please let us know what works and what doesn't. BTW, while ubuntu will run well on a P3 it will run much better if you could dig up another 128M of RAM.

---

### Post by ingo on 2006-05-25
[quote=costoa]BTW, while ubuntu will run well on a P3 it will run much better if you could dig up another 128M of RAM.[/quote]

Alternatively, try Xubuntu! Runs like a dream on my 333Mhz, 168MB Ram IBM Thinkpad 600E:p

---

### Post by Haulfron on 2006-05-25
Problem is now sorted by removing dial-up modem card from backplane and stamping on it.  Thanks for all your help.

---

