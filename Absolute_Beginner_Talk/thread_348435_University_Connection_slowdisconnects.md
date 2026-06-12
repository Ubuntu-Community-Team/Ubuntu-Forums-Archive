---
title: "University Connection slow/disconnects"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by skyhopper88 on 2007-01-28
I'm new at troubleshooting Ubuntu, so bare with me. In Windows I'm getting speeds of 6699 kbps down/8830 up. In Ubuntu however, I get  974/857! Something isn't set up right. I am running Edgy on my desktop with my ethernet coming straight from the wall to my onboard ethernet. Network Manager is telling me I'm connected to the wired connection. I have set it to automatic and static addresses, no change. The connection doesn't seem to be dropping anymore (hope I don't jinx myself), but it's still slow. Right now I'm using a X-over cable, not sure if that makes any difference. I switched it out with my roomate's but I'm not sure what it was (just said Belkin on it...). That didn't help any. I'm not exactly sure what the specs on my onboard card are other than it's a Nvidia Ethernet Controller, using forcedeth. In Windows I got similar (slow) speeds until I set it to full duplex, that's done with ethtool, correct? Well...
'ethtool eth0' gives me

> Cannot get device settings: Operation not permitted
Cannot get wake-on-lan settings: Operation not permitted
Cannot get message level: Operation not permitted
Cannot get link status: Operation not permitted
No data available


Here are some other outputs:

'dmesg |grep eth' gives me
> 
[17179586.204000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.54.
[17179586.204000] forcedeth: using HIGHDMA
[17179586.724000] eth0: forcedeth.c: subsystem: 0105b:0caf bound to 0000:00:14.0
[17179619.416000] eth0: no IPv6 routers present
[17179984.528000] eth0: no IPv6 routers present


'ifconfig -a -v' gives me

> eth0      Link encap:Ethernet  HWaddr 00:15:58:25:FD:09  
          inet addr:69.65.220.163  Bcast:69.65.221.255  Mask:255.255.254.0
          inet6 addr: fe80::215:58ff:fe25:fd09/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:84500 errors:0 dropped:0 overruns:0 frame:0
          TX packets:67923 errors:201 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:86128984 (82.1 MiB)  TX bytes:7287269 (6.9 MiB)
          Interrupt:225 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)



'dmesg |grep net' gives me

> [17179571.716000] audit: initializing netlink socket (disabled)
[17179586.204000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.54.


'ifconfig eth0' gives me

> eth0      Link encap:Ethernet  HWaddr 00:15:58:25:FD:09  
          inet addr:69.65.220.163  Bcast:69.65.221.255  Mask:255.255.254.0
          inet6 addr: fe80::215:58ff:fe25:fd09/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:82497 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66299 errors:201 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:83817927 (79.9 MiB)  TX bytes:7151651 (6.8 MiB)
          Interrupt:225 Base address:0x2000 


'cat /etc/network/interfaces' gives me

> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


'ifup eth0' gives me 
> ifup: interface eth0 already configured


I've disabled IPV6 as well, nada. I need to get this sorted out soon, as I use this for schoolwork. Any help would be appreciated.

---

### Post by Blutack on 2007-01-28
An X-over will definatly not help matters, its for connecting two computers, not to a wall socket.  Is your inet actually feeling slower?  Or is it just reporting slower?

---

### Post by Blutack on 2007-01-28
oh, you need to run ethtool with sudo in front, like this
sudo ethtool
(it alters hardware settings and so needs root access)

---

### Post by irish_flu on 2007-01-28
If you were using a crossover cable and needed a straight-cable, your connection shouldn't work at all.  I'm guessing your cable type is not the problem.

Incidentally (FYI for interested folks) some Universities who were very early to the scene ended up with cable pinouts that were not what ended up being the "standard".

Indiana University, for instance, has to make all their own cables (and that's with 40,000 undergrads and tens-of-thousands of grads, faculty, and staff) on their main campus because the cable needs to connect to a "non-standard" wall jack.

---

### Post by skyhopper88 on 2007-01-28
It's a bunch slower. Any DL or update, no matter the server, maxes at 30 kbps. Browsing is considerably slowed down as well. I'm in Windows right know and all is as it should be, even with the X-over. I think it has something to do with the duplex setting, I got similar speeds in Windows until I forced 10 Full duplex, but I can't seem to change it for Ubuntu.

I believe I did sudo it, but I'm not positive. I'll boot back into Ubuntu and give it another shot. I may try using Ndiswrapper if this keeps up, but I don't really know how.

---

### Post by r4ik on 2007-01-28
-

---

### Post by Blutack on 2007-01-28
Erm, not being harsh but I don't think nameserver resolution is his problem, it sounds like a hardware thing.  Did you misread the post maybe?
Ndiswrapper probably won't help, its mainly for wireless network cards but if it does then great!

---

### Post by r4ik on 2007-01-28
> **Blutack said:**
> Erm, not being harsh but I don't think nameserver resolution is his problem, it sounds like a hardware thing.  Did you misread the post maybe?
Ndiswrapper probably won't help, its mainly for wireless network cards but if it does then great!

I stand corrected thanks for mentioning it.
Suppose 2AM is a good time to get some sleep :)

---

### Post by skyhopper88 on 2007-01-28
Well, I wasn't doing ethtool with sudo, here's the output. 
> Settings for eth0:
        Supported ports: [ MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 10Mb/s
        Duplex: Half
        Port: MII
        PHYAD: 1
        Transceiver: external
        Auto-negotiation: on
        Supports Wake-on: g
        Wake-on: d
        Link detected: yes


It's at half duplex but I want it at full, what's the command for that?

It's getting the DNS fine, maybe I should try openDNS again though, got better preformance with it before.
*shrug*

---

### Post by Blutack on 2007-01-28
sudo ethtool -s eth0 duplex full

I don't know whether that is permenant, although I suspect it will be.

Good luck, enjoy.  Any more trouble typing man ethtool will give you the manual page for it.

(and r4ick, I understand completely and am heading to bed myself)

edit: you might want to change the speed to 100 as well
same command but with speed 100 instead

---

### Post by skyhopper88 on 2007-01-28
Thanks, hopefully it sticks.

---

### Post by Blutack on 2007-01-28
It probs won't but

[http://www.cyberciti.biz/tips/howto-linux-add-ethtool-duplex-settings-permanent.html](http://www.cyberciti.biz/tips/howto-linux-add-ethtool-duplex-settings-permanent.html)

will make em.

---

### Post by skyhopper88 on 2007-01-28
Setting it to 100 just disconnects me, 10 renews the connection. My hardware should support it, maybe it's my University?

---

### Post by Blutack on 2007-01-28
Probs, stick with 10 if it works.  It looks like that is what your card is automagically using so don't muck with it.  Its unusual to see 10mps networks nowadays is all, but that must be what you have.

---

### Post by sloggerkhan on 2007-01-28
My dorm uses 10mbs wiring, but I still get a 2mbs internet connection, at least if the servers get that fast.

---

### Post by Blutack on 2007-01-28
My uni we are all at 100 :-)
Still no frostwire :-/

---

### Post by skyhopper88 on 2007-01-28
I have no idea why, but after rebooting the script doesn't autorun, and when I manually set it to full, it still reports half.

Edit: I think I got it working with by adding 'autoneg off' to the script.

---

### Post by skyhopper88 on 2007-01-29
Well...Network Manager is telling me no network devices have been found and I can't connect. Good news is the duplex is reporting 10 full, and I got Beryl working. Still, theres no connection...>_<

---

### Post by skyhopper88 on 2007-01-29
I'm on a fresh install of 6.10 again, I messed around with beryl a bit too much. 
The connection works again but 'sudo ethtool -s eth0 duplex full' isn't changing the duplex anymore.

---

### Post by skyhopper88 on 2007-01-31
When autonegotiation is on, setting it to full duplex disconnects and reconnects, but it still remains half. When it's off, changing duplex to full just disconnects and doesn't reconnect, duplex still reports half.

---

### Post by skyhopper88 on 2007-02-01
Is there anything besides ethtool and miitools I can use? I'm at the end of my rope here.

---

### Post by skyhopper88 on 2007-02-01
I'm tryng to get it to work with ndiswrapper, here's what's going on. I've got NVENETFD.sys and the inf, oem1.inf. When I open the inf with the gui I get

> (ndisgtk:8047): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.
modprobe config already contains alias directive

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument


Same thing happens if I rename it to the same name as the sys. If I go through the terminal I get
> Installing oem1
couldn't copy oem1.inf at /usr/sbin/ndiswrapper-1.8 line 144.
skyhopper88@watkins:~$ 

Again, same happens if I rename the inf to the same as the sys.

---

### Post by skyhopper88 on 2007-02-05
Maybe the only way I can figure this out is with another NIC, idk....

---

### Post by skyhopper88 on 2007-02-07
Couldn't change anything running off the Live CD either. Anybody have recommendations on a solid cheap NIC for Ubuntu?

---

### Post by skyhopper88 on 2007-02-09
Also tried my old Dapper CD, no luck. Dunno if I should try Feisty Fawn or not since it's alpha. Can anyone reccomend me a NIC or another n00b friendly distro comparable to Ubuntu?

---

### Post by skyhopper88 on 2007-02-10
The Fiesty Fawn Live CD lets me change it, guess I'll bite the bullet and go with it.

---

### Post by skyhopper88 on 2007-02-10
Hm, the Live CD froze at 94% installing grub so I'm back to Edgy. How can I obtain the software that I need for my connection to be "fixed" under Edgy? Is there a backport?

---

