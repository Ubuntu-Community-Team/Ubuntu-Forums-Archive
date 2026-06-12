---
title: "Firestarter &amp; network security"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by TreverT on 2008-02-12
We've just installed a new ADSL modem/router here (an Orange Livebox) and now have my Ubuntu desktop connecting to the router by ethernet and my wife's XP laptop connecting wirelessly.  However, I seem to be having a strange problem with Firestarter.

(My newbie understanding of Firestarter is that it's merely a GUI for iptables, and that somehow the "real" firewall protection is built into Linux, making Firestarter non-essential, but correct me if I'm wrong)

The problem is - 

With Firestarter turned ON, I am unable to see my wife's laptop on the network, nor even the directories I am sharing on this machine.  I can access the net fine.  However, testing the computer on the Shields-Up site returns a 'Failed' message, saying that my computer replies to pings, even though all the scanned ports and other bits are stealthed (Is that a verb?).

With Firestarter turned OFF, I can see my wife's laptop just fine, and directory sharing works properly.  On Shields-Up, I get the exact same results - my machine returns pings, but is otherwise invisible.  



The two things that puzzle me are, should I be replying to pings or not (could it be the router and not my computer?), and is it possible to use the local network with Firestarter running?  Is Firestarter even necessary?  

Finally, wireless home networking like this is totally new to me.  It's incredibly handy, but I am a bit leery about the security aspects.  If anyone could has any solid, simple advice to help a newbie with basic security, please post!  Thanks in advance!

---

### Post by r4ik on 2008-02-12
Maybe this helps,

[http://ubuntuforums.org/showthread.php?t=159661&highlight=iptables](http://ubuntuforums.org/showthread.php?t=159661&highlight=iptables)

Good luck !

---

### Post by oilchangeguy on 2008-02-12
> **TreverT said:**
> We've just installed a new ADSL modem/router here (an Orange Livebox) and now have my Ubuntu desktop connecting to the router by ethernet and my wife's XP laptop connecting wirelessly.  However, I seem to be having a strange problem with Firestarter.

(My newbie understanding of Firestarter is that it's merely a GUI for iptables, and that somehow the "real" firewall protection is built into Linux, making Firestarter non-essential, but correct me if I'm wrong)

The problem is - 

With Firestarter turned ON, I am unable to see my wife's laptop on the network, nor even the directories I am sharing on this machine.  I can access the net fine.  However, testing the computer on the Shields-Up site returns a 'Failed' message, saying that my computer replies to pings, even though all the scanned ports and other bits are stealthed (Is that a verb?).

With Firestarter turned OFF, I can see my wife's laptop just fine, and directory sharing works properly.  On Shields-Up, I get the exact same results - my machine returns pings, but is otherwise invisible.  



The two things that puzzle me are, should I be replying to pings or not (could it be the router and not my computer?), and is it possible to use the local network with Firestarter running?  Is Firestarter even necessary?  

Finally, wireless home networking like this is totally new to me.  It's incredibly handy, but I am a bit leery about the security aspects.  If anyone could has any solid, simple advice to help a newbie with basic security, please post!  Thanks in advance!

no, you don't need firestarter. and when you installed the wireless router there should be several security options. read the manual that came with the router and setup the security features. as long as you don't store really sensitive data on your computer wep is the easiest to set up.

---

### Post by kestrel1 on 2008-02-12
I think you will find that when you are using Shields-up, it is being blocked by your routers firewall. I don't think you need to worry too much about the ping problem, have a look here for more info:
[http://www.faqs.org/faqs/computer-security/most-common-qs/section-18.html](http://www.faqs.org/faqs/computer-security/most-common-qs/section-18.html)
You are right in saying that Firestarter is only a GUI frontend for IPTables, so that you can set up custom rules, but I wouldn't be inclined to mess about with it unles you have specific needs. I cannot understand why turning on Firestarter stops you gaining access to networked resources, but maybe someone else can explain that.

---

### Post by ajgreeny on 2008-02-12
You really don't need firestarter unless you are running a server, as I understand things, but just out of interest, uninstall firestarter for the moment and clear your iptables to the default as follows
```
sudo /etc/init.d/firestarter stop 
sudo iptables -F 
sudo dpkg -P firestarter
sudo /etc/init.d/networking restart

```Now run Shields Up again and see what the results are,  Whenever I do it I always get a full pass, as if my machine does not exist, and I am behind a wired router.  If yours then passes, as mine does, perhaps it's not worth putting firestarter back.

---

### Post by TreverT on 2008-02-13
> **ajgreeny said:**
> You really don't need firestarter unless you are running a server, as I understand things, but just out of interest, uninstall firestarter for the moment and clear your iptables to the default as follows
```
sudo /etc/init.d/firestarter stop 
sudo iptables -F 
sudo dpkg -P firestarter
sudo /etc/init.d/networking restart

```Now run Shields Up again and see what the results are,  Whenever I do it I always get a full pass, as if my machine does not exist, and I am behind a wired router.  If yours then passes, as mine does, perhaps it's not worth putting firestarter back.


I did that in terminal and got this reply:

```

Removing firestarter ...
Purging configuration files for firestarter ...
trevert@trevert-desktop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 4098
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:10:dc:f9:db:38
Sending on   LPF/eth0/00:10:dc:f9:db:38
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
/usr/bin/poff: No pppd is running.  None stopped.
dsl-provider: ERROR while getting interface flags: No such device
Plugin rp-pppoe.so loaded.
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:10:dc:f9:db:38
Sending on   LPF/eth0/00:10:dc:f9:db:38
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.11 -- renewal in 295775 seconds.

```

I am curious about this line - "dsl-provider: ERROR while getting interface flags: No such device", but otherwise all went fine and it was immediately back online and shortly re-connected to the home network (It sees the XP computer wirelessly and vice-versa).  However, I still get the same results on Shields up - all my ports show Stealth but it still replies to pings.

I wonder if it is the Livebox modem/router that is replying, and not my computer?  

Thanks for your help, everyone!

---

### Post by kestrel1 on 2008-02-13
It will be your router that is blocking the external internet access via it's built in firewall.
You don't really need to worry too much about the ping failure.
Your router gets it's IP address from your ISP & your PC get's it's IP address from the router via DHCP.
Your PC's IP may be something like 192.168.0.2, but this depends on what your router is set to pass out as IP addresses. If you look at your routers IP address that your PC see's it may be something like 192.168.0.1, but it's external IP address will be different & you will see that when you use Shields-up.
IPTables will protect you from attacks from within your network or if anything gets past your routers firewall (not very likely, but possible)

---

