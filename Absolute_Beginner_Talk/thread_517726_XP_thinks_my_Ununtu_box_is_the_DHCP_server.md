---
title: "XP thinks my Ununtu box is the DHCP server"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by kpictjl on 2007-08-04
When my Ubuntu Feisty box is on, my Windows XP box thinks the Feisty box is the DHCP server and the XP box is the DNS.  I want my router to be the DHCP/DNS server.  

Here's my setup.
Netgear Router/Switch/WAP - I want this to provide DHCP/DNS
1 Ubuntu Feisty Box
2 Windows XP PCs 

If my Feisty box is off then DHCP on the 2 XP boxes works fine.  
If I go static IPs then all is is well. 
I want my computers to all be DHCP.

It *seems* like the network thinks the Feisty box is the DHCP server and I don't know how that could have begun.  This setup with 3 DHCP pcs has been working fine for about a year.

This all started friday night immediately after I installed an automatic update to the Feisty box.  The list of updated packages is below.  I'd like to back these out if I could.

```
Commit Log for Fri Aug  3 21:02:37 2007
Upgraded the following packages:
dbus (1.0.2-1ubuntu3) to 1.0.2-1ubuntu4
dbus-1-utils (1.0.2-1ubuntu3) to 1.0.2-1ubuntu4
libdbus-1-3 (1.0.2-1ubuntu3) to 1.0.2-1ubuntu4
libqt3-mt (3:3.3.8really3.3.7-0ubuntu5) to 3:3.3.8really3.3.7-0ubuntu5.1
python-launchpad-bugs (0.1.13) to 0.1.13.2
tzdata (2007e-0ubuntu0.7.04) to 2007f-0ubuntu0.7.4
```

Thanks.

---

### Post by jimrz on 2007-08-05
> **kpictjl said:**
> When my Ubuntu Feisty box is on, my Windows XP box thinks the Feisty box is the DHCP server and the XP box is the DNS.  I want my router to be the DHCP/DNS server.  

Here's my setup.
Netgear Router/Switch/WAP - I want this to provide DHCP/DNS
1 Ubuntu Feisty Box
2 Windows XP PCs 

If my Feisty box is off then DHCP on the 2 XP boxes works fine.  
If I go static IPs then all is is well. 
I want my computers to all be DHCP.

It *seems* like the network thinks the Feisty box is the DHCP server and I don't know how that could have begun.  This setup with 3 DHCP pcs has been working fine for about a year.

This all started friday night immediately after I installed an automatic update to the Feisty box.  The list of updated packages is below.  I'd like to back these out if I could.

```
Commit Log for Fri Aug  3 21:02:37 2007
Upgraded the following packages:
dbus (1.0.2-1ubuntu3) to 1.0.2-1ubuntu4
dbus-1-utils (1.0.2-1ubuntu3) to 1.0.2-1ubuntu4
libdbus-1-3 (1.0.2-1ubuntu3) to 1.0.2-1ubuntu4
libqt3-mt (3:3.3.8really3.3.7-0ubuntu5) to 3:3.3.8really3.3.7-0ubuntu5.1
python-launchpad-bugs (0.1.13) to 0.1.13.2
tzdata (2007e-0ubuntu0.7.04) to 2007f-0ubuntu0.7.4
```

Thanks.

might need more info on your network setup, but first thing to do is go to your router (Neatgear default ip = 192.168.0.1) and go to LAN IP Setup.make sure there is a check mark in the box for "use router as DHCP server" (or similar). On the same page you can select to get DNS automaticcaly from your ISP or specify your choice of DNS servers + if you find static ip functionality useful you can setup address reservations (by computer name and MAC address)  which will effectively provides static ip's while still using DHCP

---

### Post by kpictjl on 2007-08-05
> **jimrz said:**
> might need more info on your network setup, but first thing to do is go to your router (Neatgear default ip = 192.168.0.1) 
I switched mine to 1.1 last year for not good reason other that I like 1.1.

> and go to LAN IP Setup.make sure there is a check mark in the box for "use router as DHCP server" (or similar).
verified

>  On the same page you can select to get DNS automaticcaly from your ISP
verified

>   if you find static ip functionality useful you can setup address reservations (by computer name and MAC address)  which will effectively provides static ip's while still using DHCP
I have these reservations set up so I don't have to mess with static ip's on each machine.

---

### Post by jimrz on 2007-08-05
> **kpictjl said:**
> I switched mine to 1.1 last year for not good reason other that I like 1.1.


verified


verified


I have these reservations set up so I don't have to mess with static ip's on each machine.

guess it's not anything in the router then. not clear on how the ubuntu update (I installed same one on all of my home network machines without encountering anything like this and have not seen any other threads here indicating that others have) could cause this confusion for your win boxes. looks like you are stuck with digging through your network settings on both sides until you locate whatever is pointing the win boxes astray. 

afraid I do not know how you would go about reverting to the pre-update versions and , considering the packages involved, I do not think removing then re-installing them would be doable

**EDIT: **in case it helps you narrow your hunt, here is my setup:

Netgear router - similar setup to your's, including address reservations
1 server - feisty, no domain, just a simple workgroup 
2 desktops - feisty(1 dual boot w/xp)
2 laptops - feisty(1 dual boot w/xp)

During the span of time that the updates were applied to the various machines no win machine was attached to the netwok
Since then, however, both dual boot machines have been attached while running xp and neither has encountered this problem.

good luck ... hope it turns out to be something that is simple to fix

---

### Post by kpictjl on 2007-08-05
> **jimrz said:**
> 
good luck ... hope it turns out to be something that is simple to fix

jimrz - thanks for taking the time.  I guess this is why my sys admins at work do static ips on all the machines, just 1 less this to worry about.

---

### Post by kpictjl on 2007-08-05
I see that dhcpd3 is running but using the conf file from ltsp.  I wonder if that is trying to serve up ip addresses to my network.  I did mess around with ltsp a couple weeks ago. 
```

>$ ps -ef | grep dhcp3
dhcpd     5601     1  0 Aug04 ?        00:00:00 /usr/sbin/dhcpd3 -q -pf /var/run/dhcp3-server/dhcpd.pid -cf /etc/ltsp/dhcpd.conf

```
First I'm going to uninstall ltsp using syaptic.
Next I goto System -> Admniistration ->services and stop the DHCP server.
Next I when to System -> Administration -> Network and switched from static ip to DHCP.

Now dhcp3 is running but not using the ltsp conf file.  It looks more like a what I want it to be, notice the "dhcpclient" parameter.

```

>$ ps -ef | grep dhcp
dhcp      3854     1  0 20:08 ?        00:00:00 dhclient3 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leases eth0

```

so far all it well.

---

### Post by jimrz on 2007-08-05
> **kpictjl said:**
> I see that dhcpd3 is running but using the conf file from ltsp.  I wonder if that is trying to serve up ip addresses to my network.  I did mess around with ltsp a couple weeks ago. 
```

>$ ps -ef | grep dhcp3
dhcpd     5601     1  0 Aug04 ?        00:00:00 /usr/sbin/dhcpd3 -q -pf /var/run/dhcp3-server/dhcpd.pid -cf /etc/ltsp/dhcpd.conf

```
First I'm going to uninstall ltsp using syaptic.
Next I goto System -> Admniistration ->services and stop the DHCP server.
Next I when to System -> Administration -> Network and switched from static ip to DHCP.

Now dhcp3 is running but not using the ltsp conf file.  It looks more like a what I want it to be, notice the "dhcpclient" parameter.

```

>$ ps -ef | grep dhcp
dhcp      3854     1  0 20:08 ?        00:00:00 dhclient3 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leases eth0

```

so far all it well.

nice ... glad you found it and hope that covers the whole problem. not even gonna ask what all else you dug around in before arriving at this ;)

---

