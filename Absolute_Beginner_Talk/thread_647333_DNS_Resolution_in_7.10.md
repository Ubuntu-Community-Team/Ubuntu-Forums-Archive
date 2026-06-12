---
title: "DNS Resolution in 7.10"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by dutch_boy on 2007-12-22
Hi,
I'm having a problem with internet access which is really throwing me...hope someone can help.

Network:
D-link DSL-G624T Router wired to a machine with a new 7.10 install dual-booting with Vista.
The router is set to auto-discover DNS server - Pipex are the ISP.

The router also serves other machines - XP, W2000 & a Ubuntu 6.10 build.
None of these machines, including the Vista build on the machine that is giving me the problem exhibit the same symptoms I'm going to describe.

The 7.10 build is new - I've installed Firestarter, but the problem exists unchanged with or without it enabled.
As an attempt solve this problem I've entirely disabled ipv6 - on the system and in Firefox.
In Network Settings, I've changed all the interfaces away from enable roaming mode to DHCP. DNS is set to the router address only.  This mirrors closely the config on the 6.10 build that works fine.

**OK - so, the problem:**
Firefox is absolutely fine...I can browse anywhere at will.
Other software that accesses the internet is failing to obtain domain name resolutions.  
For example: if I fire up Evolution and receive mail, it will hang attempting to contact the mail server.  However, if I then ping the mail server from a terminal, that resolves the name and is successful.  I can then go back to Evolution, receive mail, it will contact the mail server and complete successfully.  Evolution will then continue to be able to receive mail for about ten minutes or so and then fail again until I re-ping the server.
If html mail requires images to be loaded from an internet server these will hang unless I send a ping to them.

Synaptic shows similar behaviour - it will fail to connect and reload info/download unless I ping the selected server immediately before using it.  Alternatively, if I let it select a server for me, it will be able to contact that server for a few minutes but will then start failing again - whichever server it is using.

So - it's as if everything except FireFox and ping are failing to use DNS properly ... or can only use locally cached results.

A few results:
**ifconfig eth0:**
eth0      Link encap:Ethernet  HWaddr 00:18:F3:B6:A0:03  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:234 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16524 (16.1 KB)  TX bytes:2336 (2.2 KB)
          Interrupt:20 

**tracepath [www.ubuntu.com:](www.ubuntu.com:)**
 1:  192.168.1.3 (192.168.1.3)                              0.119ms pmtu 1500
 1:  mygateway1.ar7 (192.168.1.1)                           0.988ms 
 2:  mygateway1.ar7 (192.168.1.1)                         asymm  1   0.938ms pmtu 1492
 3:  ge (62.241.161.185)                                  asymm  4  41.836ms 
 4:  pc3 (62.72.139.21)                                    42.144ms 
 5:  po-2-477-cr0.tch.datahop.it (62.72.139.14)            41.380ms 
 6:  canonical-gw.datahop.net (195.72.130.230)             41.901ms 
 7:  gw0-0-gr.canonical.com (91.189.88.10)

The machine has eth0, eth1 & wlan0, of which only eth0 is connected. One thing I haven't done is attempt to completely remove the config for the interfaces that aren't in use - that's a step further than my Linux knowledge would let me go.

---

### Post by hyper_ch on 2007-12-22
do you have any dns server in your /etc/resolv.conf file?

---

### Post by dutch_boy on 2007-12-22
> **hyper_ch said:**
> do you have any dns server in your /etc/resolv.conf file?
Just the local router:
$ cat /etc/resolv.conf
nameserver 192.168.1.1

---

### Post by hyper_ch on 2007-12-22
that should be enough... you could also try opendns servers if you want to (additionally)

---

### Post by webdr on 2007-12-22
Your Problem:
DNS resolution via local router DNS relay has proven to be a common failure point in my experience.

Try this...
open a terminal.
run this command 
```
sudo gedit /etc/dhcp3/dhclient.conf
```
search for this line... #prepend domain-name-servers 127.0.0.1; insert the following line
after that line. 
```
 prepend domain-name-servers 208.67.222.222,208.67.220.220; 
```

Save the file, disconnect and reconnect, then retest.

What this does...
It hardsets your machine to use OpenDNS nameservers.. you may swap 208.67.xxx.xxx with the IP's of your chosen nameservers, although I think you'll find the OpenDNS servers to be much more efficient.

So, no matter what DNS is handed to you by DHCP, your machine will always behave and use just the DNS servers you tell it to.


-Mark Williams

---

### Post by dutch_boy on 2007-12-22
> **webdr said:**
> 
```
sudo gedit /etc/dhcp3/dhclient.conf
```
search for this line... #prepend domain-name-servers 127.0.0.1; insert the following line
after that line. 
```
 prepend domain-name-servers 208.67.222.222,208.67.220.220; 
```

Save the file, disconnect and reconnect, then retest.

Mark, that worked a treat - seems to have solved the problem.  I just installed msttcorefonts and Synaptic found all the font cabs and downloaded them with no problem.  HTML mail is also being rendered properly.  Thank you.

Although I understand why this works - I'm a bit puzzled as to why 7.10 behaves differently to 6.10 in this respect.  Is it just particular pc/router combinations ? or an acknowledged problem with 7.10 ?  I've seen a few threads that seemed to suggest similar problems ... but often without a clearcut solution.

---

### Post by webdr on 2007-12-22
While I am not 100% sure of the cause of the problem, my conclusion was that something goes wrong with dns relay timing. I didn't pursuit the cause of the timing issue, and instead opted to hardset my DNS entries.

 I typically hardset my DNS anyway, because of an experience I had two years ago when I connected to a network with poisoned dns servers. Ever since, I've opted to hardset my own dns.

Glad it worked well for ya!
-Mark Williams

---

