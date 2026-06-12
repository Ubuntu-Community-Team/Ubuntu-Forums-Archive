---
title: "Internet problem."
date: 2006-07-09
forum: Absolute Beginner Talk
---

### Post by HarrisonHopkins on 2006-07-09
Ok, I've been trying to get internet through ethernet on my Xubuntu for a few days. My router recognizes that it is connected, and Xubuntu says that it is active, yet Firefox refuses to connect to anything, as if it doesn't even have an ethernet plugged in. CAn someone help me with this?

---

### Post by taurus on 2006-07-09
Open a terminal and see if you can ping anybody!!!
```

ping -c 3 www.yahoo.com

```
Otherwise, what is the output of this command from a terminal then?
```

ifconfig

```

---

### Post by HarrisonHopkins on 2006-07-09
Ping came back with 'ping unknown host www.yahoo.com'

ifconfig came back with 

eth0    Link encap:Ethernet Hwaddr 00:04:75:BE:91:4F
        inet addr:65.184.140.82 Bcast:65.184.143.255 Mask: 255.255.248.0
        UP BROADCAST RUNNING MULTICAST  MTU:1500 Metric:1
        RX packets:4501 errors:0 dropped:0 overruns:1 frame:0
        TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:1000
        RX bytes: 281201 (274.6 KiB) TX Bytes:1948 (1.9 KiB)
        Interrupt:11 Base Address:0xe000

lo      Link encap:Local Loopback
        inet addr:127.0.0.1 Mask:255.0.0.0
        UP LOOPBACK RUNNING MTU:16436 Metric:1
        RX packets:3 errors:0 dropped:0 overruns:0 frame:0
        TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelan:0
        RX bytes:172 (172.0 b) TX bytes: 172 (172.0 b)

---

### Post by lamego on 2006-07-09
Check your dns configuration:
```
cat /etc/resolv.conf
```

---

### Post by HarrisonHopkins on 2006-07-09
It comes up with 

search ec.rr.com
nameserver 24.25.5.150
nameserver 24.25.5.149

---

### Post by lamego on 2006-07-09
Try to ping your dns servers:
```
ping -c 5 24.25.5.150
ping -c 5 24.25.5.149
```

---

### Post by HarrisonHopkins on 2006-07-09
On both, the statistics said 5 packets transmitted, 0 recieved, 100% packet loss, time 3999ms

---

### Post by RaZer0r on 2006-07-09
do you dual boot with windows? if so, you can check the settings there and simply configure them in xubuntu.. that's how i did it :p

---

### Post by HarrisonHopkins on 2006-07-09
Nope, I do not dual boot. I have a completely Xubuntu Machine, and a completely Windows XP machine.

---

### Post by RaZer0r on 2006-07-09
well at the xp machine, start-> run-> cmd
and insert "ipconfig/all"
copy paste that output here so i can help you further

---

### Post by HarrisonHopkins on 2006-07-09
Windows IP Configuration

        Host Name . . . . . . . . . . . . : DBK82T31
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Hybrid
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No
        DNS Suffix Search List. . . . . . : ec.rr.com

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . : ec.rr.com
        Description . . . . . . . . . . . : Broadcom 440x 10/100 Integrated Cont
roller
        Physical Address. . . . . . . . . : 00-0D-56-53-4D-2B
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 65.184.140.82
        Subnet Mask . . . . . . . . . . . : 255.255.248.0
        Default Gateway . . . . . . . . . : 65.184.136.1
        DHCP Server . . . . . . . . . . . : 10.49.0.1
        DNS Servers . . . . . . . . . . . : 24.25.5.150
                                            24.25.5.149
        Lease Obtained. . . . . . . . . . : Sunday, July 09, 2006 5:27:19 PM
        Lease Expires . . . . . . . . . . : Monday, July 10, 2006 2:12:11 PM

---

### Post by RaZer0r on 2006-07-09
and what is the output of "ifconfig" at the xubuntu machine?
sorry didn't thought about the output you allready gave..

---

### Post by RaZer0r on 2006-07-09
i found your problem, you got an ip conflict.. those machines are both running on ip "65.184.140.82" which cant be correct :)

---

### Post by HarrisonHopkins on 2006-07-09
Should it really matter? I don't have both hooked up at the same time. I have to keep switching over untill I get two more ethernet cables so I can hook up my router.

---

### Post by RaZer0r on 2006-07-09
i see... forget my comment about those same ips then, that's totaly logical... wierd case, never have seen this problem before... it is configured totaly correct. Tried resetting the modem/router/hub/whatever?

---

### Post by HarrisonHopkins on 2006-07-09
I just did that, and I had no luck.

---

### Post by Apple 101 on 2006-07-09
You mean *ipconfig /all*.  Anyway, deactivate your eth0 or whatever it is and activate it again.

[I]sudo ifdown eth0
sudo ifup eth0[/I]

You could also try *network-admin*.

---

### Post by akhtet on 2006-07-10
Gosh. Help me too. I just installed Ubuntu 6.06. My firefox can connect HTTP pages, but not HTTPS. And can't use Gaim too. I didn't setup any firewall yet. Can anyone tell me how to manage Ports in Ubuntu?

---

### Post by RaZer0r on 2006-07-10
@ apple 101
you can leave the space in between when using commands in windows...

---

### Post by Apple 101 on 2006-07-11
> **RaZer0r said:**
> @ apple 101
you can leave the space in between when using commands in windows...
Cool.  Didn't know that.:p

---

### Post by Apple 101 on 2006-07-11
[QUOTE="akhtet"]Gosh. Help me too. I just installed Ubuntu 6.06. My firefox can connect HTTP pages, but not HTTPS. And can't use Gaim too. I didn't setup any firewall yet. Can anyone tell me how to manage Ports in Ubuntu?[/QUOTE]Make sure that you are using the latest Firefox version.  It has no problem (I'm using it).  What is wrong with Gaim?

---

### Post by akhtet on 2006-07-12
Yeah. I always use the latest version of Firefox.
I also installed gFTP and it worked.
But Gaim and SSL doesn't work.

For example, if you go to Gmail.com for the first time, it send you   their certificate and ask for permission. That thing doesn't happen in my Ubuntu. The page simply didn't come up. All pages with HTTPS didn't come up.

I'm wondering if there is something wrong with installation.

---

### Post by houstonbofh on 2006-07-12
> **HarrisonHopkins said:**
> Should it really matter? I don't have both hooked up at the same time. I have to keep switching over untill I get two more ethernet cables so I can hook up my router.
In most markets Road Runner caches the MAC address, so a quick change will not work.  You may have to reboot your cable modem to clear the MAC cache.  That or get a cheap router...(running) :mrgreen:

---

