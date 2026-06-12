---
title: "Ubuntu no longer connects to internet (wired LAN)!"
date: 2006-03-26
forum: Absolute Beginner Talk
---

### Post by QuacoreZX on 2006-03-26
common n00bish question I'm sure...anyways, ubuntu used to play fine with my ADSL connection via eth0, but now for some reason it absolutely refuses to!  In the gui network manager, eth0 IS up, dhcp enabled.  When I open terminal, then ifconfig, it has an ip address and everything.  However, when I try Firefox or any net app...nada....any help? x_x

---

### Post by dermotti on 2006-03-26
Can you ping google.com?

Can you ping 72.14.207.99 ?

---

### Post by QuacoreZX on 2006-03-26
nope, can't ping anything.

---

### Post by tonitee on 2006-03-26
same problem here, internet connection just stopped working this morning.

---

### Post by mneptok on 2006-03-26
Have you tried pinging by IP address and not hostname? If not, try it. If it works, you're probably not getting DNS set properly by DHCP.

---

### Post by tonitee on 2006-03-26
i tried, but the network is unreachable. weird. the connection should be ok, since another computer (with windows) connects without problems.

---

### Post by mneptok on 2006-03-26
Are you using a router, or connecting directly?

If you're connecting directly, be aware that many ISPs check your MAC address. Every network interface has a unique MAC address, and if you connect using one machine, your ISP may well limit connectivity to that MAC address only henceforth. They can reset it, but you'll have to ask them to do so. Then, the next machine that connects gets its MAC address authorized.

A router eliminates this problem, as its MAC address gets authorized, and the machines behind it are not affected.

---

### Post by tonitee on 2006-03-26
Yes, i am using a router (shared modem with my neighbour), and so far there has not been problems when using the same cable with these two different machines.
Light in the network card is burning.
I'm quite a newbie with Ubuntu and Linux, as you might guess...

---

### Post by cisde on 2006-03-28
Open a terminal and type 
ifconfig -a
This shoould tell you whether you have actually been assigned an IP address to eth0, your default network card - quite possibly 192.168.x.y
If that looks good, try to ping that IP address from another machine on the same network.
David

---

### Post by mrbiscuit on 2006-03-28
I had problems with using Net-Apps once even though my connection was working perfectly fine. However, this may be a solution. Ubuntu comes with IP-V6 enabled by default. However, a lot of hardware still uses the IPV4 protocal and cannot understand when your computer sends the IPV6 instructions. This wiki may help: [https://wiki.ubuntu.com/WebBrowsingSlowIPv6IPv4]("https://wiki.ubuntu.com/WebBrowsingSlowIPv6IPv4")

---

### Post by jamesr on 2006-03-28
I agree there seem to be a fair of number of network problems associated with ipV6 and routers.

Can you ping the ping the router.

Also posting the outputs would help. You can always copy and paste to file etc.
Also post the output of
```
sudo ifconfig -a 
```

---

### Post by tonitee on 2006-04-17
Sorry for this long delay before i'm finally reacting, and thanks for your kind advise.

I did ifconfig -a, but the output showed only zeros.

Since i had somehow been able to crash several applications in my system (maybe due to careless installing of unsafe packages) i decided to re-install ubuntu and now everything, including the network connection, works better than ever. 

My apologies for not contributing to solving this problem in a more sophisticated manner...

Toni

---

### Post by tonitee on 2006-04-17
Noooo, this can't be true! The same happened again. Now I was browsing a web radio while the computer suddenly freezed. After rebooting it it does not find the network card anymore.

The output of ifconfig -a:

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4830 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4830 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:437367 (427.1 KiB)  TX bytes:437367 (427.1 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


I changed the network card after the connection first broke down, so the problem seems not to be in the card.

Anyone who could help?

---

