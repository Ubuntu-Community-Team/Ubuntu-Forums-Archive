---
title: "Wireless card (RT2500 chipset) not working in 7.04"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by valkyrie on 2007-06-02
I have a StarTech.com CB555WG wireless card (RaLink 2500 chipset) which worked out of the box under 6.06.  I was planning to upgrade, but there was a crash mid-upgrade and I couldn't figure out what went wrong, so I ended up doing a clean install instead.  Now I've got Feisty 7.04 running, but the wireless card isn't working.

Symptoms:
[LIST][*]Lights come on.
[*]Roaming mode can "see" networks (e.g. my home network, my neighbor's router, other networks when I'm downtown)
[*]It appears to try connecting, but almost never manages to complete a connection
[*]When it does get a connection, there's no DNS (can't ping external URL's, can't ping local 192.168 network)
[*]Behavior is the same regardless of whether network uses WEP or not
[*]Entering the wrong passwords for a WEP-encrypted network results in the same behavior as a correct password[/LIST]

Problems are pretty much the same whether I go through the automatic roaming, or try to manually configure the card.

Here's the relevant part of lspci -v :
```
02:00.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
        Subsystem: RaLink Unknown device 2560
        Flags: bus master, slow devsel, latency 64, IRQ 11
        Memory at 24000000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: [40] Power Management version 2
```

Output from iwconfig:
```
lo     no wireless extensions

eth0   no wireless extensions
   
ir da0  no wireless extensions

ra0    RT2500 Wireless  ESSID:""
       Mode:Managed  Frequency=2.412 GHz  Bit Rate: 11 Mb/s   Tx-Power: -2 dBm

       RTS thr:off   Fragment thr:off
       Link Quality=0/100  Signal level=-120 dBm  Noise level: -203 dBm
       Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
       Tx excessive retries:0  Invalid misc:0  Missed beacon:0
```

Output from dmesg | grep rt2500
```
[16046.232452] rt2500 1.1.0 BETA4 2006/06/18 http://rt2x00.serialmonkey.com
[16062.951170] rt2500 EEPROM:  1  2  3  4  5  6  7  8  9 10 11 12 13 14  Channel
[16062.951195] rt2500 EEPROM:  1  1  1  1  1  3  3  3  3  3  3  3  3  3  dBm Maximum
```

I don't have the laptop  hooked up to any network right now, so please avoid requesting any extremely long output -- I have to type it in by hand :D

---

### Post by crispy_420 on 2007-06-02
Doesn't Feisty install network-manager by default? I think that may be the issue cause from last I read, RaLink cards and their chipset were not support. Did you use network-manager with this card in Dapper? If not, Is it possible to remove network-manager and connect the "old" way? That I don't know.

But on a side note, is this a notebook or desktop? If notebook, I would look into a Intel Pro based card. Just got a notebook with that chipset and it connects fast and seems to get good download speeds. Also a different notebook has a Atheros based card, it works fine as well although not as fast.

---

### Post by valkyrie on 2007-06-04
It's a notebook, and buying another wireless card isn't really an option -- mostly financially, but also because I'm stubborn -- this would be the second time I would have bought a new network card for an incompatibility issue.  (I still have the old one, some Broadcom chipset thingy, and am trying to get ndiswrapper to work with it.)

The problem is the same whether I'm manually configuring the connection or going through the auto-roaming mode (network-manager), although I have not tried uninstalling network-manager completely and going from there.  I do know that this card previously worked out of the box with zero configuration or connectivity issues back in 6.06... I'll try removing network-manager and see what happens.

---

### Post by hyper_ch on 2007-06-04
Mine works out of the box - it's a pci card for my desktop:
```

00:0a.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
        Subsystem: Linksys WMP54G 2.0 PCI Adapter
        Flags: bus master, slow devsel, latency 32, IRQ 19
        Memory at eb000000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>

```

---

### Post by brianw0667 on 2007-06-05
Another thread has information that may be relevent to your situation.  It sounds very similar.

[http://ubuntuforums.org/showpost.php?p=1310334&postcount=117](http://ubuntuforums.org/showpost.php?p=1310334&postcount=117)

---

### Post by valkyrie on 2007-06-05
Thanks brianw... it's a similar problem, but not exact -- the chipset isn't right.  (Which didn't stop me from trying, of course, but it didn't make a difference.)

I uninstalled network-manager completely from the laptop, and the problem is identical -- card sees the network, but will not receive data from it.  I've tried both DHCP and static IP assignment, it behaves the same either way.

It does seem a little bit better off *without* network-manager, since I now have the correct ESSID in the system, but it's still not quite there...

ifconfig:
```
ra0     Link encap:Ethernet  HWaddr 00:0E:2E:73:B8:6A
        inet addr:192.168.1.125  Bcast:192.168.1.255  Mask:255.255.255.0
        inet6 addr: fe80::20e:2eff:fe73:b86a/64 Scope:Link
        UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
        RX packets: 65 errors:0 dropped:0 overruns:0 frame:0
        TX packets:215 errors:0 dropped:0 overruns:0 frame:0
        collisions:3 txqueuelen:1000
        RX bytes:10270 (10.0 KiB)  TX bytes:13744 (13.4 KiB)
        Interrupt:11 Base address:0xc000
```

iwconfig:
```
ra0     RT2500 Wireless  ESSID:"linksys"
        Mode:Managed  Frequency=2.462 GHz  Access Point: 00:13:10:2E:67:61
        Bit Rate:54 Mb/s   Tx-Power:-6 dBm
        RTS thr:off   Fragment thr:off
        Encryption key:4007-****-0C   Security mode:open
        Link Quality=75/100  Signal level=-38 dBm  Noise level:-192 dBm
        Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
        Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```


EDIT: Oh yeah, and ping results:
```
$ ping -c 4 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.125 icmp_seq=3 Destination Host Unreachable
From 192.168.1.125 icmp_seq=4 Destination Host Unreachable

--- 192.168.1.1 ping statistics ---
4 packets transmitted, 0 received, +2 errors, 100% packet loss, time 2999ms, pipe 2
```
192.168.1.1 is the router, 192.168.1.125 is the static IP assigned to the laptop (on the laptop).

---

### Post by valkyrie on 2007-06-05
**arrrrrrrggh.**

It turns out my husband had changed the router key a few weeks ago without telling me.  So I've been using the wrong WEP key...  I'm just glad I thought to check that before another week went by!

SO, the problem was solved by (1) uninstall network-manager, (2) make sure your spouse hasn't messed with the router security without notifying you :P :lol:

---

### Post by WaveMyBlackFlag on 2007-06-17
So awesome.  who would have thought so simple as disabling my on-board gigabit wired lan, uninstalling the network manager and restarting the system would fix something that has been eating at my sanity for months now...   EUREKA!!

---

