---
title: "access internet"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by odwyerda on 2008-04-16
Ok i just installed FF on a mates laptop that was broken so I can try a clean install on his laptop but I cannot seem to get onto a network.
When I installed my FF it worked straight out of the box directly on to my college intranet and internet via a proxy.
Now with this laptop I cannot get online at all.

I have set up the DCHP to be automatic,
as for
"Network Settings/General" no idea what to put in  same goes for DNS and host.

When I put i ifconfig i get
> 
Eth0   
Link encap : Ethernet   HWadd 00:40: D0:7F:51:C3
UP BROADCAST MULTICAST MTU :1500  Metric :1
RX packets:82 errors:0 Dropped :0 overruns :0 carrier:0
collisions:0  txqueuelen:1000
RX bytes:10485742 (9.9mb) TX bytes)12455 (12.1Kb)
Interrupt:3 Base Address: 0xc000 

lo
Link encap: Local Loopback
inet addr:127.0.0.1 Mask: 255.0.0.0
inet6 addr:   ::1/128 Scope:Host
UP LOOPBACK RUNNING    MTU:16436  Metric:1
RX packets:2280  errors:0 Dropped :0 overruns :0 frame:0
TX packets:2280  errors:0 Dropped :0 overruns :0 carrier:0
collisions:0 txqueuelen:0
RX bytes:161952 (158.1kb) TX bytes:161952 (158.1kb)




no idea what to do next.


dave

---

### Post by superprash2003 on 2008-04-16
are you able to ping? type ping google.com and post results here

---

### Post by odwyerda on 2008-04-16
ping:unknown host google.com

---

### Post by superprash2003 on 2008-04-16
you dont seem to be getting an ip in eth0!!are you sure you set eth0 to DHCP?

---

### Post by odwyerda on 2008-04-17
Wired Connection
Address dhcp

after that i dunno.

im trying to connect through a proxy but all i need to do there is put the proxy into firefox and i should be on the net

---

### Post by odwyerda on 2008-04-17
I have changed everything to how my own laptop access the net and still i get no connection might be a driver issue??
net doesnt even register anymore

---

### Post by odwyerda on 2008-04-17
One more update sorry.

Restricted drivers are coming up, I enabled them and restarted still nothing. I cant get on the net to update them, i presume I can download them somewhere burn a cd and install?

---

### Post by bumanie on 2008-04-17
Try this 
Open firefox, in the address bar type about:config. In the filter, type ipv6 Right click on the line that appears and then left click on toggle to change the value to true. Reboot and see what happens. It is the only way I could get gutsy to connect to the internet by disabling ipv6 in firefox. If it doesn't work you can reverse your changes by returning to toggle and changing the value back to false. I did not find the same problem with FF or HH.

---

### Post by odwyerda on 2008-04-17
nope did nothing,
I think the ubuntu its self is not seeing anyting to get it on the net rather than it being a firefox issue, thats my inclination

---

### Post by odwyerda on 2008-04-17
Apparently in the bios is is turned on. When I turned it off I couldn't change any setting for the ethernet, so thats not it.....hmmm 

[I]I think i found a solution but I have no idea how to do it,
It appears that the laptop Packard Bell e2250 has the ethernet board turned off by default, and I can change it in the BIOS but I dont know how to access it[/I]

---

