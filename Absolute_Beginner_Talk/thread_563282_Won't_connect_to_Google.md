---
title: "Won't connect to Google"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by H3retic on 2007-09-29
Firefox can't connect to google.  The problem seemed to start when I initialised Firefox for wine, installed through winedoors.

Rebooted the machine, didn't work.  Reconnected to network, didn't work.  Removed all addons, didn't work.  Tried using epiphany and elinks, neither of them can connect to google either.  PINg'd google.ca in console (ping google.ca), didn't work, even though I'm not so sure about that one.

At the end of my rope.  Ideas anyone?

---

### Post by MobiusNZ on 2007-09-29
Err, why are you running firefox under wine? Its available natively in linux...

Anyway, what is your /etc/network/interfaces like? And what do you get if you type "ifconfig" in the terminal?

Can you get on any other site?

---

### Post by H3retic on 2007-09-29
Well yeah I can get to just about anything else, though some sides randomly don't want to load.  Ubuntu forums woudn't load unless I enabled script blocker, maybe that has something to do with it.  Yahoo doesn't load either.

As for ff under wine... curiosity.  Just curiosity.

==>Anyway, what is your /etc/network/interfaces like? And what do you get if you type "ifconfig" in the terminal?<==

chris@UbuntuStudio:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:DB:86:14:43  
          inet addr:192.168.1.107  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:dbff:fe86:1443/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1507 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1475 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1091265 (1.0 MiB)  TX bytes:197723 (193.0 KiB)
          Interrupt:21 Base address:0xf200 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:50 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6724 (6.5 KiB)  TX bytes:6724 (6.5 KiB)

ra0       Link encap:Ethernet  HWaddr 00:0F:66:6C:70:71  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:270 errors:1 dropped:0 overruns:0 frame:0
          TX packets:12652 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:40631 (39.6 KiB)  TX bytes:506080 (494.2 KiB)
          Interrupt:22 Base address:0xc000

---

### Post by MobiusNZ on 2007-09-29
Can you connect to all sites normally using the native firefox?

---

### Post by H3retic on 2007-09-29
Yes, more or less.
Just to clear things up, I'm having problems with the native Firefox, the wine version is removed now.  When I log onto ubuntu forums without script blocker I get hung up when ff is looking up "google-analytics" which I'm assuming is advertising.

etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

---

### Post by H3retic on 2007-09-29
Gah forget it I'll just reinstall the whole thing.  I needed to install windows xp for games anyway.  And it's a hassle to do Ubuntu before xp...  Thanks for the help : )

---

### Post by MobiusNZ on 2007-09-29
Hmmm... what shows up in the terminal if you type```
ping google.com
```?

---

